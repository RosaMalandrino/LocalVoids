---
layout: splash
classes: wide
author_profile: false
title: Mapping high-significance cosmic voids in the Local Universe


header:
  overlay_image: /assets/images/test-header.png
  caption: "Photo credit: Chris Wren and Kenn Brown/mondoworks"
  actions:
    - label: "Explore the voids in 3D"
      url: "assets/html_files/all_voids_Voronoi_cloud_N64_pmin0.37_wireframe.html"

---




## A precise characterization of the voids in our Local Neighborhood


We present a new method to identify cosmic voids in the Local Universe from galaxy surveys, and to assess their statistical significance.
Leveraging the state-of-the-art Bayesian reconstructions of the Universe from the [Manticore project](https://cosmictwin.org){:target="_blank"}, we are able to precisely characterize our Local Neighborhood, producing a catalog of voids that are real structures in the dark matter distribution, as opposed to artifacts of the galaxy surveys. 
Our voids have well-defined centers, shapes, and boundaries, making the catalog practical to use for all applications that need precise characterization of the density environment. The Bayesian nature of this framework provides us with a rigorous estimation of statistical uncertainties, producing high-quality data products for the community. <br>

Our catalog of 100 cosmic voids is presented. Click [here](assets/html_files/all_voids_Voronoi_cloud_N64_pmin0.37_wireframe.html){:target="_blank"} to explore the voids in the <b>interactive</b> version of this plot.




<!-- 
<div>
  <iframe id="allVoids"
    title="Full catalog of voids"
    src="assets/html_files/all_voids_Voronoi_cloud_N64_pmin0.37_wireframe.html"
    width='1200'
    height='900'
    frameborder='0'
    >
  </iframe>
</div>
-->

![image-right](/assets/images/all_clouds.png){: .align-center}



## Reconstructing cosmic structure from incomplete observations of the sky

Our method allows to bypass some of the challenges of direct detection of voids from galaxy surveys, such as holes in the mask or magnitude selection. The <tt>BORG</tt> [algorithm](https://academic.oup.com/mnras/article/432/2/894/1020272){:target="_blank"} running at the core of the posterior simulations is able to reconstruct structures from incomplete data, providing predictions in unobserved regions such as behind the galactic plane. We are able to provide a precise characterization of voids in these difficult locations.

![image-right](/assets/gifs/voids_on_the_sky_galCoord.gif){: .align-center}



## Precise characterization of void morphology and its relationship with the environment

Understanding the complex morphology of voids is crucial to study many astrophysical objects whose properties depend on the density environment.
We provide a full description of the void shape in terms of a function we name Voronoi cloud, where higher values correspond the to innermost part of voids. A more detailed description can be found in the [Method](_pages/Method.md){:target="_blank"} section.

<div>
  <iframe id="exampleVoid"
    title="Single void morphology"
    src="VoidGallery/Void10/void_10_Voronoi_cloud_N32_with_galaxies.html"
    width='1200'
    height='1000'
    frameborder='0'
    >
  </iframe>
</div>



Our probabilistic detection of voids perfectly matches the underlying halo field inferred from Manticore, confirming the quality of our catalog and the reliability for the community to use. We encourage anyone who has interest in this work to [download](_pages/Download.md){:target="_blank"} the catalog and use it for their research! 


![image-center](/VoidGallery/Void10/void_10_z_slices_withMarginal.gif){: style="width:100%" .align-center}






### References

* This work <br>
<b> R. Malandrino, G. Lavaux, B. D. Wandelt, S. McAlpine, J. Jasche </b> <br>
<i> (in prep.) </i>

* The Manticore Project I: a digital twin of our cosmic neighbourhood from Bayesian field-level analysis <br>
<b> S. McAlpine, J. Jasche, M. Ata, G. Lavaux, R. Stiskalek, C. S. Frenk, A. Jenkins </b> <br>
[Monthly Notices of the Royal Astronomical Society (2025) 540, 1, 716](https://academic.oup.com/mnras/article/540/1/716/8128029){:target="_blank"}; [arXiv:2505.10682](https://arxiv.org/pdf/2505.10682){:target="_blank"}