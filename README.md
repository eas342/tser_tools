# Welcome to Time Series Tools!

## Installation
 - Clone this git repository and `pip install` any dependencies.

### Dependencies
 - `astropy`, `numpy`
 - `ccdphot` - only needed for data reduction of photometric data
 - `emcee` - only needed for time series analysis and model fitting
 - `miescatter` - only needed for fitting Mie extinction to spectra

## Usage for Data Reduction
Edit `parameters/reduction_parameters.yaml`. You can specify any number of directories for reducing data.
Execute `nohup python prep_images.py &` to run the reduction in the background.

## Usage for Time Series Aperture Photometry
Create a photometry parameters file from the example in `parameters/phot_parameters.yaml`.
You will need to specify a list of files, source name and a list of source coordinates in pixels [x,y].
The first source should be the target and the rest will be reference stars.
Specify the aperture geometry, sizes as well as the box finding size for locating sources.
The `jdRef` parameter specifies a reference epoch for time series plots.
Run the following commands in either an iPython session or in a python script:

```python
phot = phot_pipeline.phot(paramFile='parameters/aug2016_corot1_parameters.yaml')
phot.do_phot()
phot.showCustSet()
```
where 'parameters/aug2016_corot1_parameters.yaml' is the name of the `yaml` parameters file.

## Usage for Time Series Model Fitting