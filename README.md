# Scientific Claim Verifier

Full code for the Master Thesis **"Development of a Language Model-Based Framework for Credibility Assessment and Verification of Scientific Claims"** by **Mateus Pereira** (final grade: **19/20**).

A framework for automated verification of scientific claims using Large Language Models and proposition-based retrieval. Made in Python, built on LangChain and FastAPI.

## What it does

Given a scientific claim, the framework decides whether the existing literature supports it, refutes it, or is inconclusive — and how credible that evidence is. The verification flow is organized in three stages:

### 1. Knowledge Base Construction (optional)

The evidence base is built by turning literature into searchable, credibility-aware units:

- **Articles → Chunks → Propositions** — papers are retrieved through scientific literature APIs (PubMed, PubMed Central, OpenAlex, Semantic Scholar, CORE), split into overlapping chunks, and then decomposed by an LLM into atomic, self-contained *propositions* (single factual statements).
- **Credibility & quality assessment** — each article gets a 1–5★ credibility rating derived from its study type (meta-analysis and systematic review rank highest, down through RCTs, cohort/case-control, to case reports), methodology metadata (sample size, blinding, randomization, population type), citation count, recency, and full-text availability. Each extracted proposition is graded by an LLM on four dimensions — accuracy, clarity, completeness, and conciseness (1–10 each) — and only those clearing the quality threshold are kept as high-quality evidence.
- **Storage with metadata and scores** — propositions and chunks are embedded and stored in a FAISS vector knowledge base, persisted alongside paper metadata and credibility scores in SQLite.

This stage is optional: the repository ships with a prebuilt knowledge base, so claims can be verified against existing evidence right away.

### 2. Evidence Retrieval

For a given claim, the framework gathers the most relevant evidence. This stage runs in **one of two modes**:

- **Traditional Pipeline** — a structured, fixed sequence: from the claim it generates three complementary search queries (the original claim, an opposing formulation, and a neutral/related variant), performs semantic similarity search over the knowledge base, and weights the retrieved evidence by the credibility of its sources. Best for reproducibility, debugging, and predictable workflows.

- **AI Agent** — autonomous evidence gathering with dynamic planning. The agent iteratively *selects a tool → executes it → evaluates the result → decides whether it has enough evidence*, looping until the investigation is complete. It has access to several tools: proposition search (`search_similar_propositions`), paper discovery (`search_similar_chunks`, `find_similar_papers`), in-paper and source lookup (`search_propositions_in_paper`, `get_proposition_source_chunk`, `get_paper_details`), knowledge base overview (`get_kb_statistics`), and online literature search (`search_online_papers` for PubMed, Semantic Scholar, CORE). Best for complex claims that require adaptive investigation and cases where the evidence path isn't predictable.

### 3. Verdict Generation

An LLM weighs the retrieved evidence against the claim and produces a verdict — `SUPPORTS`, `REFUTES`, or `INSUFFICIENT_EVIDENCE` — together with a **confidence score** (on a 1–10 scale) that reflects the strength and credibility of the supporting evidence.

Crucially, every verdict comes with a written **rationale** explaining *why* the evidence supports, refutes, or fails to settle the claim. The rationale **cites the specific propositions it relied on** with inline references (e.g. `[Source 1]`, `[Sources 1, 2, 3]`), so each conclusion is traceable back to the exact sentence and paper it came from.

### Example output

Running the pipeline on a claim prints the verdict, a confidence bar with its interpretation, the cited rationale, and every evidence source used:

