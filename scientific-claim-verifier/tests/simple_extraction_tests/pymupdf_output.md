[Food Chemistry: Molecular Sciences 4 (2022) 100090](https://doi.org/10.1016/j.fochms.2022.100090)


Contents lists available at ScienceDirect

# Food Chemistry: Molecular Sciences


[journal homepage: www.sciencedirect.com/journal/food-chemistry-molecular-sciences](https://www.sciencedirect.com/journal/food-chemistry-molecular-sciences)

## ChemTastesDB : A curated database of molecular tastants


Cristian Rojas [a][,][*], Davide Ballabio [b], Karen Pacheco Sarmiento [a], Elisa Pacheco Jaramillo [a],
Mateo Mendoza [a], Fernando García [c ]


a _Grupo de Investigacion en Quimiometría y QSAR, Facultad de Ciencia y Tecnología, Universidad del Azuay, Av. 24 de Mayo 7-77 y Hern_ ´ _an Malo, Cuenca, Ecuador_ ´
b _Milano Chemometrics and QSAR Research Group. Department of Earth and Environmental Sciences, University of Milano-Bicocca, P.za della Scienza 1-20126, Milano,_
_Italy_
c _Facultad de Ciencias Econ_ ´ _omicas, Universidad Nacional de C_ ´ _ordoba. Centro de Investigaciones en Ciencias Econ_ ´ _omicas, Grupo vinculado CIECS_ – _UNC_ – _CONICET,_
_Cordoba, Argentina_ ´



A R T I C L E I N F O


_Keywords:_

_ChemTastesDB_

Database

Tastes

Chemical space

Foodinformatics


**1. Introduction**



A B S T R A C T


The purpose of this work is the creation of a chemical database named _ChemTastesDB_ that includes both organic
and inorganic tastants. The creation, curation pipeline and the main features of the database are described in
detail. The database includes 2944 verified and curated compounds divided into nine classes, which comprise the
five basic tastes (sweet, bitter, umami sour and salty) along with four additional categories: tasteless, non-sweet,
multitaste and miscellaneous. _ChemTastesDB_ provides the following information for each tastant: name, Pub­
Chem CID, CAS registry number, canonical SMILES, class taste and references to the scientific sources from which
data were retrieved. The molecular structure in the HyperChem ( _.hin_ ) format of each chemical is also made
available. In addition, molecular fingerprints were used for characterizing and analyzing the chemical space of
tastants by means of unsupervised machine learning. _ChemTastesDB_ constitutes a useful tool to the scientific
community to expand the information of taste molecules and to assist _in silico_ studies for the taste prediction of
unevaluated and as yet unsynthetized compounds, as well as the analysis of the relationships between molecular
[structure and taste. The database is freely accessible at https://doi.org/10.5281/zenodo.5747393.](https://doi.org/10.5281/zenodo.5747393)



The sensation of taste plays an important role in the food chemistry
field, since it is closely related to the development and selection of food
products and food intake. Throughout history, there has been a strong
interest in understanding the mechanism by which gustatory sensation
is perceived by humans (Damodaran & Parkin, 2017). The extraordinary
developments in foodinfomatics (computational food chemistry) and
bioinformatics (computational biochemistry) have provided the neces­
sary tools to study the receptor/ligand binding interaction. In order to
achieve a particular taste, it is now understood that the structure of the
receptors and the specific features of the tastant ligands to interact with
receptors must be analyzed (Chandrashekar et al., 2006; Rojas et al.,
2016a). A molecular tastant is a water-soluble chemical compound
(ligand) able to interact with the chemosensory receptors to produce a
taste sensation (Di Lorenzo et al., 2009). The taste-receptor cells (TRCs)
are located in the gustatory papillae of the tongue and palate epithelium,
which react to tastants by means of receptor-ligand interactions along


 - Corresponding author.
_E-mail address:_ [crojasvilla@gmail.com (C. Rojas).](mailto:crojasvilla@gmail.com)



with other mechanisms. These additional mechanisms are associated

with the opening of ion channels or through secondary messenger
channels associated with nucleotides or phosphorylated inositol (Dam­
odaran & Parkin, 2017; Di Lorenzo et al., 2009; Wong, 2018). Evidence
suggests that there are five basic tastes (sweet, bitter, umami, sour and
salty), which are also known as “ _taste modalities_ ” or “ _receptor-mediated_
_tastes_ ” (Chandrashekar et al., 2006; Morini et al., 2011).
Among the basic tastes, sweetness is probably the most important,
since sweeteners evoke a pleasant sensation in several foods and medi­
cines (Chandrashekar et al., 2006; Damodaran & Parkin, 2017). _Sucrose_
is used as a standard to quantify the relative sweetness (RS) of new
sweet-tasting molecules (Rojas et al., 2016a; Rojas et al., 2016b). The
sweet taste chemoreceptor is a G-protein coupled receptor (GPCR) of
class C made up of T1R2/T1R3 subunits (Chandrashekar et al., 2006;
Morini et al., 2011). In contrast to the pleasant sensation of sweetness,
bitterness may be related to the protection of humans from the con­
sumption of toxic compounds (Chandrashekar et al., 2006; Di Lorenzo
et al., 2009), although in some foods or products it is perceived as a



[https://doi.org/10.1016/j.fochms.2022.100090](https://doi.org/10.1016/j.fochms.2022.100090)
Received 23 December 2021; Received in revised form 17 February 2022; Accepted 18 February 2022

Available online 21 February 2022
2666-5662/© 2022 The Author(s). Published by Elsevier Ltd. This is an open access article under the CC BY-NC-ND license


[(http://creativecommons.org/licenses/by-nc-nd/4.0/).](http://creativecommons.org/licenses/by-nc-nd/4.0/)


_C. Rojas et al.                                                                                                                  Food Chemistry: Molecular Sciences 4 (2022) 100090_



pleasant taste. _Quinine sulfate_ is used as the bitterness standard (Dam­
odaran & Parkin, 2017; Rojas et al., 2017). Bitterness receptors are
comprised of a family of T2Rs proteins, which are located on taste re­
ceptor cells. (Chandrashekar et al., 2006; Di Lorenzo et al., 2009).
Umaminess is defined as a meaty or savory sensation (Baines & Brown,
2016; Damodaran & Parkin, 2017; Suess et al., 2015; Wong, 2018) and
_monosodium glutamate_ (MSG) is used as a standard to quantify the rela­
tive intensity of umami tastants (Baines & Brown, 2016). As it is for
sweetness, this taste receptor is a GPCR made up of T1R1/T1R3 subunits
(Chandrashekar et al., 2006; Morini et al., 2011). The taste sensation of
sourness is related to substances that produce hydrogen ions when they
are diluted in water, such as _citric acid_, which is used as the sourness
standard (Damodaran & Parkin, 2017; Ley et al., 2012; Wong, 2018).
Finally, saltiness is a stimulus produced by soluble salts, particularly
salts of low-molecular-weight, such as chlorides (sodium, potassium and
calcium). _Sodium chloride_ is the standard for quantifying saltiness (Di
Lorenzo et al., 2009; Ley et al., 2012; Wong, 2018).
In addition to molecules that elicit the five basic tastes, there are
tastants that evoke other kinds of tastes, such as astringent, chilling,
cooling, heating or pungent (Damodaran & Parkin, 2017; Ley et al.,
2012; Wong, 2018). Other compounds elicit a complex combination of
tastes (multitastes), for instance _potassium acid oxalate_ and _protocatechuic_
_acid_ produce a sour/bitter taste (Wong, 2018), while _calcium phenolsul­_
_fonate_ and _benzyl acetate_ exhibit bitter/astringent and bitter/pungent
tastes, respectively (Dagan-Wiener et al., 2019). Additionally, taste­
lessness refers to insipid molecules, that is, chemicals exhibiting the lack
of any particular taste. This class of compounds involves non-sweet, nonbitter, non-sour, non-salty or non-umami compounds (Damodaran &
Parkin, 2017; Rojas et al., 2017).
The chemical analysis of taste molecules in raw ingredients and in
end-products for human consumption play an important role for the
assurance of food quality and desirability, as well as to prevent defects
(offensive tastes) in consumer food products (Ley et al., 2012). Due to
interest in producing new, safe and more potent tastants (particularly
sweet and bitter), several freely accessible databases containing infor­
mation of taste molecules have been reported in the literature in the last
decade. These databases include: _SuperSweet_ [(http://bioinformatics.ch](http://bioinformatics.charite.de/sweet/)
[arite.de/sweet/) (Ahmed et al., 2011),](http://bioinformatics.charite.de/sweet/) _BitterDB_ [(http://bitterdb.agri.](http://bitterdb.agri.huji.ac.il/)
[huji.ac.il/) (Dagan-Wiener et al., 2019),](http://bitterdb.agri.huji.ac.il/) _TasteDB_ (by merging portions
of the _SuperSweet_ and the _BitterDB_ ) (Ruddigkeit & Reymond, 2014),
_SweetenersDB_ [(http://chemosim.unice.fr/SweetenersDB/)](http://chemosim.unice.fr/SweetenersDB/) (Bouysset
et al., 2020). Additionally, other databases of tastants have been
recently developed for _in silico_ modeling, such as BitterX (Huang et al.,
2016), expert system (Rojas et al., 2017), BitterPredict (Dagan-Wiener
et al., 2017), BitterSweetForest (Banerjee & Preissner, 2018), e-Bitter
(Zheng et al., 2018), e-Sweet (Zheng et al., 2019), BitterSweet (Tuwani
et al., 2019), structure-based screening (Shoshan-Galeczki & Niv, 2020),
BTP640 (Charoenkwan et al., 2020), children’s bitter drug prediction
system (CBDPS) (Bai et al., 2021), and multi-layer prediction system
(Yang et al., 2022).
Given these advances, we developed an extensive database of mo­
lecular structures with associated information on taste. The database is

named _ChemTastesDB_ and includes 2944 organic and inorganic tastants.
For each tastant, the database includes the following information:
PubChem CID, CAS registry number, canonical SMILES, class taste and
references to the scientific sources from where data were retrieved, as
well as the molecular structure in the HyperChem ( _.hin_ ) format. The
overall aim of the _ChemTastesDB_
is to provide a tool to the scientific
community to increase the available information of taste molecules and
to support the development of _in silico_ approaches for taste prediction.
The database is freely available at the following URL: [https://doi.](https://doi.org/10.5281/zenodo.5747393)
[org/10.5281/zenodo.5747393.](https://doi.org/10.5281/zenodo.5747393)



**2. Materials and methods**


_2.1. Data collection_


Data was collected on 4580 molecular tastants from several scientific
sources: 37 papers (including public databases), 3 books and 53 book
chapters. Each molecule was associated with an experimental basic taste
(sweet, bitter, umami, sour or salty) or other gustatory sensations; for
instance, tasteless (neutral taste), non-sweet (lacking sweet), non-bitter,
astringent, cooling, scratchy, burning, heating, pungent, and tingling.
Initially, we adopted the following criteria for a preliminary screening of
the collected data on the specific chemicals:


a. protein tastants were not considered, for instance, _miraculin_, _braz­_

_zein_, _curculin_, _pentadin_, _monellin_ (I and II), _thaumatin_ (I, II, III, a, b and
c) and _mabinlin_ (I and II).
b. water molecules were removed from the hydrated compounds,
because the sensorial evaluation of the taste is performed by a sipspit methodology using aqueous (or hydro-alcoholic) solutions
(Bassoli et al., 2008; Kelly et al., 2005; Rojas et al., 2016a).
c. when dealing with the umami taste, we considered umami com­

pounds, taste-modulating and umami enhancer molecules (Suess
et al., 2015; Wong, 2018).
d. the Haworth projection (Damodaran & Parkin, 2017) was used to
represent the chemical structure of monosaccharides, such as _fruc­_
_tose_, _glucose_, _psicose_ or _tagatose_ .


_2.2. Curation and optimization of molecular structures_


The 3D molecular structures of 4580 tastants were manually repre­
sented using the HyperChem software (Hypercube Inc.). For geometry
optimization, the molecular mechanics force field (MM+) and the con­
jugate gradient algorithm were used. The convergence criteria for ge­
ometry optimization was established when the root mean square
deviation of the gradient vector was less than 0.01 kcal×(Å×mol) [-1] . The
information of stereocenters was used in order to differentiate stereo­

isomers (when available). The information of stereochemistry, when not
available, was obtained from the PubChem open library (Kim et al.,

2019
) and other scientific sources. Otherwise, the default structure
generated by the model builder of HyperChem was used (no confor­
mational analysis was performed).
Since chemical structures available in scientific papers, books (or
chapters) and/or public and commercial databases are not exempt from
errors, we performed a further molecular structure curation. The cura­
tion process of a query compound constitutes a crucial step during the
development of a reliable database to be used in QSAR/QSPR modeling.
Identification of errors in molecular structures includes, for example,
missing atoms or functional groups, misplaced atoms or rearranged
chemical groups. All of these potential errors can negatively influence
the calculation of molecular descriptors, which may have deleterious
effects on subsequent modelling (Fourches et al., 2010).
Thus, the accuracy of molecular structures was initially analyzed in
PubChem (Kim et al., 2019) or other open libraries. Subsequently, the
alvaMolecule software (Alvascience, 2020) was used for molecular
curation to identify molecules with multiple structures, unusual valence,
covalent/ionic bonds, total charge, isotopes, charged atoms, non-carbon
atoms, non-standard atom sets (H, C, N, O, P, S, F, Cl, Br and I), no ar­
omatic ring standardization and radical atoms. These issues were cor­
rected applying some standard criteria as implemented in the software,
such as standardization of benzene rings into aromatic form, conversion
of unusual covalent bonds to ionic forms, addition of charge to quater­
nary nitrogen atom, removal or adding excessive or missing hydrogens,
standardization of nitro, azide and diazo groups, and NOxide compati­
bility. Finally, the CAS registry number and the PubChem CID of each
tastant was also obtained from the PubChem (when available) along
with the search function implemented in alvaMolecule.



2


_C. Rojas et al.                                                                                                                  Food Chemistry: Molecular Sciences 4 (2022) 100090_



For 402 compounds, the name, PubChem CID and CAS registry
number were automatically retrieved from the PubChem library by
means of alvaMolecule. Additionally, the Marvin Sketch (ChemAxon
Ltd., 2021) was used to generate the IUPAC name for 538 molecules,
which were not found when applying the alvaMolecule similarity
search.


_2.3. Database merging and filtering_


Data were further filtered to verify replicated compounds. Initially,
the canonical SMILES (simplified molecular input line entry system) of
the 4580 tastants were generated in alvaMolecule from the HyperChem
3D molecular representation. Subsequently, the chemical name (with
the corresponding taste), CAS registry number, PubChem CID, canonical
SMILES and scientific reference were merged with an in-house KNIME
workflow (Berthold et al., 2008), which included the following filtering
steps:


a. molecules labelled as _3,5-dichlorophenyl guanidineacetic acid deriva­_

_tive_, _4-cyanophenyl guanidineacetic acid derivative_, _compound_, _iso­_
_vanillyl_ _derivative_, _perillartine_ _derivative_ and _phenylsulfamate_
_monosubstituted_ were excluded;
b. molecules exhibiting the exact match of name, CAS number or
PubChem CID were merged into a single entry;
c. molecules excluded in step a) were considered together with the
molecules processed in step b), and a new curation step was applied
to find chemicals with the same molecular structure by comparing
canonical SMILES. Stereoisomers (for instance _D-glucose_ and _L-_
_glucose_ ) were not considered in this step;
d. molecules exhibiting multiple-valued tastes were assigned to the
most frequent taste class with a majority voting approach. When
multiple-valued tastes were tied, the tastant was included in the
miscellaneous class;
e. molecules with the following tastes were included in the miscella­

neous class: astringent, cooling, hot burning, heating, pungent, and
tingling. The same criterion was adopted to assign compounds
labelled with an ambiguous class (bitter/burning/scratchy, bitter/
tasteless, non-bitter, non-bitter/burning, non-sweet/sweet, sweet/
bitter, sweet/tasteless).


_2.4. Analysis of the chemical space of tastants_


Chemical space (Medina-Franco et al., 2021) is a useful concept in
diverse areas of computational chemistry including chemoinformatics
and foodinformatics. The chemical space is defined by all chemicals
represented by a _N_ -dimensional vector of features (for instance MACCS)
that captures the most relevant chemical information of compounds.
Thus, this multidimensional space aims to conceptualize molecular
similarities by identifying regions where molecules are clustered by
their features. The most suitable way to visualize and analyze the
chemical space is by the projection of similarities/dissimilarities into a
low-dimensional space by means of diverse unsupervised machine
learning approaches. Previous studies have analyzed the chemical
spaces of taste molecules by applying Principal Component Analysis
(PCA) (Dagan-Wiener et al., 2017; Di Pizio et al., 2019; Ruddigkeit &
Reymond, 2014), Multidimensional Scaling (MDS) (Rojas et al., 2017),
and the t-Distributed Stochastic Neighbor Embedding (t-SNE) (Bouysset
et al., 2020; Tuwani et al., 2019).
In this study, structural characteristics of molecular tastants were
represented by means of the Molecular ACCess System (MACCS) fin­
gerprints (Durant et al., 2002). These are 2D binary fixed size finger­
prints associated with a SMART pattern, which is a chemical language
able to specify substructures that describe atomic and bond properties
by means of well-defined rules based on simple extensions of the SMILES
notation. Thus, each bit indicates the presence/absence of a particular
molecular feature. These MDL structural keys are suitable fingerprints



for substructure searching or molecular similarity. The alvaDesc soft­
ware (Alvascience, 2021) was used to calculate the binary 166 MACCS
fingerprints starting with the molecular SMILES.
The chemical space was defined through molecular similarity/di­
versity analysis based on the t-Distributed Stochastic Neighbor Embed­
ding (t-SNE) (van der Maaten & Hinton, 2008), which attempts to
project tastants fingerprints into a two-dimensional space (ℝ [N ] → ℝ [2] ), in
such a way as to preserve the local structure. To calculate the pairwise
similarities in low-dimensional space, t-SNE uses a symmetrized version
of the cost function with simpler gradients to facilitate the optimization
process, as well as the heavy-tailed Student-t distribution to overcome
the crowding problem. This unsupervised approach is able to match
pairwise similarity distributions in both higher-dimensional space and
lower-dimensional space to preserve the local structure of data. Conse­
quently, t-SNE efficiently captures the local structure of the highdimensional space, while eliciting the presence of clusters at several
scales (structure of the data). The pairwise similarities were calculated
Todeschini
by means of the Jaccard-Tanimoto similarity coefficient (
et al., 2015). This well-known binary similarity coefficient emphasizes
the presence of common features omitting the absence of common fea­
tures and the simple matching accounting for both presence and absence
of common features.


_2.5. Software and code_


HyperChem version 8 was used for drawing and displaying chemical
structure of molecular tastants, while the chemical structures were

checked and curated in the alvaMolecule software. An in-house KNIME
workflow was programmed for filtering the database. MACCS finger­
prints were calculated in alvaDesc. MATLAB was used to calculate t-SNE
models.


**3. Results and discussion**


_3.1. ChemTastesDB description_


The curated _ChemTastesDB_ consisted of 2944 compounds grouped
into nine classes, which include the five basic tastes (sweet, bitter,
umami, sour and salty) and four additional classes (non-sweet, tasteless,
multitaste and miscellaneous). Table 1 lists the number of molecules
included in each class. The _ChemTastesDB_ [is freely available at https://d](https://doi.org/10.5281/zenodo.5747393)
[oi.org/10.5281/zenodo.5747393, and includes four files:](https://doi.org/10.5281/zenodo.5747393)


1. a pdf file (ChemTastesDB_readme.pdf) containing a complete
description of the _ChemTastesDB_ ;
2. an excel file (ChemTastesDB_database.xls), where the following data
are collected for each tastant: molecular ID, name, PubChem CID,
CAS registry number, canonical SMILES string, class taste and
reference to the scientific sources from which data were retrieved;
3. an excel file (ChemTastesDB_references.xls), containing a compre­

hensive list of all scientific references with their extended details;


**Table 1**

Number of molecular tastants included in the nine classes of the

curated _ChemTastesDB_ .


Tastant class Number of molecules


Sweetness 977

Bitterness 1183

Umaminess 98

Sourness 38

Saltiness 12

Non-sweetness 233

Tastelessness 203

Multitaste 113

Miscellaneous 87



3


_C. Rojas et al.                                                                                                                  Food Chemistry: Molecular Sciences 4 (2022) 100090_



4. ChemTastesDB_molecules.zip file, which includes the Hyperchem
_.hin_
file ( ) of each compound optimized by the mechanics force field
(MM+). Files are named using the molecular IDs of the Chem­
TastesDB_database excel file.


The database will be continuously updated by including new mo­
lecular tastants, when available. To the best of our knowledge, _Chem­_
_TastesDB_ constitutes the most comprehensive curated database that
provides support for decision-making to rationally design new tastants

–
by means of quantitative structure activity relationships and diverse
supervised machine learning approaches.


_3.2. Analysis of the chemical space_


The 2944 molecules included in the _ChemTastesDB_ were used to
define the chemical space of tastants based on their structural similarity
provided by the 166 MACCS structural keys. The intent of this analysis is
a comprehensive characterization of the chemical features of tastants
and an evaluation of how these molecules are structurally clustered.
Since MACCS is a Boolean vector, molecular similarities/dissimilarities
were quantified by means of the Jaccard-Tanimoto distance in the tDistributed Stochastic Neighbor Embedding (t-SNE). We tested diverse
values for the parameters to be set in t-SNE by using the following values
for the Exaggeration = [2, 4, 50, 100], Perplexity = [20, 30, 40, 50] and
Learning Rate = [100, 500, 900, 1300]. Results were visually inspected
and the parameters that generated the t-SNE scatter plot with the best
discrimination of the taste classes as well as the formation of consistent

clusters inside each class were selected: Exaggeration = 100, Perplexity
= 30 and Learning Rate = 100. Fig. 1 presents the chemical space
defined by the t-SNE scores of the two coordinates. t-SNE generates
interesting low-dimensional clusters of data that represents the distri­
butions in the original multidimensional data space. The chemical space
of tastants exhibits a high degree of overlap among the nine classes.
However, it is possible to identify some interesting groups, particularly
for the basic tastes. In order to thoroughly explore the nature of these
clusters, we defined the chemical space in terms of a class/non-class
scatter plot for the sweet, bitter, umami and sour classes.

Fig. 2a shows the distribution of compounds from the Sweetness class
(Sw) in the chemical space, where some groups with specific structural
_sucrose_ standard and some of its de­
similarities can be identified. The
rivatives are located in cluster Sw1. Other sweeteners located in this
cluster are the _D-lactulose_, _palatinose_, _raffinose_, _sedoheptulosan_, _stachyose_,
_sodium cyclamate_, _calcium cyclamate chloro-nitroaniline_ and diverse de­
rivatives of _sodium sulfamate_ . On the other hand, cluster Sw2 includes 22



sodium sulfamate derivatives. The next cluster, Sw3, is formed by the
_hesperetin DHC_, _phloroglucinol_, _resorcinol_, _trans-anethole_, _trans-cinna­_
_maldehyde_ sweeteners, as well as two dihydrochalcone derivatives, some
isocoumarin derivatives and diverse guanidineacetic acid derivatives
(for instance _sucrononic acid_ ). Cluster Sw4 includes three subgroups that
comprise other guanidineacetic acid derivatives (for instance _bernar­_
_dame_, _carrelame_ and _lugduname_ ), _acesulfame_ (and some of its analogues,
such as _acesulfame K_, _aspartame-acesulfame_ or _6-ethyl-acesulfame_ ) and
molecules with the phenylsulfonyl fragment in their scaffolds (for
instance _sulfone_, _ASA 1_, _ASA 3_ and _ASA 5_ ). Another interesting cluster is
Sw5, which includes 51 halogenated derivatives (mono-, di-, tri- and
tetra- substituted) of both _sucrose_ and _galactosucrose_, as well as _sucralose_
and three analogues. The _saccharin_ sweetener and ten of its derivatives
(including sodium, potassium and calcium salts) are located in cluster
Sw6. Cluster Sw7 contains diverse aspartic acid derivatives (for instance
_aspartame_, _advantame_ and _neotame_ ), as well as the _guanidineacetic acid_
and two α-amino acids ( _D-asparagine_ and _D-glutamine_ ).
The class of Bitterant (Bi) compounds (Fig. 2b) has a great dispersion
along the t-SNE scatter plot. However, some consistent clusters of bitter­
ants can be identified. Cluster Bi1 includes diverse type of bitterants, such
as _butalbital_, _butethal_, _hexethal sodium_, _methyprylon_, _phenallymal_, _phenytoin_
_sodium_, _piperidione_, _propallylonal_ . Other compounds located in this group
are _urea_ (and 3 derivatives), three sucrose derivatives, _butallylonal_ (and its
sodium salt), four thiouracil derivatives and _barbital_ (with 20 analogues).
Cluster Bi2 includes essentially the _methylergonovine maleate_, 13 lupone
derivatives ( _dehydrotricycloadlupone_, _dehydrotricyclocolupone_, _dehydro­_
_tricyclolupone_, _hydroperoxytricycloadlupone_, _hydroxytricycloadlupone_,
_hydroxytricyclocolupone_, _hydroxytricyclolupone_, _nortricycloadlupone_, _nor­_
_tricyclocolupone_, _nortricyclolupone_, _tricycloadlupone_, _tricyclocolupone_ and
_tricyclolupone_ ), as well as the _benzaldehyde_ bitterant and compounds
which include the benzaldehyde molecular fragment in their scaffold.
Near to this group, cluster Bi3 includes 16 sodium salt sulfamate de­
rivatives. On the contrary side of Bi2 and Bi3, cluster Bi4 comprises the
bitterants _camphotamide_, _glimepiride_, _sulfisoxazole_ and _trimethaphan cam­_
_sylate_, as well as 19 bitter saccharin derivatives (for instance _5-methox­_
_ysaccharin_, _5-nitrosaccharin_, _6-nitrosaccharin_, _7-nitrosaccharin_ and
_denatonium saccharide_ ). Cluster Bi5 includes 15 bitterants, such as
_azathioprine_, _chloramphenicol_, _chrysamminic acid_, _m-nitrobenzene_, _nitro­_
_furazone_, _picric acid_ (and _ammonium picrate_ ), _ranitidine hydrochloride_, _1-_
_nitronaphthalene_, _2-amino-5-nitrothiazole_, _2-nitroaniline_, _2-(cyclohexene-4-_
_yl)-1,2-propanediol_, _2,4-dinitro-propoxybenzene_, _3-(2-(4-nitrophenyl)acet­_
_amido)propanoic acid_ and _3,4-dinitrobenzoic acid_ . Near to this group,
cluster Bi6 includes _quinine_ and its salts; for instance, hydrochloride,
dihydrochloride and sulfate (bitterness standard). In this cluster, a large



**Fig. 1.** Scatter plot of the t-SNE coordinates of tastants included in the _ChemTastesDB_, as obtained on MACCS structural keys. Molecules are colored based on their
taste class.


4


_C. Rojas et al.                                                                                                                  Food Chemistry: Molecular Sciences 4 (2022) 100090_


**Fig. 2.** Scatter plot of the t-SNE coordinates. Molecules are colored on the basis of (a) Sweetness, (b) Bitterness, (c) Umaminess and (d) Sourness classes.



number of molecules was identified including 15 denatonium derivatives,
several amino acid sequences (6 linear and 28 cyclic) and other com­
pounds with high molecular similarity among them.
Umami compounds (Um) are highlighted in Fig. 2c. It is possible to
identify five consistent clusters. The first one (Um1) is comprised of the
majority of umami tastants (49 molecules), with salts (disodium, dipo­
tassium and calcium) of guanylate, inosine, adenylate, adenosine,
riboside and xanthosine. Cluster Um2 includes five umami compounds
with the presence of amide groups in their scaffolds as a common
characteristic. The umami standard, _monosodium L-glutamate_ (MSG), is
grouped in cluster Um3 together with three other glutamates ( _monop­_
_otassium glutamate_, _monoammonium glutamate_ and _monosodium D,L-threo-_
_β-hydroxy glutamate_ ), two diglutamates ( _calcium diglutamate_ and _mag­_
_nesium diglutamate_ ), two amino acid sequences ( _Thr-Glu_ and _Glu-Asp-_
_Glu_ ), as well as the _monosodium L-aspartate_ and the _monosodium L-_
_α-amino adipate_ . Near to this group, cluster Um4 includes 13 umami
taste molecules: _L-ibotenic acid_, _L-theanin_, _L-tricholomic acid_ ( _erythro_ form), _Asp-Glu-Ser_, _γ-L-glutamyl-L-(S-methyl) methionine_, _γ-L-glutamyl-L-_
_cysteinyl-glycine_, _ethyl 4-((2-isopropyl-5-methylcyclohexyloxy)carbonyl)_
_butanoate_, _N-(3-methoxy-4-hydroxy-benzyl)-5-hydroxypentanamide_, _N-_
_2,4-dimethoxybenzyl-N-(2-pyridyl)ethyl oxalamide_, _N-phenethyl-4-hydrox­_
_ypentanamide_, as well as three N-(4-hydroxyphenethyl) derivatives (of
the erythronamide, gluconamide and succinamide). On the other hand,
cluster Um5 contains the _2-mercaptoinosine 5’-monophosphate_ and seven
inosinate derivatives, which were divided into sodium salts ( _disodium 2-_
_methoxy-5’-inosinate_, _disodium 2-methyl-5’-inosinate_, _disodium N1-methyl-_
_5’-inosinate_ and _disodium N1-methyl-2-methylthio-5’-inosinate_ ) and cal­
cium salts ( _calcium inosinate_ and _calcium 2-allyloxy-5’-inosinate_ ).

Fig. 2d shows the distribution of _sourness_ tastants (So) in the chem­
ical space. Cluster So1 consists of four sulfamate sodium salts, while
cluster So2 contains 8 imidodisulfuric acid disodium salt derivatives. On

the other hand, sour tastants found in foods (for instance, _acetic acid_,
_citric acid_, _lactic acid_, _malic acid_, _propionic acid_, _tartaric acid_ ), as well as
_carbonic acid_, _formic acid_, _phosphoric acid_ and two sodium salts ( _sodium 3-_
_(sulfonatoamino)benzene-1-sulfonate_ and _sodium N-[4-(butan-2-yl)phenyl]_
_sulfamate_ ) are located in cluster So3.
The remaining sweet, bitter, umami and sour tastants are more



scattered along the t-SNE chemical space and overlap with molecules of
other classes. Sensory data is subject to a high degree of variation due to
wide differences in human perception as measured by sensory panelists.
Diverse factors can affect taste perceptions; for instance, presence of
taste modifiers, differences in psychology, anatomy or receptor func­
tionality, as well as the reception, transduction and neural processing of
electrical impulse information. In fact, many compounds imprint a
complex sensation of diverse tastes (basic and non-basic) (Damodaran &
Parkin, 2017; Rojas et al., 2016c; Wong, 2018). From a chemical point of
view, during the synthesis of new tastants, small variations in the scaf­
fold could result in the loss of a specific taste. For instance, the sweetener
_saccharin_
became bitter when modified with a chloride or a methyl
fragment in the _meta_ position (overlapped by bitter tastants), and
became tasteless when replacing the imino fragment by a methyl, ethyl,
or bromoethyl radical (nearest to tasteless compounds) (Rojas et al.,
2016c; Rojas et al., 2017).
To the best of our knowledge, only two published studies exist
regarding the definition of the chemical space of tastants based on the tSNE unsupervised learning approach. One was published in 2019 when
defining the BitterSweet classifier (Tuwani et al., 2019). The chemical
space developed for the curated molecules and random bioactive com­
pounds (ChEBI) reveals the molecular diversity of bitter, sweet and
tasteless molecules in comparison to random bioactive compounds. The
chemical space also captures clusters in the general chemical domain by
reflecting the molecular distribution of taste molecules taken from
several bibliographic sources. The second case is based on 316 sweet­
eners from the _SweetenersDB_, 4796 molecules from the Super-Natural II
and PhytoLab, and three experimentally tested compounds (namely
_arctiin_, _ginsenoside Rd_ and _jujuboside A_ ) (Bouysset et al., 2020). The 2D
chemical space was developed in Python using the default parameters
(Perplexity = 30, Exaggeration = 12, Learning Rate = 200 and 1000
iterations). This chemical domain reflects a negligible superposition of
the natural compounds with sweet-tasting molecules, which suggest that
a great portion of the natural chemical space remains for further ex­
plorations. In addition, it had been stated that the lignan chemical
family constitutes a new chemical space for eliciting new sweet tastants
through machine learning approaches.



5


_C. Rojas et al.                                                                                                                  Food Chemistry: Molecular Sciences 4 (2022) 100090_



**4. Conclusions**


In this work the authors present the _ChemTastesDB_, an open-access
database of 2944 molecular tastants, which are grouped in nine clas­
ses, including the five basic tastes and four other categories. Curation of
molecules and data filtering allowed the collection of information to
cover a more complete chemical domain with respect to existing data­
bases. This database constitutes a novel tool to increase the information

of taste molecules and to assist _in silico_ studies for the taste prediction of
[new compounds. The database is freely accessible at https://doi.org/10.](https://doi.org/10.5281/zenodo.5747393)
[5281/zenodo.5747393.](https://doi.org/10.5281/zenodo.5747393)

The chemical space of the molecules included in the database was
explored and characterized by means of MACCS keys molecular fin­
gerprints analyzed with unsupervised machine learning based on t-SNE.
The analysis enabled the comprehensive characterization of the tastants
chemical space by looking at similarities among chemicals and their
derived clusters. This analysis constitutes a useful approach to visualize
the similarities/dissimilarities of tastants in multidimensional space and
allows a better understanding of the relationships between molecular
structure and taste.


**Declaration of Competing Interest**


The authors declare that they have no known competing financial
interests or personal relationships that could have appeared to influence
the work reported in this paper.


**Acknowledgements**


We thank Dr. Wayne R. Hanson for his valuable revision of the
manuscript and for providing some useful comments for improving the
technical quality.


**References**


Ahmed, J., Preissner, S., Dunkel, M., Worth, C. L., Eckert, A., & Preissner, R. (2011).
SuperSweet-a resource on natural and artificial sweetening agents. _Nucleic Acids_
_Research, 39_ [(Database), D377–D382. https://doi.org/10.1093/nar/gkq917](https://doi.org/10.1093/nar/gkq917)
Alvascience. (2020). alvaMolecule (software to view and prepare chemical datasets)
(Version 1.0.4). https://www.alvascience.com.
Alvascience. (2021). alvaDesc (software for molecular descriptors calculation) (Version
2.0.6). https://www.alvascience.com.
Bai, G., Wu, T., Zhao, L., Wang, X., Li, S., & Ni, X. (2021). CBDPS 1.0: A Python GUI
application for machine learning models to predict bitter-tasting children’s oral
medicines. _Chemical and Pharmaceutical Bulletin, 69_, 989-994. 10.1248/cpb.c2000866.

[Baines, D., & Brown, M. (2016). Flavor enhancers: Characteristics and uses. In](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0025)
[B. Caballero, P. M. Finglas, & F. Toldr´a (Eds.),](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0025) _Encyclopedia of food and health_ (pp.
[716–723). Academic Press.](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0025)
Banerjee, P., & Preissner, R. (2018). BitterSweetForest: A random forest based binary
classifier to predict bitterness and sweetness of chemical compounds. _Frontiers in_
_Chemistry, 6_ [. https://doi.org/10.3389/fchem.2018.00093](https://doi.org/10.3389/fchem.2018.00093)
Bassoli, A., Laureati, M., Borgonovo, G., Morini, G., Servant, G., & Pagliarini, E. (2008).
Isovanillic sweeteners: Sensory evaluation and in vitro assays with human sweet
taste receptor. _Chemosensory Perception, 1_ [(3), 174–183. https://doi.org/10.1007/](https://doi.org/10.1007/s12078-008-9027-z)
[s12078-008-9027-z](https://doi.org/10.1007/s12078-008-9027-z)

¨
[Berthold, M. R., Cebron, N., Dill, F., Gabriel, T. R., Kotter, T., Meinl, T., … Wiswedel, B.](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0040)
[(2008). KNIME: The konstanz information miner. In C. Preisach, H. Burkhardt,](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0040)
[L. Schmidt-Thieme, & R. Decker (Eds.),](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0040) _Data analysis, machine learning and_
Bouysset, C., Belloir, C., Antonczak, S., Briand, L., & Fiorucci, S _applications_ [(pp. 319–326). Berlin Heidelberg: Springer.](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0040) ´ebastien (2020). Novel
scaffold of natural compound eliciting sweet taste revealed by machine learning.
_Food Chemistry, 324_ [, 126864. https://doi.org/10.1016/j.foodchem.2020.126864](https://doi.org/10.1016/j.foodchem.2020.126864)
Chandrashekar, J., Hoon, M. A., Ryba, N. J. P., & Zuker, C. S. (2006). The receptors and
cells for mammalian taste. _Nature, 444_, 288-294. 10.1038/nature05401.
Charoenkwan, P., Yana, J., Schaduangrat, N., Nantasenamat, C., Hasan, M. M., &
Shoombuatong, W. (2020). iBitter-SCM: Identification and characterization of bitter
peptides using a scoring card method with propensity scores of dipeptides. _Genomics,_
_112_ [(4), 2813–2822. https://doi.org/10.1016/j.ygeno.2020.03.019](https://doi.org/10.1016/j.ygeno.2020.03.019)
ChemAxon Ltd. (2021). MarvinSketch (Version 21.17.0). http://www.chemaxon.com.
Dagan-Wiener, A., Nissim, I., Abu, N. B., Borgonovo, G., Bassoli, A., & Niv, M. Y. (2017).
Bitter or not? BitterPredict, a tool for predicting taste from chemical structure.
_Scientific Reports, 7_, Article 12074. 10.1038/s41598-017-12359-7.



Dagan-Wiener, A., Di Pizio, A., Nissim, I., Bahia, M. S., Dubovski, N., Margulis, E., &
Niv, M. Y. (2019). BitterDB: Taste ligands and receptors database in 2019. _Nucleic_
_Acids Research, 47_ [(D1), D1179–D1185. https://doi.org/10.1093/nar/gky974](https://doi.org/10.1093/nar/gky974)
Damodaran, S., & Parkin, K. L. (2017). _[Fennema’s food chemistry](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0075)_ (5th ed.). CRC Press.
[Di Lorenzo, P. M., Chen, J.-Y., Rosen, A. M., & Roussin, A. T. (2009). Tastant. In](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0080)
[M. D. Binder, N. Hirokawa, & U. Windhorst (Eds.),](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0080) _Encyclopedia of neuroscience_ (pp.
[4014–4019). Springer.](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0080)
Di Pizio, A., Shoshan-Galeczki, Y. B., Hayes, J. E., & Niv, M. Y. (2019). Bitter and sweet
tasting molecules: It’s complicated. _Neuroscience Letters, 700_ [, 56–63. https://doi.org/](https://doi.org/10.1016/j.neulet.2018.04.027)
[10.1016/j.neulet.2018.04.027](https://doi.org/10.1016/j.neulet.2018.04.027)
Durant, J. L., Leland, B. A., Henry, D. R., & Nourse, J. G. (2002). Reoptimization of MDL
keys for use in drug discovery. _Journal of Chemical Information and Computer Science,_
_42_ [(6), 1273–1280. https://doi.org/10.1021/ci010132r](https://doi.org/10.1021/ci010132r)
Fourches, D., Muratov, E., & Tropsha, A. (2010). Trust, but verify: On the importance of
chemical structure curation in cheminformatics and QSAR modeling research.
_Journal of Chemical Information and Modeling, 50_ [(7), 1189–1204. https://doi.org/](https://doi.org/10.1021/ci100176x)
[10.1021/ci100176x](https://doi.org/10.1021/ci100176x)
Huang, W., Shen, Q., Su, X., Ji, M., Liu, X., Chen, Y., Lu, S., Zhuang, H., & Zhang, J.
(2016). BitterX: A tool for understanding bitter taste in humans. _Scientific Reports, 6_,
Article 23450. 10.1038/srep23450.
Hypercube Inc. HyperChem Professional (Version 8). http://www.hyper.com.
Kelly, D. P., Spillane, W. J., & Newell, J. (2005). Development of structure-taste
relationships for monosubstituted phenylsulfamate sweeteners using classification
and regression tree (CART) analysis. _Journal of Agriculture and Food Chemistry, 53_
[(17), 6750–6758. https://doi.org/10.1021/jf0507137](https://doi.org/10.1021/jf0507137)
Kim, S., Chen, J., Cheng, T., Gindulyte, A., He, J., He, S., Li, Q., Shoemaker, B. A.,
Thiessen, P. A., & Yu, B. (2019). PubChem 2019 update: Improved access to
chemical data. _Nucleic Acids Res., 47_ (D1), D1102-D1109. 10.1093/nar/gky1033.
Ley, J., Reichelt, K., Obst, K., Krammer, G., new developments. In H. Jelen (Ed.), ´ _Food Flavors. Chemical, sensory and technological_ & Engel, K.-H. (2012). Important tastants and
Medina-Franco, J. L., S _properties_ (pp. 19-33). CRC Press. ´anchez-Cruz, N., Lopez-L´ opez, E., & Díaz-Eufracio, B. I. (2021). ´
Progress on open chemoinformatic tools for expanding and exploring the chemical
space. _Journal of Computer-Aided Molecular Design_ [. https://doi.org/10.1007/s10822-](https://doi.org/10.1007/s10822-021-00399-1)
[021-00399-1](https://doi.org/10.1007/s10822-021-00399-1)

Morini, G., Bassoli, A., & Borgonovo, G. (2011). Molecular modelling and models in the
study of sweet and umami taste receptors. A review. _Flavour and Fragrance Journal,_
_26_ [(4), 254–259. https://doi.org/10.1002/ffj.v26.410.1002/ffj.2054](https://doi.org/10.1002/ffj.v26.410.1002/ffj.2054)
[Rojas, C., Duchowicz, P. R., Pis Diez, R., & Tripaldi, P. (2016). Applications of](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0135)
[quantitative structure-relative sweetness relationships in food chemistry. In](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0135)
[A. G. Mercader, P. R. Duchowicz, & P. M. Sivakumar (Eds.),](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0135) _Chemometrics_
_[applications and research: QSAR in medicinal chemistry](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0135)_ (pp. 317–339). Apple Academic

[Press.](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0135)

Rojas, C., Tripaldi, P., & Duchowicz, P. R. (2016b). A new QSPR study on relative
sweetness. _International Journal of Quantitative Structure-Property Relationships, 1_ (1),
78-92. 10.4018/IJQSPR.2016010104.
Rojas, C., Ballabio, D., Consonni, V., Tripaldi, P., Mauri, A., & Todeschini, R. (2016c).
Quantitative structure-activity relationships to predict sweet and non-sweet tastes.
_Theoretical Chemistry Accounts, 135_, Article 66. 10.1007/s00214-016-1812-1.
Rojas, C., Todeschini, R., Ballabio, D., Mauri, A., Consonni, V., Tripaldi, P., & Grisoni, F.
(2017). A QSTR-based expert system to predict sweetness of molecules. _Frontiers in_
_Chemistry, 5_ [, Article 53. https://doi.org/10.3389/fchem.2017.00053](https://doi.org/10.3389/fchem.2017.00053)
[Ruddigkeit, L., & Reymond, J.-L. (2014). The chemical space of flavours. In K. Martinez-](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0155)
[Mayorga, & J. L. Medina-Franco (Eds.),](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0155) _Foodinformatics: Applications of chemical_
_[information to food chemistry](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0155)_ (pp. 83–96). Springer.
Ben Shoshan-Galeczki, Y., & Niv, M. Y. (2020). Structure-based screening for discovery of
sweet compounds. _Food Chemistry, 315_ [, 126286. https://doi.org/10.1016/j.](https://doi.org/10.1016/j.foodchem.2020.126286)
[foodchem.2020.126286](https://doi.org/10.1016/j.foodchem.2020.126286)

[Suess, B., Festring, D., & Hofmann, T. (2015). Umami compounds and taste enhancers. In](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0165)
[J. K. Parker, J. S. Elmore, & L. Methven (Eds.),](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0165) _Flavour development, analysis and_
_perception in food and beverages_ [(pp. 331–351). Woodhead Publishing.](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0165)
[Todeschini, R., Ballabio, D., & Consonni, V. (2015). Distances and other dissimilarity](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0170)
[measures in chemometrics. In R. A. Meyers (Ed.),](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0170) _Encyclopedia of analytical chemistry:_
_[Applications, theory and instrumentation](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0170)_ (pp. 1–34). JohnWiley & Sons Ltd.
Tuwani, R., Wadhwa, S., & Bagler, G. (2019). BitterSweet: Building machine learning
models for predicting the bitter and sweet taste of small molecules. _Scientific Reports,_
_9_, Article 7155. 10.1038/s41598-019-43664-y.
[van der Maaten, L., & Hinton, G. (2008). Visualizing data using t-SNE.](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0180) _Journal of Machine_
_[Learning Research, 9](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0180)_, 2579–2605.
Wong, D. W. (2018). _[Mechanism and theory in food chemistry](http://refhub.elsevier.com/S2666-5662(22)00018-1/h0185)_ (2nd ed.). Springer.
Yang, Z.-F., Xiao, R., Xiong, G.-L., Lin, Q.-L., Liang, Y., Zeng, W.-B., … Cao, D.-s. (2022).
A novel multi-layer prediction approach for sweetness evaluation based on
systematic machine learning modeling. _Food Chemistry, 372_ [, 131249. https://doi.](https://doi.org/10.1016/j.foodchem.2021.131249)
[org/10.1016/j.foodchem.2021.131249](https://doi.org/10.1016/j.foodchem.2021.131249)
Zheng, S., Jiang, M., Zhao, C., Zhu, R., Hu, Z., Xu, Y., & Lin, F. (2018). e-Bitter: Bitterant
prediction by the consensus voting from the machine-learning methods. _Frontiers in_
_Chemistry, 6_ [, Article 82. https://doi.org/10.3389/fchem.2018.00082](https://doi.org/10.3389/fchem.2018.00082)
Zheng, S., Chang, W., Xu, W., Xu, Y., & Lin, F. (2019). e-Sweet: A machine-learning based
platform for the prediction of sweetener and its relative sweetness. _Frontiers in_
_Chemistry, 7_ [, Article 35. https://doi.org/10.3389/fchem.2019.00035](https://doi.org/10.3389/fchem.2019.00035)



6


