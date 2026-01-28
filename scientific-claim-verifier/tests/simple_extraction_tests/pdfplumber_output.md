FoodChemistry:MolecularSciences4(2022)100090
Contents lists available at ScienceDirect
Food Chemistry: Molecular Sciences
journal homepage: www.sciencedirect.com/journal/food-chemistry-molecular-sciences
ChemTastesDB: A curated database of molecular tastants
Cristian Rojasa,*, Davide Ballabiob, Karen Pacheco Sarmientoa, Elisa Pacheco Jaramilloa,
Mateo Mendozaa, Fernando Garcíac
aGrupo de Investigacio´n en Quimiometría y QSAR, Facultad de Ciencia y Tecnología, Universidad del Azuay, Av. 24 de Mayo 7-77 y Herna´n Malo, Cuenca, Ecuador
bMilano Chemometrics and QSAR Research Group. Department of Earth and Environmental Sciences, University of Milano-Bicocca, P.za della Scienza 1-20126, Milano,
Italy
cFacultad de Ciencias Econ´omicas, Universidad Nacional de C´ordoba. Centro de Investigaciones en Ciencias Econ´omicas, Grupo vinculado CIECS – UNC – CONICET,
Co´rdoba, Argentina
A R T I C L E I N F O A B S T R A C T
Keywords: The purpose of this work is the creation of a chemical database named ChemTastesDB that includes both organic
ChemTastesDB and inorganic tastants. The creation, curation pipeline and the main features of the database are described in
Database detail. The database includes 2944 verified and curated compounds divided into nine classes, which comprise the
Tastes
five basic tastes (sweet, bitter, umami sour and salty) along with four additional categories: tasteless, non-sweet,
Chemical space
multitaste and miscellaneous. ChemTastesDB provides the following information for each tastant: name, Pub-
Foodinformatics
Chem CID, CAS registry number, canonical SMILES, class taste and references to the scientific sources from which
data were retrieved. The molecular structure in the HyperChem (.hin) format of each chemical is also made
available. In addition, molecular fingerprints were used for characterizing and analyzing the chemical space of
tastants by means of unsupervised machine learning. ChemTastesDB constitutes a useful tool to the scientific
community to expand the information of taste molecules and to assist in silico studies for the taste prediction of
unevaluated and as yet unsynthetized compounds, as well as the analysis of the relationships between molecular
structure and taste. The database is freely accessible at https://doi.org/10.5281/zenodo.5747393.
1. Introduction with other mechanisms. These additional mechanisms are associated
with the opening of ion channels or through secondary messenger
The sensation of taste plays an important role in the food chemistry channels associated with nucleotides or phosphorylated inositol (Dam-
field, since it is closely related to the development and selection of food odaran & Parkin, 2017; Di Lorenzo et al., 2009; Wong, 2018). Evidence
products and food intake. Throughout history, there has been a strong suggests that there are five basic tastes (sweet, bitter, umami, sour and
interest in understanding the mechanism by which gustatory sensation salty), which are also known as “taste modalities” or “receptor-mediated
is perceived by humans (Damodaran & Parkin, 2017). The extraordinary tastes” (Chandrashekar et al., 2006; Morini et al., 2011).
developments in foodinfomatics (computational food chemistry) and Among the basic tastes, sweetness is probably the most important,
bioinformatics (computational biochemistry) have provided the neces- since sweeteners evoke a pleasant sensation in several foods and medi-
sary tools to study the receptor/ligand binding interaction. In order to cines (Chandrashekar et al., 2006; Damodaran & Parkin, 2017). Sucrose
achieve a particular taste, it is now understood that the structure of the is used as a standard to quantify the relative sweetness (RS) of new
receptors and the specific features of the tastant ligands to interact with sweet-tasting molecules (Rojas et al., 2016a; Rojas et al., 2016b). The
receptors must be analyzed (Chandrashekar et al., 2006; Rojas et al., sweet taste chemoreceptor is a G-protein coupled receptor (GPCR) of
2016a). A molecular tastant is a water-soluble chemical compound class C made up of T1R2/T1R3 subunits (Chandrashekar et al., 2006;
(ligand) able to interact with the chemosensory receptors to produce a Morini et al., 2011). In contrast to the pleasant sensation of sweetness,
taste sensation (Di Lorenzo et al., 2009). The taste-receptor cells (TRCs) bitterness may be related to the protection of humans from the con-
are located in the gustatory papillae of the tongue and palate epithelium, sumption of toxic compounds (Chandrashekar et al., 2006; Di Lorenzo
which react to tastants by means of receptor-ligand interactions along et al., 2009), although in some foods or products it is perceived as a
* Corresponding author.
E-mail address: crojasvilla@gmail.com (C. Rojas).
https://doi.org/10.1016/j.fochms.2022.100090
Received 23 December 2021; Received in revised form 17 February 2022; Accepted 18 February 2022
Availableonline21February2022
2666-5662/© 2022 The Author(s). Published by Elsevier Ltd. This is an open access article under the CC BY-NC-ND license
(http://creativecommons.org/licenses/by-nc-nd/4.0/).

C. Rojas et al. F o o d C h e m i s t r y : M o l e c u l a r S c i e n ces4(2022)100090
pleasant taste. Quinine sulfate is used as the bitterness standard (Dam- 2. Materials and methods
odaran & Parkin, 2017; Rojas et al., 2017). Bitterness receptors are
comprised of a family of T2Rs proteins, which are located on taste re- 2.1. Data collection
ceptor cells. (Chandrashekar et al., 2006; Di Lorenzo et al., 2009).
Umaminess is defined as a meaty or savory sensation (Baines & Brown, Data was collected on 4580 molecular tastants from several scientific
2016; Damodaran & Parkin, 2017; Suess et al., 2015; Wong, 2018) and sources: 37 papers (including public databases), 3 books and 53 book
monosodium glutamate (MSG) is used as a standard to quantify the rela- chapters. Each molecule was associated with an experimental basic taste
tive intensity of umami tastants (Baines & Brown, 2016). As it is for (sweet, bitter, umami, sour or salty) or other gustatory sensations; for
sweetness, this taste receptor is a GPCR made up of T1R1/T1R3 subunits instance, tasteless (neutral taste), non-sweet (lacking sweet), non-bitter,
(Chandrashekar et al., 2006; Morini et al., 2011). The taste sensation of astringent, cooling, scratchy, burning, heating, pungent, and tingling.
sourness is related to substances that produce hydrogen ions when they Initially, we adopted the following criteria for a preliminary screening of
are diluted in water, such as citric acid, which is used as the sourness the collected data on the specific chemicals:
standard (Damodaran & Parkin, 2017; Ley et al., 2012; Wong, 2018).
Finally, saltiness is a stimulus produced by soluble salts, particularly a. protein tastants were not considered, for instance, miraculin, braz-
salts of low-molecular-weight, such as chlorides (sodium, potassium and zein, curculin, pentadin, monellin (I and II), thaumatin (I, II, III, a, b and
calcium). Sodium chloride is the standard for quantifying saltiness (Di c) and mabinlin (I and II).
Lorenzo et al., 2009; Ley et al., 2012; Wong, 2018). b. water molecules were removed from the hydrated compounds,
In addition to molecules that elicit the five basic tastes, there are because the sensorial evaluation of the taste is performed by a sip-
tastants that evoke other kinds of tastes, such as astringent, chilling, spit methodology using aqueous (or hydro-alcoholic) solutions
cooling, heating or pungent (Damodaran & Parkin, 2017; Ley et al., (Bassoli et al., 2008; Kelly et al., 2005; Rojas et al., 2016a).
2012; Wong, 2018). Other compounds elicit a complex combination of c. when dealing with the umami taste, we considered umami com-
tastes (multitastes), for instance potassium acid oxalate and protocatechuic pounds, taste-modulating and umami enhancer molecules (Suess
acid produce a sour/bitter taste (Wong, 2018), while calcium phenolsul- et al., 2015; Wong, 2018).
fonate and benzyl acetate exhibit bitter/astringent and bitter/pungent d. the Haworth projection (Damodaran & Parkin, 2017) was used to
tastes, respectively (Dagan-Wiener et al., 2019). Additionally, taste- represent the chemical structure of monosaccharides, such as fruc-
lessness refers to insipid molecules, that is, chemicals exhibiting the lack tose, glucose, psicose or tagatose.
of any particular taste. This class of compounds involves non-sweet, non-
bitter, non-sour, non-salty or non-umami compounds (Damodaran & 2.2. Curation and optimization of molecular structures
Parkin, 2017; Rojas et al., 2017).
The chemical analysis of taste molecules in raw ingredients and in The 3D molecular structures of 4580 tastants were manually repre-
end-products for human consumption play an important role for the sented using the HyperChem software (Hypercube Inc.). For geometry
assurance of food quality and desirability, as well as to prevent defects optimization, the molecular mechanics force field (MM+) and the con-
(offensive tastes) in consumer food products (Ley et al., 2012). Due to jugate gradient algorithm were used. The convergence criteria for ge-
interest in producing new, safe and more potent tastants (particularly ometry optimization was established when the root mean square
sweet and bitter), several freely accessible databases containing infor- deviation of the gradient vector was less than 0.01 kcal×(Å×mol)-1. The
mation of taste molecules have been reported in the literature in the last information of stereocenters was used in order to differentiate stereo-
decade. These databases include: SuperSweet (http://bioinformatics.ch isomers (when available). The information of stereochemistry, when not
arite.de/sweet/) (Ahmed et al., 2011), BitterDB (http://bitterdb.agri. available, was obtained from the PubChem open library (Kim et al.,
huji.ac.il/) (Dagan-Wiener et al., 2019), TasteDB (by merging portions 2019) and other scientific sources. Otherwise, the default structure
of the SuperSweet and the BitterDB) (Ruddigkeit & Reymond, 2014), generated by the model builder of HyperChem was used (no confor-
SweetenersDB (http://chemosim.unice.fr/SweetenersDB/) (Bouysset mational analysis was performed).
et al., 2020). Additionally, other databases of tastants have been Since chemical structures available in scientific papers, books (or
recently developed for in silico modeling, such as BitterX (Huang et al., chapters) and/or public and commercial databases are not exempt from
2016), expert system (Rojas et al., 2017), BitterPredict (Dagan-Wiener errors, we performed a further molecular structure curation. The cura-
et al., 2017), BitterSweetForest (Banerjee & Preissner, 2018), e-Bitter tion process of a query compound constitutes a crucial step during the
(Zheng et al., 2018), e-Sweet (Zheng et al., 2019), BitterSweet (Tuwani development of a reliable database to be used in QSAR/QSPR modeling.
et al., 2019), structure-based screening (Shoshan-Galeczki & Niv, 2020), Identification of errors in molecular structures includes, for example,
BTP640 (Charoenkwan et al., 2020), children’s bitter drug prediction missing atoms or functional groups, misplaced atoms or rearranged
system (CBDPS) (Bai et al., 2021), and multi-layer prediction system chemical groups. All of these potential errors can negatively influence
(Yang et al., 2022). the calculation of molecular descriptors, which may have deleterious
Given these advances, we developed an extensive database of mo- effects on subsequent modelling (Fourches et al., 2010).
lecular structures with associated information on taste. The database is Thus, the accuracy of molecular structures was initially analyzed in
named ChemTastesDB and includes 2944 organic and inorganic tastants. PubChem (Kim et al., 2019) or other open libraries. Subsequently, the
For each tastant, the database includes the following information: alvaMolecule software (Alvascience, 2020) was used for molecular
PubChem CID, CAS registry number, canonical SMILES, class taste and curation to identify molecules with multiple structures, unusual valence,
references to the scientific sources from where data were retrieved, as covalent/ionic bonds, total charge, isotopes, charged atoms, non-carbon
well as the molecular structure in the HyperChem (.hin) format. The atoms, non-standard atom sets (H, C, N, O, P, S, F, Cl, Br and I), no ar-
overall aim of the ChemTastesDB is to provide a tool to the scientific omatic ring standardization and radical atoms. These issues were cor-
community to increase the available information of taste molecules and rected applying some standard criteria as implemented in the software,
to support the development of in silico approaches for taste prediction. such as standardization of benzene rings into aromatic form, conversion
The database is freely available at the following URL: https://doi. of unusual covalent bonds to ionic forms, addition of charge to quater-
org/10.5281/zenodo.5747393. nary nitrogen atom, removal or adding excessive or missing hydrogens,
standardization of nitro, azide and diazo groups, and NOxide compati-
bility. Finally, the CAS registry number and the PubChem CID of each
tastant was also obtained from the PubChem (when available) along
with the search function implemented in alvaMolecule.
2

C. Rojas et al. F o o d C h e m i s t r y : M o l e c u l a r S c i e n ces4(2022)100090
For 402 compounds, the name, PubChem CID and CAS registry for substructure searching or molecular similarity. The alvaDesc soft-
number were automatically retrieved from the PubChem library by ware (Alvascience, 2021) was used to calculate the binary 166 MACCS
means of alvaMolecule. Additionally, the Marvin Sketch (ChemAxon fingerprints starting with the molecular SMILES.
Ltd., 2021) was used to generate the IUPAC name for 538 molecules, The chemical space was defined through molecular similarity/di-
which were not found when applying the alvaMolecule similarity versity analysis based on the t-Distributed Stochastic Neighbor Embed-
search. ding (t-SNE) (van der Maaten & Hinton, 2008), which attempts to
project tastants fingerprints into a two-dimensional space (ℝN → ℝ2), in
2.3. Database merging and filtering such a way as to preserve the local structure. To calculate the pairwise
similarities in low-dimensional space, t-SNE uses a symmetrized version
Data were further filtered to verify replicated compounds. Initially, of the cost function with simpler gradients to facilitate the optimization
the canonical SMILES (simplified molecular input line entry system) of process, as well as the heavy-tailed Student-t distribution to overcome
the 4580 tastants were generated in alvaMolecule from the HyperChem the crowding problem. This unsupervised approach is able to match
3D molecular representation. Subsequently, the chemical name (with pairwise similarity distributions in both higher-dimensional space and
the corresponding taste), CAS registry number, PubChem CID, canonical lower-dimensional space to preserve the local structure of data. Conse-
SMILES and scientific reference were merged with an in-house KNIME quently, t-SNE efficiently captures the local structure of the high-
workflow (Berthold et al., 2008), which included the following filtering dimensional space, while eliciting the presence of clusters at several
steps: scales (structure of the data). The pairwise similarities were calculated
by means of the Jaccard-Tanimoto similarity coefficient (Todeschini
a. molecules labelled as 3,5-dichlorophenyl guanidineacetic acid deriva- et al., 2015). This well-known binary similarity coefficient emphasizes
tive, 4-cyanophenyl guanidineacetic acid derivative, compound, iso- the presence of common features omitting the absence of common fea-
vanillyl derivative, perillartine derivative and phenylsulfamate tures and the simple matching accounting for both presence and absence
monosubstituted were excluded; of common features.
b. molecules exhibiting the exact match of name, CAS number or
PubChem CID were merged into a single entry; 2.5. Software and code
c. molecules excluded in step a) were considered together with the
molecules processed in step b), and a new curation step was applied HyperChem version 8 was used for drawing and displaying chemical
to find chemicals with the same molecular structure by comparing structure of molecular tastants, while the chemical structures were
canonical SMILES. Stereoisomers (for instance D-glucose and L- checked and curated in the alvaMolecule software. An in-house KNIME
glucose) were not considered in this step; workflow was programmed for filtering the database. MACCS finger-
d. molecules exhibiting multiple-valued tastes were assigned to the prints were calculated in alvaDesc. MATLAB was used to calculate t-SNE
most frequent taste class with a majority voting approach. When models.
multiple-valued tastes were tied, the tastant was included in the
miscellaneous class; 3. Results and discussion
e. molecules with the following tastes were included in the miscella-
neous class: astringent, cooling, hot burning, heating, pungent, and 3.1. ChemTastesDB description
tingling. The same criterion was adopted to assign compounds
labelled with an ambiguous class (bitter/burning/scratchy, bitter/ The curated ChemTastesDB consisted of 2944 compounds grouped
tasteless, non-bitter, non-bitter/burning, non-sweet/sweet, sweet/ into nine classes, which include the five basic tastes (sweet, bitter,
bitter, sweet/tasteless). umami, sour and salty) and four additional classes (non-sweet, tasteless,
multitaste and miscellaneous). Table 1 lists the number of molecules
2.4. Analysis of the chemical space of tastants included in each class. The ChemTastesDB is freely available at https://d
oi.org/10.5281/zenodo.5747393, and includes four files:
Chemical space (Medina-Franco et al., 2021) is a useful concept in
diverse areas of computational chemistry including chemoinformatics 1. a pdf file (ChemTastesDB_readme.pdf) containing a complete
and foodinformatics. The chemical space is defined by all chemicals description of the ChemTastesDB;
represented by a N-dimensional vector of features (for instance MACCS) 2. an excel file (ChemTastesDB_database.xls), where the following data
that captures the most relevant chemical information of compounds. are collected for each tastant: molecular ID, name, PubChem CID,
Thus, this multidimensional space aims to conceptualize molecular CAS registry number, canonical SMILES string, class taste and
similarities by identifying regions where molecules are clustered by reference to the scientific sources from which data were retrieved;
their features. The most suitable way to visualize and analyze the 3. an excel file (ChemTastesDB_references.xls), containing a compre-
chemical space is by the projection of similarities/dissimilarities into a hensive list of all scientific references with their extended details;
low-dimensional space by means of diverse unsupervised machine
learning approaches. Previous studies have analyzed the chemical
spaces of taste molecules by applying Principal Component Analysis
(PCA) (Dagan-Wiener et al., 2017; Di Pizio et al., 2019; Ruddigkeit & Table 1
Number of molecular tastants included in the nine classes of the
Reymond, 2014), Multidimensional Scaling (MDS) (Rojas et al., 2017),
curated ChemTastesDB.
and the t-Distributed Stochastic Neighbor Embedding (t-SNE) (Bouysset
et al., 2020; Tuwani et al., 2019). Tastant class Number of molecules
In this study, structural characteristics of molecular tastants were Sweetness 977
represented by means of the Molecular ACCess System (MACCS) fin- Bitterness 1183
gerprints (Durant et al., 2002). These are 2D binary fixed size finger- Umaminess 98
Sourness 38
prints associated with a SMART pattern, which is a chemical language
Saltiness 12
able to specify substructures that describe atomic and bond properties Non-sweetness 233
by means of well-defined rules based on simple extensions of the SMILES Tastelessness 203
notation. Thus, each bit indicates the presence/absence of a particular Multitaste 113
Miscellaneous 87
molecular feature. These MDL structural keys are suitable fingerprints
3