```text
======================================================================
 VERIFICATION RESULTS
======================================================================

 Claim:
   A high microerythrocyte count raises vulnerability to severe anemia
   in homozygous alpha(+)-thalassemia trait subjects.

 Verdict: REFUTES

 Confidence:
   9.0/10 [█████████░]
   Extremely confident the claim is false - overwhelming, consistent
   evidence contradicting it

 Reasoning:
   The claim states that a high microerythrocyte count raises
   vulnerability to severe anemia in homozygous alpha(+)-thalassemia
   trait subjects. However, the evidence indicates the opposite.
   Children homozygous for alpha(+)-thalassaemia have microcytosis and
   an increased erythrocyte count [Sources 1, 2, 3]. This haematological
   profile actually reduces the risk of severe malarial anaemia (SMA)
   during acute malaria compared to children of normal genotype
   [Source 5]. Furthermore, these children require a 10% greater
   reduction in erythrocyte count for their Hb concentration to fall to
   50 g/l, suggesting increased resistance to severe anemia [Source 4].

 Evidence Summary:
   Evidence used: 5 propositions
   Sources: 1 paper

 All Evidence Sources:
======================================================================

   1. Increased Microerythrocyte Count in Homozygous α+-Thalassaemia
      Contributes to Protection against Severe Malarial Anaemia
      18174210
      Individuals homozygous for alpha(+)-thalassaemia have microcytosis.

   2. Increased Microerythrocyte Count in Homozygous α+-Thalassaemia
      Contributes to Protection against Severe Malarial Anaemia
      18174210
      Individuals homozygous for alpha(+)-thalassaemia have an increased
      erythrocyte count.

   3. Increased Microerythrocyte Count in Homozygous α+-Thalassaemia
      Contributes to Protection against Severe Malarial Anaemia
      18174210
      Increased erythrocyte count and microcytosis occur in children
      homozygous for alpha(+)-thalassaemia.

   4. Increased Microerythrocyte Count in Homozygous α+-Thalassaemia
      Contributes to Protection against Severe Malarial Anaemia
      18174210
      Children homozygous for alpha(+)-thalassaemia require a 10% greater
      reduction in erythrocyte count than children of normal genotype for
      Hb concentration to fall to 50 g/l.

   5. Increased Microerythrocyte Count in Homozygous α+-Thalassaemia
      Contributes to Protection against Severe Malarial Anaemia
      18174210
      The haematological profile in children homozygous for
      alpha(+)-thalassaemia reduces the risk of SMA during acute malaria
      compared to children of normal genotype.
```

> This example is drawn from the SciFact benchmark (claim id 42); the framework correctly refuted the claim with high confidence, citing the gold source document.

Beyond the core pipeline, the project includes a FastAPI web interface, an autonomous agent verification mode, and a benchmarking suite (CoverBench, HealthVer, SciFact).

## Quick Start

1. **Navigate to the project directory:**

   ```bash
   cd scientific-claim-verifier
   ```

2. **Install dependencies:**

    ```bash
    pip install -e .
    # or
    pip install -r requirements.txt
    ```

3. **Set up environment variables:**

    Create a `.env` file in the `scientific-claim-verifier` directory with the following variables:

    ```bash
    # Gemini API Key
    GEMINI_API_KEY=your_gemini_api_key_here

    # API keys for paper search
    SEMANTIC_SCHOLAR_API_KEY=your_semantic_scholar_key_here
    CORE_API_KEY=your_core_api_key_here

    # OpenAlex API (required for polite pool access)
    OPENALEX_MAILTO=your_email@example.com
    OPENALEX_API_KEY=your_openalex_key_here  # Optional
    ```

    **Note on OpenAlex:** The `OPENALEX_MAILTO` parameter is required for polite pool access (better rate limits and service). The API key is optional for basic usage.

