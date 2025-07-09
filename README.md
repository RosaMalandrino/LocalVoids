# A Bayesian catalog of 100 high-significance cosmic voids in the Local Universe

We present the catalog obtained with the method described in [TBD]() and in the dedicated [website](https://voids.cosmictwin.org).



## Summary features

The main features of the catalog are summarized in the ```voids_catalog.csv``` table. You can use ```pandas``` to read it:

```
import pandas as pd
voids_catalog = pd.read_csv('voids_catalog.csv')
```

The columns are organized as follows:

- ```center x (Mpc/h)```, ```std x (Mpc/h)```, ```center y (Mpc/h)```, ```std y (Mpc/h)```, ```center z (Mpc/h)```, ```std z (Mpc/h)``` are the mean and standard deviation of the posterior distribution of the void positions;
- ```mean radius (Mpc/h)```, ```std radius (Mpc/h)``` are the mean and standard deviation of the posterior distribution of the void radii;
- ```center RA [hms]```, ```center RA [deg]```, ```center Dec [deg]``` represent the void's position in the sky, in equatorial coordinates (with right ascension presented in different units);
- ```center dist [Mpc/h]``` is the distance of the void centers from the observer;
- ```redshift near```, ```redshift center```, ```redshift far``` represent the redshift of the closest edge, the center, and the farthest edge along the line of sight;
- ```redshift near [km/s]```, ```redshift center [km/s]```, ```redshift far [km/s]``` are the same quantities as above, but presented in $\text{km s}^{-1}$.

The simulation box is centered in $[340.5, 340.5, 340.5] \, h^{−1} \, \text{Mpc}$, the xy plane corresponding to the equatorial plane, and the $\hat{z}$ axis pointing to the equatorial North Pole.
The assumed cosmology to convert between $h^{-1} \, \text{Mpc}$ and redshift is: $(\Omega_m, h) = (0.306, 681)$.

This table can be already used as a first approximation of the full void catalog.

## Shape of voids

The ```VoronoiClouds/``` directory presents the probability clouds of each individual void. Each file, named ```Voronoi_cloud_void_i_N32.npy```, contains the information of a $32^3$ grid with size equal to $4 \times R_\text{void}$, with $R_\text{void}$ the statistical radius of the void obtained from the mean posterior. The array has shape ```[32**3,4]```, and it is organized as follows:

- columns ```[:,:3]``` represent the (x,y,z) coordinates of the grid
- columns ```[:, 3]``` represents the value of the Voronoi overlap rate in that position.

The files contain the full untruncated Voronoi clouds, including the outskirts. We recommend to fix a threshold ```th``` and subsample the cloud as ```[:, 3]>th```.

In order to conserve the statistical volume of the voids the optimal threshold value is ```th = 0.37```; to select the interior at $\sim 80/%$ of the radius, choose ```th = 0.72```.

Find the threshold that works best for you! In the plot below we present the truncation threshold on the $x$-axis, and the resulting radius of the Voronoi cloud, as a fraction of the statistical radius on the $y$-axis. Try different values of ```th``` to probe different density regimes within the void. The function is presented in the ```name``` array, where the index ```i``` represent ```100*th```, and ```v[i]``` the resulting radius ratio.

[include image here]

