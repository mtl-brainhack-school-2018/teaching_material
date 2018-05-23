# Introduction to Nipype

[Nipype](https://github.com/nipy/nipype) is a python-based workflow constructor for fMRI preprocessing and analysis.
There are an [excellent series of tutorials](https://miykael.github.io/nipype_tutorial/) for introducing Nipype based analyses, which I strongly encourage you to check out!

If your tool of interest (e.g., [AFNI 3dTagaline](https://afni.nimh.nih.gov/pub/dist/doc/program_help/3dTagalign.html)), is not availablle in Nipype, they have a great guide on [how to add interfaces](http://nipype.readthedocs.io/en/latest/devel/interface_specs.html).

# Introduction to FMRIPrep

One tool that uses Nipype based workflows is [FMRIPrep](https://github.com/poldracklab/fmriprep/).
FMRIPrep is a [BIDS App](http://bids-apps.neuroimaging.io/about/), which means it works on [BIDS](http://bids.neuroimaging.io/) datasets and runs on [OpenNeuro](https://openneuro.org).

FMRIPrep runs preprocessing on [many](https://github.com/poldracklab/fmriprep/issues/1056) [kinds](https://github.com/poldracklab/fmriprep/pull/875) [of fMRI](https://github.com/poldracklab/fmriprep/issues/310) datasets, and generates [visual summary reports](http://fmriprep.readthedocs.io/en/latest/outputs.html#visual-reports).
Check out the [usage guide](http://fmriprep.readthedocs.io/en/latest/usage.html) for specific options you can supply. 