C. Rojas et al. F o o d C h e m i s t r y : M o l e c u l a r S c i e n ces4(2022)100090
4. ChemTastesDB_molecules.zip file, which includes the Hyperchem sodium sulfamate derivatives. The next cluster, Sw3, is formed by the
file (.hin) of each compound optimized by the mechanics force field hesperetin DHC, phloroglucinol, resorcinol, trans-anethole, trans-cinna-
(MM+). Files are named using the molecular IDs of the Chem- maldehyde sweeteners, as well as two dihydrochalcone derivatives, some
TastesDB_database excel file. isocoumarin derivatives and diverse guanidineacetic acid derivatives
(for instance sucrononic acid). Cluster Sw4 includes three subgroups that
The database will be continuously updated by including new mo- comprise other guanidineacetic acid derivatives (for instance bernar-
lecular tastants, when available. To the best of our knowledge, Chem- dame, carrelame and lugduname), acesulfame (and some of its analogues,
TastesDB constitutes the most comprehensive curated database that such as acesulfame K, aspartame-acesulfame or 6-ethyl-acesulfame) and
provides support for decision-making to rationally design new tastants molecules with the phenylsulfonyl fragment in their scaffolds (for
by means of quantitative structure–activity relationships and diverse instance sulfone, ASA 1, ASA 3 and ASA 5). Another interesting cluster is
supervised machine learning approaches. Sw5, which includes 51 halogenated derivatives (mono-, di-, tri- and
tetra- substituted) of both sucrose and galactosucrose, as well as sucralose
and three analogues. The saccharin sweetener and ten of its derivatives
3.2. Analysis of the chemical space
(including sodium, potassium and calcium salts) are located in cluster
Sw6. Cluster Sw7 contains diverse aspartic acid derivatives (for instance
The 2944 molecules included in the ChemTastesDB were used to
aspartame, advantame and neotame), as well as the guanidineacetic acid
define the chemical space of tastants based on their structural similarity and two α-amino acids (D-asparagine and D-glutamine).
provided by the 166 MACCS structural keys. The intent of this analysis is
The class of Bitterant (Bi) compounds (Fig. 2b) has a great dispersion
a comprehensive characterization of the chemical features of tastants
along the t-SNE scatter plot. However, some consistent clusters of bitter-
and an evaluation of how these molecules are structurally clustered.
ants can be identified. Cluster Bi1 includes diverse type of bitterants, such
Since MACCS is a Boolean vector, molecular similarities/dissimilarities
as butalbital, butethal, hexethal sodium, methyprylon, phenallymal, phenytoin
were quantified by means of the Jaccard-Tanimoto distance in the t-
sodium, piperidione, propallylonal. Other compounds located in this group
Distributed Stochastic Neighbor Embedding (t-SNE). We tested diverse
are urea (and 3 derivatives), three sucrose derivatives, butallylonal (and its
values for the parameters to be set in t-SNE by using the following values
sodium salt), four thiouracil derivatives and barbital (with 20 analogues).
for the Exaggeration =[2, 4, 50, 100], Perplexity =[20, 30, 40, 50] and
Cluster Bi2 includes essentially the methylergonovine maleate, 13 lupone
Learning Rate =[100, 500, 900, 1300]. Results were visually inspected
derivatives (dehydrotricycloadlupone, dehydrotricyclocolupone, dehydro-
and the parameters that generated the t-SNE scatter plot with the best
tricyclolupone, hydroperoxytricycloadlupone, hydroxytricycloadlupone,
discrimination of the taste classes as well as the formation of consistent
hydroxytricyclocolupone, hydroxytricyclolupone, nortricycloadlupone, nor-
clusters inside each class were selected: Exaggeration =100, Perplexity
tricyclocolupone, nortricyclolupone, tricycloadlupone, tricyclocolupone and
= 30 and Learning Rate = 100. Fig. 1 presents the chemical space
tricyclolupone), as well as the benzaldehyde bitterant and compounds
defined by the t-SNE scores of the two coordinates. t-SNE generates
which include the benzaldehyde molecular fragment in their scaffold.
interesting low-dimensional clusters of data that represents the distri-
Near to this group, cluster Bi3 includes 16 sodium salt sulfamate de-
butions in the original multidimensional data space. The chemical space
rivatives. On the contrary side of Bi2 and Bi3, cluster Bi4 comprises the
of tastants exhibits a high degree of overlap among the nine classes.
bitterants camphotamide, glimepiride, sulfisoxazole and trimethaphan cam-
However, it is possible to identify some interesting groups, particularly
sylate, as well as 19 bitter saccharin derivatives (for instance 5-methox-
for the basic tastes. In order to thoroughly explore the nature of these
ysaccharin, 5-nitrosaccharin, 6-nitrosaccharin, 7-nitrosaccharin and
clusters, we defined the chemical space in terms of a class/non-class
denatonium saccharide). Cluster Bi5 includes 15 bitterants, such as
scatter plot for the sweet, bitter, umami and sour classes.
azathioprine, chloramphenicol, chrysamminic acid, m-nitrobenzene, nitro-
Fig. 2a shows the distribution of compounds from the Sweetness class
furazone, picric acid (and ammonium picrate), ranitidine hydrochloride, 1-
(Sw) in the chemical space, where some groups with specific structural
nitronaphthalene, 2-amino-5-nitrothiazole, 2-nitroaniline, 2-(cyclohexene-4-
similarities can be identified. The sucrose standard and some of its de-
yl)-1,2-propanediol, 2,4-dinitro-propoxybenzene, 3-(2-(4-nitrophenyl)acet-
rivatives are located in cluster Sw1. Other sweeteners located in this
amido)propanoic acid and 3,4-dinitrobenzoic acid. Near to this group,
cluster are the D-lactulose, palatinose, raffinose, sedoheptulosan, stachyose,
cluster Bi6 includes quinine and its salts; for instance, hydrochloride,
sodium cyclamate, calcium cyclamate chloro-nitroaniline and diverse de-
dihydrochloride and sulfate (bitterness standard). In this cluster, a large
rivatives of sodium sulfamate. On the other hand, cluster Sw2 includes 22
Fig. 1. Scatter plot of the t-SNE coordinates of tastants included in the ChemTastesDB, as obtained on MACCS structural keys. Molecules are colored based on their
taste class.
4

