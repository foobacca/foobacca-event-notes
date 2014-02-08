Python in Astronomy
===================

* Dr Haley Gomez
* @astrofairy

* astronomy then - look through a telescope and sketch what you see on paper
* astronomy now - have digital photos, colour, hubble ... - also x-ray, radio spectrums
* 1970 - FITS format - 1st successful cross-platform sharing - metadata and long term data storage
* problems: big data, rich data - survey astronomy (lots of telescopes - 1 exabyte/day)

* 4 years ago still teaching fortran
* now moving to python
* if you want to use hubble data (or kepler, SKA ...) you need to use python
* python can communicate with fortran!
* many py packages for astronomy - PyFITS, PyWCS, astlib, CosmoPy ... (though so many it's hard to navigate/choose)
* make one package to rule them all - astropy (only required dependency is Numpy)
* ``import cosmology`` :)
* astropy is well tested, documented, community consensus as to what to include, cross platform, easy to install, python 3
* nice units conversion, define own units
* plot FITS files, combine images from different telescopes
* machine learning - trying to find signal amongst the noise