4. **Login to Hugging Face (Required for Benchmarks):**

    To access benchmark datasets like CoverBench, HealthVer, and SciFact, you need to authenticate with Hugging Face:

    ```bash
    # Install huggingface-cli if not already installed
    pip install huggingface_hub

    # Login using one of these methods:
    huggingface-cli login
    # Or set token as environment variable:
    # export HF_TOKEN=your_token_here
    ```

    Follow the [Hugging Face CLI guide](https://huggingface.co/docs/huggingface_hub/main/en/guides/cli) for detailed authentication instructions.

5. **Run the pipeline:**

    Check examples below!

### Command Line Usage

> The repository ships with a prebuilt knowledge base at `data/kb_all` (the default `DB_NAME`), so you can verify claims against existing evidence right away with `--kb-only`, without first extracting your own corpus.

```bash
# Extract propositions from documents (all sections by default)
python scripts/run_extraction_pipeline.py  # Process demo paper (data/demo_paper.pdf)
python scripts/run_extraction_pipeline.py data/demo_paper.pdf  # Process specific file
python scripts/run_extraction_pipeline.py folder/  # Process all files in folder

# Verify claims
python scripts/run_verification_pipeline.py --help
python scripts/run_verification_pipeline.py "Vitamin D prevents COVID-19" --max-papers 10
python scripts/run_verification_pipeline.py "claim" --kb-only  # Use only existing KB
python scripts/run_verification_pipeline.py "claim" --skip-extraction-eval  # Skip quality evaluation during extraction (faster)
python scripts/run_verification_pipeline.py "claim" --kb-only --use-all-propositions  # Use all propositions, not just quality ones

# Query knowledge base
python scripts/query_knowledge_base.py  # Interactive mode
python scripts/query_knowledge_base.py "search query"
python scripts/query_knowledge_base.py --stats  # Show statistics
python scripts/query_knowledge_base.py --list-papers  # List all papers

# Test autonomous agent
python scripts/test_agents.py
```

### Batch Processing

The project supports batch processing of proposition extraction using Google's Batch API (50% cost discount). This is useful for processing large benchmark datasets.

```bash
cd scripts/batch_processing

# Step 1: Create batch job for a benchmark
python create_batch_extraction_jobs.py --benchmark coverbench --papers-per-claim 10
python create_batch_extraction_jobs.py --benchmark healthver --papers-per-claim 10
python create_batch_extraction_jobs.py --benchmark scifact --papers-per-claim 10

# Chunked processing - Process claims in smaller batches (resumable)
python create_batch_extraction_jobs.py --benchmark coverbench --offset 0 --limit 100
python create_batch_extraction_jobs.py --benchmark coverbench --offset 100 --limit 100
python create_batch_extraction_jobs.py --benchmark coverbench --offset 200 --limit 100

# Test with single claim first
python create_batch_extraction_jobs.py --benchmark coverbench --test-single-claim

# Step 2: Monitor batch job (optional)
python monitor_batch_jobs.py  # Monitor latest job
python monitor_batch_jobs.py --job-id batches/abc123  # Monitor specific job
python monitor_batch_jobs.py --list-all  # List all jobs

# Step 3: Process results and add to knowledge base
python process_batch_results.py  # Process latest results
python process_batch_results.py --results-file path/to/results.jsonl
```

Features:
- **Chunked Processing**: Use `--offset` and `--limit` flags to process claims in manageable batches
- **Resumable**: Process large datasets incrementally (e.g., CoverBench's 733 claims in 100-claim batches)
- **Timing**: Automatically tracks and displays processing time for each batch
- **Metadata Tracking**: Saves offset, limit, claim range, and elapsed time to metadata files

See [scripts/batch_processing/README.md](scientific-claim-verifier/scripts/batch_processing/README.md) for detailed documentation.

### Benchmarking

The framework supports several scientific claim verification benchmarks:

```bash
cd scientific-claim-verifier

# Run benchmarks
python -m scverifier.core.benchmarking.run_benchmark coverbench --max-items 10
python -m scverifier.core.benchmarking.run_benchmark healthver --max-items 10
python -m scverifier.core.benchmarking.run_benchmark scifact --max-items 10
```

Available benchmarks:
- **CoverBench**: 733 complex claims with rich grounding contexts (Google)
- **HealthVer**: Health-related claim verification dataset
- **SciFact**: Scientific fact verification dataset

Note: Requires Hugging Face authentication (see Quick Start step 4).

### Web Application

The project includes a FastAPI web interface for browsing and verifying claims:

```bash
# Run the web application
cd scientific-claim-verifier
uvicorn scverifier.webapp.main:app --reload
```

Features:
- Browse papers in the knowledge base
- View paper details, chunks, and propositions
- Search propositions and chunks
- Verify scientific claims with visual timeline
- Upload and process documents with/without claim extraction
- Autonomous agent-based verification
