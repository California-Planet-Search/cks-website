# The California-Kepler Survey

## Project Info

The California-Kepler Survery (CKS) is a database of 1305 spectra of "Kepler Objects of Interest" (KOIs) hosting 2025 planet candidates. The CKS project was initiated by Andrew Howard, Geoff Marcy, and John Johnson. Spectra were observed from 2011 to 2015. The core component of CKS was to obtain a Keck/HIRES spectra of all KOIs brighter than kepmag of 14.2. Fainter stars were appended for a variety of reasons. The CKS dataset consists of several subsets:

1. Magnitude-limited (Kp < 14.2; N = 960)
2. Multi-planet hosts (N = 484)
3. Ultra-short period hosts (P < 1 day; N = 71)
4. Habitable Zone hosts (N = 127)

## Attribution 

The CKS dataset is described in two papers

1. [CKS-I](https://arxiv.org/abs/1703.10402): "The California-Kepler Survey. I. High Resolution Spectroscopy of 1305 Stars Hosting Kepler Transiting Planets" (Petigura, Howard, Marcy, et al. 2017)

2. [CKS-II](https://arxiv.org/abs/1703.10402): "The California-Kepler Survey. II. Precise Physical Properties of 2025 Kepler Planets and Their Host Stars" (Johnson, Petigura, Fulton, et al. 2017)

## Other papers Using CKS data

1. [CKS-III](https://arxiv.org/abs/1703.10402): "The California-Kepler Survey. I. High Resolution Spectroscopy of 1305 Stars Hosting Kepler Transiting Planets" (Petigura, Howard, Marcy, et al. 2017)

## Spectra 

Spectra are available via

1. A gzipped tarball (size = 2.8GB) [[download]](http://www.astro.caltech.edu/~howard/cks/cks-spectra.tgz) 
2. Individually [[here]](http://www.astro.caltech.edu/~howard/cks/spectra/) 

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


### ToDo: Howard, please explain the spectrum format and give an example of how to read in.

## Parameters

Parameters are available via

- The [ExoFOP](https://exofop.ipac.caltech.edu/kepler/welcome.php) (account required) 
- As a single csv file [[download]](http://www.astro.caltech.edu/~howard/cks/cksphys-merged.csv) click [[here]](http://www.astro.caltech.edu/~howard/cks/column-definitions.txt) for column definitions
