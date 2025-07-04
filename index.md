# AnaCal Shear Profile or Abell 360 in ComCam Data

```{abstract}
This technote presents the measurement of the shear profile for the Abell 360
galaxy cluster using ComCam data processed with the AnaCal pipeline. We detail
the procedures involved in bright star masking, source selection, and the
estimation of tangential and cross shear around the cluster center. The
resulting shear profiles provide key insights into the mass distribution of
Abell 360 and demonstrate the capabilities of AnaCal in processing early LSST
data.
```

## Introduction
The Rubin ComCam observing campaign conducted at the end of 2024 targeted seven
fields, including the low ecliptic latitude Rubin SV 38 7 field. This field
hosts the Abell 360 galaxy cluster, an intermediate-mass cluster at redshift
$z = 0.22$, which we use as a commissioning case study to demonstrate Rubin’s
capabilities for weak lensing analyses of galaxy clusters. This technote
presents the lensing shear profile of the Abell 360 cluster as measured with
the AnaCal pipeline. The analysis includes source selection, masking, and shear
estimation steps, serving as an end-to-end demonstration of AnaCal’s
performance on early ComCam data.

## AnaCal Shear Estimation

AnaCal analytical framework to derive the shear response of galaxy shape, flux,
detection and selection processes, offering a precise and generalizable
approach to characterizing how weak gravitational lensing affects measurements
from astronomical images. Instead of relying on numerical shearing or image
simulations, the method starts from first principles by analytically computing
how each pixel in an image responds to an applied shear after deconvolution and
reconvolution with a Gaussian smoothing kernel {cite}`Anacal_Li2023`. This
pixel-level shear response captures the fundamental transformation properties
of the image under lensing distortions.

Building on this, the framework then develops a way to propagate pixel-level
shear responses to derived quantities---such as flux, moments, ellipticities,
detection or selection--that are calculated as functions of the pixels. To do
this systematically, the method introduces a mathematical formalism based on
quintuple numbers {cite}`Anacal_Li2026`, a structure defined by the authors as
a commutative ring tailored for tracking shear derivatives up to second order.
Each quintuple encodes not just the value of a quantity, but also its first and
second derivatives with respect to shear, enabling symbolic propagation of
shear responses through arbitrary algebraic operations.

To address noise bias, the method incorporates a "renoise" correction scheme.
The idea is to construct a "renoised" image by adding a pure noise
field---drawn from the same noise distribution as the original image but
rotated by 90 degrees---to the exposure. This rotation symmetrizes the noise
contribution under shear distortion and allows the authors to analytically
derive the correction term for noise bias in the shear response
{cite}`Anacal_Li2025`. The resulting correction is not only accurate but avoids
the need for noisy simulations, maintaining the fully analytical nature of the
shear response pipeline.


### Bright Star Mask
```{figure} _static/exposure.png
:name: exposure

Coadd image of tract 10463, patch 61, before (left) and after (right) masking
the bright stars.
```

### Match to DM catalog

```{figure} _static/magdiff.png
:name: magdiff
Magnitude difference between DM and AnaCal. Galaxies are, on average, 0.05
magnitudes fainter in AnaCal compared to DM measurements.
```

### Shear Profile

```{figure} _static/shear_profile.png
:name: shear_profile
Tangential and cross shear profile for Abell 360 cluster.
```

# References

```{bibliography}
:style: lsst_aa
