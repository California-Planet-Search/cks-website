# The California-Kepler Survey

## Project Info

The California-Kepler Survery (CKS) is a database of 1305 spectra of "Kepler Objects of Interest" (KOIs) hosting 2025 planet candidates. The CKS project was initiated by Andrew Howard, Geoff Marcy, and John Johnson. Spectra were observed from 2011 to 2015. The core goal of CKS was to obtain a Keck/HIRES spectrum of all KOIs with kepmag < 14.2. Fainter stars were appended for a variety of reasons. 

The CKS dataset consists of several subsets:

1. Magnitude-limited (Kp < 14.2; N = 960)
2. Multi-planet hosts (N = 484)
3. Ultra-short period hosts (P < 1 day; N = 71)
4. Habitable Zone hosts (N = 127)

## Attribution 

The CKS dataset is described in two papers

1. [CKS-I](https://arxiv.org/abs/1703.10400): "The California-Kepler Survey. I. High Resolution Spectroscopy of 1305 Stars Hosting Kepler Transiting Planets" (Petigura, Howard, Marcy, et al. 2017)

2. [CKS-II](https://arxiv.org/abs/1703.10402): "The California-Kepler Survey. II. Precise Physical Properties of 2025 Kepler Planets and Their Host Stars" (Johnson, Petigura, Fulton, et al. 2017)

## Other papers Using CKS data

1. [CKS-III](https://arxiv.org/abs/1703.10375): "The California-Kepler Survey. III. A Gap in the Radius Distribution of Small Planets" (Fulton, Petigura, Howard, et al. 2017)

## Spectra 

Spectra are available via

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
 'i' (3640-4800 Ang), 
 'r' (4975-6420 Ang), or 
 'b'(6540-8000 Ang) 
 indicating the wavelength range covered. The CKS spectral analysis uses only the central ('r') spectrum.
 
 Within each .fits file, there are three extensions of equal dimemsions. The first extension is the spectrum itself, in echelle format. The vertical axis is flux, in arbitray units. The blaze function has been removed from each spectral order.  The signal to noise ratio has been preserved in the second extension, which gives the fractional error per pixel. The third extension holds the rest frame wavelength solution, which is accurate to plus or minus one pixel.
 
Example of how to open a spectrum:
- IDL

```IDL> im=readfits('cks-K00001_rj122.742.fits',hd)

Read the fractional error:
IDL> im=readfits('cks-K00001_rj122.742.fits',exten=1,hd)

Read the pixel by pixel wavelength solution (error = +/- 1 pixel)
IDL> im=readfits('cks-K00001_rj122.742.fits.fits',exten=2,hd)
```
- Python
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

## Parameters

Parameters are available via

- The [ExoFOP](https://exofop.ipac.caltech.edu/kepler/welcome.php) (account required) 
- As a single csv file [[download]](http://www.astro.caltech.edu/~howard/cks/cks_physical_merged.csv) click [[here]](http://www.astro.caltech.edu/~howard/cks/column-definitions.txt) for column definitions