C. Rojas et al. F o o d C h e m i s t r y : M o l e c u l a r S c i e n ces4(2022)100090
Fig. 2. Scatter plot of the t-SNE coordinates. Molecules are colored on the basis of (a) Sweetness, (b) Bitterness, (c) Umaminess and (d) Sourness classes.
number of molecules was identified including 15 denatonium derivatives, scattered along the t-SNE chemical space and overlap with molecules of
several amino acid sequences (6 linear and 28 cyclic) and other com- other classes. Sensory data is subject to a high degree of variation due to
pounds with high molecular similarity among them. wide differences in human perception as measured by sensory panelists.
Umami compounds (Um) are highlighted in Fig. 2c. It is possible to Diverse factors can affect taste perceptions; for instance, presence of
identify five consistent clusters. The first one (Um1) is comprised of the taste modifiers, differences in psychology, anatomy or receptor func-
majority of umami tastants (49 molecules), with salts (disodium, dipo- tionality, as well as the reception, transduction and neural processing of
tassium and calcium) of guanylate, inosine, adenylate, adenosine, electrical impulse information. In fact, many compounds imprint a
riboside and xanthosine. Cluster Um2 includes five umami compounds complex sensation of diverse tastes (basic and non-basic) (Damodaran &
with the presence of amide groups in their scaffolds as a common Parkin, 2017; Rojas et al., 2016c; Wong, 2018). From a chemical point of
characteristic. The umami standard, monosodium L-glutamate (MSG), is view, during the synthesis of new tastants, small variations in the scaf-
grouped in cluster Um3 together with three other glutamates (monop- fold could result in the loss of a specific taste. For instance, the sweetener
otassium glutamate, monoammonium glutamate and monosodium D,L-threo- saccharin became bitter when modified with a chloride or a methyl
β-hydroxy glutamate), two diglutamates (calcium diglutamate and mag- fragment in the meta position (overlapped by bitter tastants), and
nesium diglutamate), two amino acid sequences (Thr-Glu and Glu-Asp- became tasteless when replacing the imino fragment by a methyl, ethyl,
Glu), as well as the monosodium L-aspartate and the monosodium L- or bromoethyl radical (nearest to tasteless compounds) (Rojas et al.,
α-amino adipate. Near to this group, cluster Um4 includes 13 umami 2016c; Rojas et al., 2017).
taste molecules: L-ibotenic acid, L-theanin, L-tricholomic acid (erythro- To the best of our knowledge, only two published studies exist
form), Asp-Glu-Ser, γ-L-glutamyl-L-(S-methyl) methionine, γ-L-glutamyl-L- regarding the definition of the chemical space of tastants based on the t-
cysteinyl-glycine, ethyl 4-((2-isopropyl-5-methylcyclohexyloxy)carbonyl) SNE unsupervised learning approach. One was published in 2019 when
butanoate, N-(3-methoxy-4-hydroxy-benzyl)-5-hydroxypentanamide, N- defining the BitterSweet classifier (Tuwani et al., 2019). The chemical
2,4-dimethoxybenzyl-N-(2-pyridyl)ethyl oxalamide, N-phenethyl-4-hydrox- space developed for the curated molecules and random bioactive com-
ypentanamide, as well as three N-(4-hydroxyphenethyl) derivatives (of pounds (ChEBI) reveals the molecular diversity of bitter, sweet and
the erythronamide, gluconamide and succinamide). On the other hand, tasteless molecules in comparison to random bioactive compounds. The
cluster Um5 contains the 2-mercaptoinosine 5’-monophosphate and seven chemical space also captures clusters in the general chemical domain by
inosinate derivatives, which were divided into sodium salts (disodium 2- reflecting the molecular distribution of taste molecules taken from
methoxy-5’-inosinate, disodium 2-methyl-5’-inosinate, disodium N1-methyl- several bibliographic sources. The second case is based on 316 sweet-
5’-inosinate and disodium N1-methyl-2-methylthio-5’-inosinate) and cal- eners from the SweetenersDB, 4796 molecules from the Super-Natural II
cium salts (calcium inosinate and calcium 2-allyloxy-5’-inosinate). and PhytoLab, and three experimentally tested compounds (namely
Fig. 2d shows the distribution of sourness tastants (So) in the chem- arctiin, ginsenoside Rd and jujuboside A) (Bouysset et al., 2020). The 2D
ical space. Cluster So1 consists of four sulfamate sodium salts, while chemical space was developed in Python using the default parameters
cluster So2 contains 8 imidodisulfuric acid disodium salt derivatives. On (Perplexity = 30, Exaggeration = 12, Learning Rate = 200 and 1000
the other hand, sour tastants found in foods (for instance, acetic acid, iterations). This chemical domain reflects a negligible superposition of
citric acid, lactic acid, malic acid, propionic acid, tartaric acid), as well as the natural compounds with sweet-tasting molecules, which suggest that
carbonic acid, formic acid, phosphoric acid and two sodium salts (sodium 3- a great portion of the natural chemical space remains for further ex-
(sulfonatoamino)benzene-1-sulfonate and sodium N-[4-(butan-2-yl)phenyl] plorations. In addition, it had been stated that the lignan chemical
sulfamate) are located in cluster So3. family constitutes a new chemical space for eliciting new sweet tastants
The remaining sweet, bitter, umami and sour tastants are more through machine learning approaches.
5

