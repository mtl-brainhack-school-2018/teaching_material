# Preprocessing

There are a few well established steps usually performed on fMRI data before extracting metrics of interest that can be entered into a group statistical model:
  * registration of individual anatomy in a reference template space (either volumetric or surface).
  * realignment of different BOLD time samples (within and between run, across modalities, may include field map correction).
  * Noise reduction (regression of confounds, ICA).

There are many available pipelines. Selection with documentation:
  * the fMRIprep [documentation](http://fmriprep.readthedocs.io/en/latest/).
  * the cifty [documentation](https://edickie.github.io/ciftify/#/03_cifti-for-your_fmri).
  * the Neuroimaging analysis kit [documentation](http://niak.simexp-lab.org/pipe_preprocessing.html) and companion [slides](https://figshare.com/articles/Preprocessing_of_fMRI_data/1368669).

Check this [paper](https://arxiv.org/pdf/1608.03616.pdf) and this [paper](https://www.biorxiv.org/content/biorxiv/early/2017/06/27/156380.full.pdf) for a comparison of different preprocessing strategies and this [book](https://global.oup.com/academic/product/an-introduction-to-resting-state-fmri-functional-connectivity-9780198808220?cc=ca&lang=en&) for an overview of preprocessing steps.

# Quality control

Checking the quality of all steps of preprocessing is critical. Couple resources:
  * The [QAP project](http://preprocessed-connectomes-project.org/quality-assessment-protocol/) along with that [paper](https://www.ncbi.nlm.nih.gov/pubmed/29278774) for evaluation.
  * [visual protocol](https://www.zooniverse.org/projects/simexp/brain-match) for T1 registration, with an example [report](https://simexp.github.io/qc_cobre/index.html) from NIAK.
  * [QC in the UK biobank](https://www.sciencedirect.com/science/article/pii/S1053811917308613).
  * A bunch of different quantitative metrics in [MRIQC](https://www.biorxiv.org/content/early/2017/02/24/111294).

# Extracting derivative measures
  * the [CPAC pipeline](https://fcp-indi.github.io/) has (pretty much) everything.
  * the NIAK [connectome pipeline](http://niak.simexp-lab.org/pipe_connectome.html) generates, well, connectomes. And connectivity maps. See an example of report here.
  * you can also generate these maps on the fly, in a notebook, with [nilearn](https://nilearn.github.io/auto_examples/index.html#id68).
