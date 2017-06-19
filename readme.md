# The California-Kepler Survey

## Project Info

The California-Kepler Survery (CKS) is a project to measure precise properties of planets and thier host stars discovered by NASA's Kepler Mission.  There are 1305 CKS spectra of "Kepler Objects of Interest" (KOIs) hosting 2025 planet candidates. The CKS project was initiated by Andrew Howard, Geoff Marcy, John Johnson, Tim Morton, and Howard Isaacson.  Spectra were obtained from 2011 to 2015. The core goal of CKS was to obtain a high-resolution spectrum with HIRES at the W. M. Keck Observatory of all KOIs with Kp (Kepler magnitude) < 14.2. Fainter stars were appended for a variety of reasons. 

The overlapping CKS stellar samples are:

1. Magnitude-limited (Kp < 14.2; N<sub>star</sub> = 960, N<sub>planet</sub> = 1385)
2. Multi-planet hosts (N<sub>star</sub> = 484, N<sub>planet</sub> = 1254)
3. Ultra-short period hosts (P < 1 day; N<sub>star</sub> = 127, N<sub>planet</sub> = 127)
4. Habitable Zone hosts (N<sub>star</sub> = 71, N<sub>planet</sub> = 71)
5. Other (N<sub>star</sub> = 38, N<sub>planet</sub> = 38)

## Attribution 

The CKS dataset is described in two papers

1. [CKS-I](https://arxiv.org/abs/1703.10400): "The California-Kepler Survey. I. High Resolution Spectroscopy of 1305 Stars Hosting Kepler Transiting Planets" (Petigura, Howard, Marcy, Johnson, Isaacson, et al. 2017)

2. [CKS-II](https://arxiv.org/abs/1703.10402): "The California-Kepler Survey. II. Precise Physical Properties of 2025 Kepler Planets and Their Host Stars" (Johnson, Petigura, Fulton, Marcy, Howard, et al. 2017)

## Other papers Using CKS data

1. [CKS-III](https://arxiv.org/abs/1703.10375): "The California-Kepler Survey. III. A Gap in the Radius Distribution of Small Planets" (Fulton, Petigura, Howard, Isaacson, Marcy, et al. 2017)

## CKS Contributors (alphabetical)

Phillip A. Cargile, Ian J. M. Crossfield, Benjamin J. Fulton, Leslie Hebb, Lea A. Hirsch, Andrew W. Howard, Howard Isaacson, John Asher Johnson, Geoffrey W. Marcy, Timothy D. Morton, Erik A. Petigura, Leslie A. Rogers, Evan Sinukoff, Lauren M. Weiss, Joshua N. Winn

## Parameters

Parameters are available via

- The [ExoFOP](https://exofop.ipac.caltech.edu/kepler/welcome.php) (account required) 
- As a single csv file [[download]](http://www.astro.caltech.edu/~howard/cks/cks_physical_merged.csv) click [[here]](http://www.astro.caltech.edu/~howard/cks/column-definitions.txt) for column definitions

## Spectra 

See CKS-I for a detailed description of the CKS spectra from Keck-HIRES.  Spectra are available via

- The [ExoFOP](https://exofop.ipac.caltech.edu/kepler/welcome.php) (account required) 
- A gzipped tarball (size = 2.8GB) [[download]](http://www.astro.caltech.edu/~howard/cks/cks-spectra.tgz) 
- Individually [[here]](http://www.astro.caltech.edu/~howard/cks/spectra/) 

Naming convention for individual spectra is

```
cks-<id_starname>_<chip><id_obs>.fits
```

e.g.

```
cks-k00001_bj122.742.fits

- <k00001> = KOI-1
- <b> = Blue chip
- <j122.742> = Unique CPS spectrum identifier
```


## File Format
 Each Keck/HIRES spectrum consists of three individual files. Each file is prefixed with an 

'i' (6540-8000 Ang), 

'r' (4975-6420 Ang), or 

'b' (3640-4800 Ang), 

indicating the wavelength range covered. The CKS spectral analysis uses only the central ('r') spectrum.
 
 Within each .fits file, there are three extensions of equal dimemsions. The first extension is the spectrum itself, in echelle format. The vertical axis is flux, in arbitray units. The blaze function has been removed from each spectral order.  The signal to noise ratio has been preserved in the second extension, which gives the fractional error per pixel. The third extension holds the rest frame wavelength solution, which is accurate to plus or minus one pixel.
 
- Example of how to open a spectrum:
IDL

```
IDL> im=readfits('cks-K00001_rj122.742.fits',hd)

Read the fractional error:
IDL> err =readfits('cks-K00001_rj122.742.fits',exten=1,hd)

Read the pixel by pixel wavelength solution (error = +/- 1 pixel)
IDL> wave=readfits('cks-K00001_rj122.742.fits.fits',exten=2,hd)
```
 
 Python

```
from astropy.io import fits
hdulist = fits.open('cks-K00001_rj122.742.fits.fits')
hdulist.info()
Filename: cks-K00001_rj122.742.fits
No.    Name         Type      Cards   Dimensions   Format
0    PRIMARY     PrimaryHDU     722   (4021, 16)   float32   
1                ImageHDU         7   (4021, 16)   float32   
2                ImageHDU         7   (4021, 16)   float64   

Isolate the spectrum, fractional error and wavelength solution
spec = hdulist[0].data
frac_err = hdulist[1].data
wave_sol = hdulist[2].data
```
