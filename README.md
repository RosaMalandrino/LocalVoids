# A Bayesian catalog of 100 high-significance cosmic voids in the Local Universe

We present a cat


## Summary features

The main features of the catalog are summarized in the ```name``` table, organized as follows:

- void ID
- coordinates mean and std
- radius mean and std
- sky coordinates
- redshift range

This table is a first approximation that can be already used

## Shape of voids

The ```VoronoiClouds``` directory presents the probability clouds of each individual void. Each file, named ```bla bla bla``` is a $(32^3, 4)$ vector, organized as follows:

- columns ```[:,:3]``` represent the (x,y,z) coordinates of the grid
- columns ```[:, 3]``` represents the value of the Voronoi overlap rate in that position.