C. Rojas et al. F o o d C h e m i s t r y : M o l e c u l a r S c i e n ces4(2022)100090
4. Conclusions Dagan-Wiener, A., Di Pizio, A., Nissim, I., Bahia, M. S., Dubovski, N., Margulis, E., &
Niv, M. Y. (2019). BitterDB: Taste ligands and receptors database in 2019. Nucleic
Acids Research, 47(D1), D1179–D1185. https://doi.org/10.1093/nar/gky974
In this work the authors present the ChemTastesDB, an open-access Damodaran, S., & Parkin, K. L. (2017). Fennema’s food chemistry (5th ed.). CRC Press.
database of 2944 molecular tastants, which are grouped in nine clas- Di Lorenzo, P. M., Chen, J.-Y., Rosen, A. M., & Roussin, A. T. (2009). Tastant. In
ses, including the five basic tastes and four other categories. Curation of M. D. Binder, N. Hirokawa, & U. Windhorst (Eds.), Encyclopedia of neuroscience (pp.
4014–4019). Springer.
molecules and data filtering allowed the collection of information to
Di Pizio, A., Shoshan-Galeczki, Y. B., Hayes, J. E., & Niv, M. Y. (2019). Bitter and sweet
cover a more complete chemical domain with respect to existing data- tasting molecules: It’s complicated. Neuroscience Letters, 700, 56–63. https://doi.org/
bases. This database constitutes a novel tool to increase the information 10.1016/j.neulet.2018.04.027
Durant, J. L., Leland, B. A., Henry, D. R., & Nourse, J. G. (2002). Reoptimization of MDL
of taste molecules and to assist in silico studies for the taste prediction of
keys for use in drug discovery. Journal of Chemical Information and Computer Science,
new compounds. The database is freely accessible at https://doi.org/10. 42(6), 1273–1280. https://doi.org/10.1021/ci010132r
5281/zenodo.5747393. Fourches, D., Muratov, E., & Tropsha, A. (2010). Trust, but verify: On the importance of
chemical structure curation in cheminformatics and QSAR modeling research.
The chemical space of the molecules included in the database was
Journal of Chemical Information and Modeling, 50(7), 1189–1204. https://doi.org/
explored and characterized by means of MACCS keys molecular fin- 10.1021/ci100176x
gerprints analyzed with unsupervised machine learning based on t-SNE. Huang, W., Shen, Q., Su, X., Ji, M., Liu, X., Chen, Y., Lu, S., Zhuang, H., & Zhang, J.
(2016). BitterX: A tool for understanding bitter taste in humans. Scientific Reports, 6,
The analysis enabled the comprehensive characterization of the tastants
Article 23450. 10.1038/srep23450.
chemical space by looking at similarities among chemicals and their Hypercube Inc. HyperChem Professional (Version 8). http://www.hyper.com.
derived clusters. This analysis constitutes a useful approach to visualize Kelly, D. P., Spillane, W. J., & Newell, J. (2005). Development of structure-taste
the similarities/dissimilarities of tastants in multidimensional space and relationships for monosubstituted phenylsulfamate sweeteners using classification
and regression tree (CART) analysis. Journal of Agriculture and Food Chemistry, 53
allows a better understanding of the relationships between molecular (17), 6750–6758. https://doi.org/10.1021/jf0507137
structure and taste. Kim, S., Chen, J., Cheng, T., Gindulyte, A., He, J., He, S., Li, Q., Shoemaker, B. A.,
Thiessen, P. A., & Yu, B. (2019). PubChem 2019 update: Improved access to
chemical data. Nucleic Acids Res., 47(D1), D1102-D1109. 10.1093/nar/gky1033.
Declaration of Competing Interest Ley, J., Reichelt, K., Obst, K., Krammer, G., & Engel, K.-H. (2012). Important tastants and
new developments. In H. Jelen´ (Ed.), Food Flavors. Chemical, sensory and technological
The authors declare that they have no known competing financial properties (pp. 19-33). CRC Press.
Medina-Franco, J. L., S´anchez-Cruz, N., Lo´pez-Lo´pez, E., & Díaz-Eufracio, B. I. (2021).
interests or personal relationships that could have appeared to influence
Progress on open chemoinformatic tools for expanding and exploring the chemical
the work reported in this paper. space. Journal of Computer-Aided Molecular Design. https://doi.org/10.1007/s10822-
021-00399-1
Morini, G., Bassoli, A., & Borgonovo, G. (2011). Molecular modelling and models in the
Acknowledgements
study of sweet and umami taste receptors. A review. Flavour and Fragrance Journal,
26(4), 254–259. https://doi.org/10.1002/ffj.v26.410.1002/ffj.2054
We thank Dr. Wayne R. Hanson for his valuable revision of the Rojas, C., Duchowicz, P. R., Pis Diez, R., & Tripaldi, P. (2016). Applications of
quantitative structure-relative sweetness relationships in food chemistry. In
manuscript and for providing some useful comments for improving the
A. G. Mercader, P. R. Duchowicz, & P. M. Sivakumar (Eds.), Chemometrics
technical quality. applications and research: QSAR in medicinal chemistry (pp. 317–339). Apple Academic
Press.
References Rojas, C., Tripaldi, P., & Duchowicz, P. R. (2016b). A new QSPR study on relative
sweetness. International Journal of Quantitative Structure-Property Relationships, 1(1),
78-92. 10.4018/IJQSPR.2016010104.
Ahmed, J., Preissner, S., Dunkel, M., Worth, C. L., Eckert, A., & Preissner, R. (2011). Rojas, C., Ballabio, D., Consonni, V., Tripaldi, P., Mauri, A., & Todeschini, R. (2016c).
SuperSweet-a resource on natural and artificial sweetening agents. Nucleic Acids Quantitative structure-activity relationships to predict sweet and non-sweet tastes.
Research, 39(Database), D377–D382. https://doi.org/10.1093/nar/gkq917 Theoretical Chemistry Accounts, 135, Article 66. 10.1007/s00214-016-1812-1.
Alvascience. (2020). alvaMolecule (software to view and prepare chemical datasets) Rojas, C., Todeschini, R., Ballabio, D., Mauri, A., Consonni, V., Tripaldi, P., & Grisoni, F.
(Version 1.0.4). https://www.alvascience.com. (2017). A QSTR-based expert system to predict sweetness of molecules. Frontiers in
Alvascience. (2021). alvaDesc (software for molecular descriptors calculation) (Version Chemistry, 5, Article 53. https://doi.org/10.3389/fchem.2017.00053
2.0.6). https://www.alvascience.com. Ruddigkeit, L., & Reymond, J.-L. (2014). The chemical space of flavours. In K. Martinez-
Bai, G., Wu, T., Zhao, L., Wang, X., Li, S., & Ni, X. (2021). CBDPS 1.0: A Python GUI Mayorga, & J. L. Medina-Franco (Eds.), Foodinformatics: Applications of chemical
application for machine learning models to predict bitter-tasting children’s oral information to food chemistry (pp. 83–96). Springer.
medicines. Chemical and Pharmaceutical Bulletin, 69, 989-994. 10.1248/cpb.c20- Ben Shoshan-Galeczki, Y., & Niv, M. Y. (2020). Structure-based screening for discovery of
00866. sweet compounds. Food Chemistry, 315, 126286. https://doi.org/10.1016/j.
Baines, D., & Brown, M. (2016). Flavor enhancers: Characteristics and uses. In foodchem.2020.126286
B. Caballero, P. M. Finglas, & F. Toldr´a (Eds.), Encyclopedia of food and health (pp. Suess, B., Festring, D., & Hofmann, T. (2015). Umami compounds and taste enhancers. In
716–723). Academic Press. J. K. Parker, J. S. Elmore, & L. Methven (Eds.), Flavour development, analysis and
Banerjee, P., & Preissner, R. (2018). BitterSweetForest: A random forest based binary perception in food and beverages (pp. 331–351). Woodhead Publishing.
classifier to predict bitterness and sweetness of chemical compounds. Frontiers in Todeschini, R., Ballabio, D., & Consonni, V. (2015). Distances and other dissimilarity
Chemistry, 6. https://doi.org/10.3389/fchem.2018.00093 measures in chemometrics. In R. A. Meyers (Ed.), Encyclopedia of analytical chemistry:
Bassoli, A., Laureati, M., Borgonovo, G., Morini, G., Servant, G., & Pagliarini, E. (2008). Applications, theory and instrumentation (pp. 1–34). JohnWiley & Sons Ltd.
Isovanillic sweeteners: Sensory evaluation and in vitro assays with human sweet Tuwani, R., Wadhwa, S., & Bagler, G. (2019). BitterSweet: Building machine learning
taste receptor. Chemosensory Perception, 1(3), 174–183. https://doi.org/10.1007/ models for predicting the bitter and sweet taste of small molecules. Scientific Reports,
s12078-008-9027-z 9, Article 7155. 10.1038/s41598-019-43664-y.
Berthold, M. R., Cebron, N., Dill, F., Gabriel, T. R., Ko¨tter, T., Meinl, T., … Wiswedel, B. van der Maaten, L., & Hinton, G. (2008). Visualizing data using t-SNE. Journal of Machine
(2008). KNIME: The konstanz information miner. In C. Preisach, H. Burkhardt, Learning Research, 9, 2579–2605.
L. Schmidt-Thieme, & R. Decker (Eds.), Data analysis, machine learning and Wong, D. W. (2018). Mechanism and theory in food chemistry (2nd ed.). Springer.
applications (pp. 319–326). Berlin Heidelberg: Springer. Yang, Z.-F., Xiao, R., Xiong, G.-L., Lin, Q.-L., Liang, Y., Zeng, W.-B., … Cao, D.-s. (2022).
Bouysset, C., Belloir, C., Antonczak, S., Briand, L., & Fiorucci, S´ebastien (2020). Novel A novel multi-layer prediction approach for sweetness evaluation based on
scaffold of natural compound eliciting sweet taste revealed by machine learning. systematic machine learning modeling. Food Chemistry, 372, 131249. https://doi.
Food Chemistry, 324, 126864. https://doi.org/10.1016/j.foodchem.2020.126864 org/10.1016/j.foodchem.2021.131249
Chandrashekar, J., Hoon, M. A., Ryba, N. J. P., & Zuker, C. S. (2006). The receptors and Zheng, S., Jiang, M., Zhao, C., Zhu, R., Hu, Z., Xu, Y., & Lin, F. (2018). e-Bitter: Bitterant
cells for mammalian taste. Nature, 444, 288-294. 10.1038/nature05401. prediction by the consensus voting from the machine-learning methods. Frontiers in
Charoenkwan, P., Yana, J., Schaduangrat, N., Nantasenamat, C., Hasan, M. M., & Chemistry, 6, Article 82. https://doi.org/10.3389/fchem.2018.00082
Shoombuatong, W. (2020). iBitter-SCM: Identification and characterization of bitter Zheng, S., Chang, W., Xu, W., Xu, Y., & Lin, F. (2019). e-Sweet: A machine-learning based
peptides using a scoring card method with propensity scores of dipeptides. Genomics, platform for the prediction of sweetener and its relative sweetness. Frontiers in
112(4), 2813–2822. https://doi.org/10.1016/j.ygeno.2020.03.019 Chemistry, 7, Article 35. https://doi.org/10.3389/fchem.2019.00035
ChemAxon Ltd. (2021). MarvinSketch (Version 21.17.0). http://www.chemaxon.com.
Dagan-Wiener, A., Nissim, I., Abu, N. B., Borgonovo, G., Bassoli, A., & Niv, M. Y. (2017).
Bitter or not? BitterPredict, a tool for predicting taste from chemical structure.
Scientific Reports, 7, Article 12074. 10.1038/s41598-017-12359-7.
6