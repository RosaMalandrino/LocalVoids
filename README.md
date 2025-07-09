# A Bayesian catalog of 100 high-significance voids in the Local Universe

We present the catalog of 100 cosmic voids obtained with the method described in [TBD]() and in the dedicated [website](https://voids.cosmictwin.org).

Produced in the Bayesian framework of the [Manticore project](https://cosmictwin.org), we are able to precisely characterize our Local Neighborhood, producing a void catalog matching real structures in the dark matter distribution, as opposed to artifacts of the galaxy surveys.  
Our voids have well-defined centers, shapes, and boundaries, making the catalog practical to use for all applications that need precise characterization of the density environment (e.g. galaxy properties and their evolution, galaxy biasing, supernovae, and high-energy astrophysics).
The Bayesian nature of this framework provides us with a rigorous estimation of statistical uncertainties, producing high-quality data products for the community. 


## Summary features

The main features of the catalog are summarized in the ```voids_catalog.csv``` table. You can use the ```pandas``` library to read it and analyze it:

```
import pandas as pd
voids_catalog = pd.read_csv('voids_catalog.csv')
```

The columns are organized as follows:

- ```[center x (Mpc/h)]```, ```[std x (Mpc/h)]```, ```[center y (Mpc/h)]```, ```[std y (Mpc/h)]```, ```[center z (Mpc/h)]```, ```[std z (Mpc/h)]``` are the mean and standard deviation of the posterior distribution of the void positions;
- ```[mean radius (Mpc/h)]```, ```[std radius (Mpc/h)]``` are the mean and standard deviation of the posterior distribution of the void radii;
- ```[center RA [hms]]```, ```[center RA [deg]]```, ```[center Dec [deg]]``` represent the void's position in the sky, in equatorial coordinates (with right ascension presented in different units);
- ```[center dist [Mpc/h]]``` is the distance of the void centers from the observer;
- ```[redshift near]```, ```[redshift center]```, ```[redshift far]``` represent the redshift of the closest edge, the center, and the farthest edge along the line of sight;
- ```[redshift near [km/s]]```, ```[redshift center [km/s]]```, ```[redshift far [km/s]]``` are the same quantities as above, but presented in $\text{km s}^{-1}$.

The simulation box is centered in $[340.5, 340.5, 340.5] \ h^{−1} \ \text{Mpc}$, the xy plane corresponding to the equatorial plane, and the $\hat{z}$ axis pointing to the equatorial North Pole.
The assumed cosmology to project in the sky is: $(\Omega_m, h) = (0.306, 681)$.

This table can be already used as a first approximation of the full void catalog.

## Shape of voids

The ```VoronoiClouds/``` directory presents the probability clouds of each individual void. Each file, named ```Voronoi_cloud_void_i_N32.npy```, contains the information of a $32^3$ grid with size equal to $4 \times R_\text{void}$, with $R_\text{void}$ the statistical radius of the void obtained from the mean posterior.
You can load them in a dictionary with the following lines:

```
import numpy as np
VoroClouds = {i:np.load(f'VoronoiClouds/Voronoi_cloud_void_{i}_N32.npy') for i in range(100)}
```

The i-th cloud can be accessed with the corresponding key, e.g. cloud #0:

```
VoroCloud = VoroClouds[0]
VoroCloud.shape
```
with ```VoroCloud.shape = (32768, 4)```
The information is:

- ```VoroCloud[:,:3]``` represent the (x,y,z) coordinates of the grid;
- ```VoroCloud[:, 3]``` represents the value of the Voronoi overlap rate in that position.

In order to reconstruct the grid shape:

```
VoroCloud_Grid = np.reshape(VoroCloud, (32,32,32,4))
```

with:
- ```VoroCloud_Grid[:,:,:,0]```, ```VoroCloud_Grid[:,:,:,1]```, ```VoroCloud_Grid[:,:,:,2]``` are the x, y, z mesh coordinates of the 3D grid;
- ```VoroCloud_Grid[:,:,:,3]``` is the Voronoi overlap on the 3D grid.



The files contain the full untruncated Voronoi clouds, including the outskirts. We recommend to fix a threshold ```th``` and subsample the cloud as ```VoroCloud[:, 3]>th```.

In order to conserve the statistical volume of the voids the optimal threshold value is ```th = 0.37```; to select the interior at $\sim 80%$ of the radius, choose ```th = 0.72```.

Find the threshold that works best for you! In the plot below we present the truncation threshold on the $x$-axis, and the resulting radius of the Voronoi cloud, as a fraction of the statistical radius on the $y$-axis. Try different values of ```th``` to probe different density regimes within the void. The function is presented in the ```truncation_vs_radius.npy``` array:

```
thresholds = np.load('truncation_vs_radius.npy')
```
with ```thresholds.shape = (100)```. The index ```i``` represent 100 times ```th```, e.g. ```thresholds[37]```  gives access to the radius obtained with the 0.37 truncation level.

![](https://github.com/RosaMalandrino/LocalVoids/blob/gh-pages/assets/images/min_Voronoi_rate_vs_radius_with_clouds.png)


## Global Voronoi cloud

We provide the global Voronoi clouds, obtained by painting the individual cloud on a $64^3$ grid with resolution of $$. TDespite the lower resolution, this dataset contains information on the interplay between voids.
```
VoroCloudAll = np.load('Voronoi_cloud_all_voids_N64.npy')```

with ```VoroCloudAll.shape = (262144, 4)```

The information is organized in the same way as the individual clouds, with:

- ```VoroCloudAll[:,:3]``` represent the (x,y,z) coordinates of the grid;
- ```VoroCloudAll[:, 3]``` represents the value of the Voronoi overlap rate in that position.

To reconstruct the grid:

```
VoroCloudAll_Grid = np.reshape(VoroCloudAll, (64,64,64,4))
```

