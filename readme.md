# Introduction to the Data

Here we provide the [galaxy catalog](./Data/zcosmos_galaxy.dat) and [group catalog](./data/zcosmos_group.dat) in COSMOS volume based on zCOSMOS[ [Lily at al. 2009][1]] spectroscopic survey and COSMOS2015[[Laigle at al. 2015][2]] photometric catalog.

The [demo code](./DemoCode/script.py) shows the usage of the group catalog with python.

## Galaxy selection criteria:

1. $I_{\rm AB} < 22.5$;
2. $0.1 \le z \le 1.0$
3. $\rm 149.617 < RA < 150.603$, $\rm 1.767 < Dec < 2.703$
4. Exclude confidence class: 0, 1.1, 2.1, and 9.1 [[Lily at al. 2009][1]]

# Data format

## Galaxy catalog

The galaxies are sorted with ascending galaxy id, so the galaxy id equals row index starting from zero. Besides, galaxies in a command group are in continuous rows with satellites following the central galaxy. So you can use the galaxy of central galaxy with the richness to access all the galaxies in a common group easily.

**Columns:**

1. `ID`: unique ID of galaxies, which can be used to match galaxies across the galaxy and group catalogs;
2. `SurveyID`: ID of galaxies from the original survey data release. This can be used to match galaxies across our catalogs and the original survey data release;
3. `ID2015`: Galaxy ID in [Laigle at al. 2015][2];
4. `GroupID`: ID of the group of which a galaxy is a member, -1 for photometric galaxy with no group assignment;
5. `RA`: right ascension (J2000) in degrees;
6. `Dec`: declination (J2000) in degrees;
7. `z`: photometric redshift for confidence class = -1, spectroscopic redshift otherwise;
8. `StellarMass`: 10-based logarithm of the galaxy in units of $\rm M_{\odot}$
9. `tag`: 1 for central, 0 for satellite;
10. `CC`: redshift conﬁdence class, -1 for photometric galaxies, others see  [Lily at al. 2009][1];

## Group catalog

The groups are sorted with ascending group id, which means the group id equals row index starting from zero, so you can access the group property using group id as row index.

**Columns:**

1. `GroupID`: a unique ID of each group in the group catalog;
2. `cenID`: galaxy ID of the central galaxy of a group;
3. `cenID2015`: central galaxy ID in [Laigle at al. 2015][2];
4. `RA_avg`: Right Ascension (J2000) of the group center in degrees, deﬁned as the average RA of member galaxies weighted by the stellar mass;
5. `dec_avg`: Declination (J2000) of the group center in degrees, deﬁned as the average Dec of member galaxies weighted by the stellar mass;
6. `z_avg`: redshift of the group, deﬁned as the average redshift of member galaxies with spectroscopic redshift weighted by the stellar mass;
7. `HaloMass`: 10-based logarithm of the halo mass of a group in units of $\rm M_{\odot}$;
8. `GroupTag`: 0 for groups with only spectroscopic members, 1 for groups with photometric central and spectroscopic member, and 2 for groups with only one photometric member;
9. `Richness`: number of member galaxies in a group.

[1]: https://iopscience.iop.org/article/10.1088/0067-0049/184/2/218	"THE zCOSMOS 10k-BRIGHT SPECTROSCOPIC SAMPLE"
[2]: https://iopscience.iop.org/article/10.3847/0067-0049/224/2/24	"THE COSMOS2015 CATALOG: EXPLORING THE 1 < z < 6 UNIVERSE WITH HALF A MILLION GALAXIES"
