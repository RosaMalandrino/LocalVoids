# A Bayesian catalog of 100 high-significance cosmic voids in the Local Universe

We present the catalog obtained with the method described in [TBD]() and in the dedicated [website](https://voids.cosmictwin.org).



## Summary features

The main features of the catalog are summarized in the ```name``` table, organized as follows:

- void ID
- coordinates mean and std
- radius mean and std
- sky coordinates
- redshift range

This table is a first approximation that can be already used

## Shape of voids

The ```VoronoiClouds/``` directory presents the probability clouds of each individual void. Each file, named ```Voronoi_cloud_void_i_N32.npy```, contains the information of a $32^3$ grid with size equal to $4 \times R_\text{void}$, with $R_\text{void}$ the statistical radius of the void obtained from the mean posterior. The array has shape ```[32**3,4]```, and it is organized as follows:

- columns ```[:,:3]``` represent the (x,y,z) coordinates of the grid
- columns ```[:, 3]``` represents the value of the Voronoi overlap rate in that position.

The files contain the full untruncated Voronoi clouds, including the outskirts. We recommend to fix a threshold ```th``` and subsample the cloud as ```[:, 3]>th```.

In order to conserve the statistical volume of the voids the optimal threshold value is ```th = 0.37```; to select the interior at $\sim 80/%$ of the radius, choose ```th = 0.72```.

Find the threshold that works best for you! In the plot below we present the truncation threshold on the $x$-axis, and the resulting radius of the Voronoi cloud, as a fraction of the statistical radius on the $y$-axis. Try different values of ```th``` to probe different density regimes within the void. The function is presented in the ```name``` array, where the index ```i``` represent ```100*th```, and ```v[i]``` the resulting radius ratio.

[include image here]

