


If you haven't done so, download the [Anaconda python distribution](https://www.anaconda.com/download/) and install it following the [instructions](https://conda.io/docs/user-guide/install/index.html#regular-installation).
## Install Jupyter notebook in a new conda environment
1. Open a new terminal
2. [Create a new conda environment](https://conda.io/docs/user-guide/tasks/manage-environments.html#creating-an-environment-with-commands) for jupyter notebook: `conda create --name jpserver`
3. [Check the available conda environments](https://conda.io/docs/user-guide/tasks/manage-environments.html#viewing-a-list-of-your-environments): `conda env list`. You should see the new `jpserver` environment in the list.
3. [Activate the new environment](https://conda.io/docs/user-guide/tasks/manage-environments.html#activating-an-environment) `source activate jpserver`
4. This is an empty conda environment, with nothing in it: `conda list --name jpserver`. We need to install python first: `conda install --name jpserver python`
4. Now we can [install the jupyter packages](https://conda.io/docs/user-guide/tasks/manage-pkgs.html#installing-packages) in this environment: `conda install --name jpserver jupyter jupyterlab`
5. Move to your home directory or some other directory that you would like the server to have access to: `cd ~/`
5. Start the jupyter lab server `jupyter lab`

This should open a new browser window with the jupyter lab layout.


For problems with conda, consult the [conda cheat sheet](https://conda.io/docs/_downloads/conda-cheatsheet.pdf).

## Create a conda environment for your project
If you are wondering why virtual environments (like conda) are useful to keep things from breaking in unexpected ways, [have a look at this](https://virtualenv.pypa.io/en/stable/).
1. Create a new conda environment for your current project (e.g. `brainhack`) but this time request that python is installed directly: `conda create --name brainhack python`. You can confirm that python was in fact installed (with some additional tools) by running `conda list --name brainhack`
2. Now install `ipykernel` so we can make jupyter aware of your new environment: `conda install --name brainhack ipykernel`
3. Activate the environment with `source activate brainhack`
4. [Register your new environment with jupyter](https://ipython.readthedocs.io/en/latest/install/kernel_install.html#kernels-for-different-environments): `python -m ipykernel install --user --name brainhack --display-name "python brainhack"`
5. Deactivate your environment: `source deactivate` and switch over to jupyter `source activate jpserver`
6. [Run the jupyter lab server](http://jupyterlab.readthedocs.io/en/latest/getting_started/starting.html): `jupyter lab`

You should now see an additional kernel available in your [jupyter lab home page](http://jupyterlab.readthedocs.io/en/latest/user/interface.html).

## Install packages in your project environment
As a general rule, [don't install packages from inside the jupyter notebook](https://jakevdp.github.io/blog/2017/12/05/installing-python-packages-from-jupyter/).

You may find the standard python to be lacking some key libraries you like. Let's install them.
1. Open a new terminal
2. Ask conda to install the packages (e.g. `numpy` and `matplotlib`): `conda install --name brainhack numpy matplotlib`.
3. Go to your jupyter lab website that is running in the `jpserver` environment and [start a new notebook](http://jupyterlab.readthedocs.io/en/latest/user/notebook.html) with the `brainhack` kernel.
4. Confirm that you can access the newly installed packages by running `import numpy as np` and executing the cell (`Shift + Enter`). If you don't get an error message you are good to go

## Install packages that are not available through conda
This works well for big python packages that are available directly from conda. But some of the more neuroscience specific packages are not directly available (e.g. `nilearn`, `nibabel`). You have two options here:
1. [See if the package is available from a conda channel](https://conda.io/docs/user-guide/tasks/manage-pkgs.html#installing-packages-from-anaconda-org). These channels are additional repositories maintained by community members. I don't know how reliable they are.
1. Install them directly from the [Python Package Index](https://conda.io/docs/user-guide/tasks/manage-pkgs.html#installing-non-conda-packages). The Python Package Index or pypi is a central hosting platform for python packages. Most packages are available from there. You can [install them using `pip`.](https://pip.pypa.io/en/stable/user_guide/#installing-packages).
    - When you use pip, you need to first activate your environment: `source activate brainhack`
    - `pip install nilearn nibabel`

__Sidenote__: It is (almost always) necessary to activate your conda environment before you can run code using that environment. The conda commands used above always default to the currently active conda environment. So you can technically run `conda install nilearn` without specifying the environment directly and it will install in the current environment. The reason I am using the `--name` flag in the examples above is because it is generally better to be explicit about what you plan to do.
