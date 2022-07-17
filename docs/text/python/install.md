## Clean Installation
This tutorial will install Miniconda3 onto your computer. You may follow different instructions for installing python if you choose. If you already have Python3 installed on your computer, you can skip this tutorial. 

For Mac:
```zsh
#download the latest 64-bit version
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh

#install in batch mode
bash Miniconda3-latest-MacOSX-x86_64 -b 
```

For Linux:
```bash
#install the latest 64-bit version
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```

```bash
# install in batch mode
bash Miniconda3-latest-Linux-x86_64 -b 
```


If this is your first time installing, make sure you run this code to add conda to your path:
`~/miniconda3/condabin/conda init`


## Create a Working Environment
It is best to create a working environment that is separate from your base environment, and install packages there. This will help you avoid dependency conflicts and manage Python versions in the future. 

```zsh
#This code creates the environment
conda create -n py38 Python=3.8

#This code sets the working environment
conda activate py38
```
Note, this code creates a Python 3.8 environment, which is not the latest version of Python. 

## Installing Packages from channels
Channels are a collection of recipes, build infrastructure, and distributions for python packages. There are many different channels, but Conda-forge is the most extensive and tends to be kept up-to-date. It is a good idea to install packages from the same channel as much as possible to help reduce conflicts. You can choose to set your default channel with the following code: 
```bash
conda config --add channels conda-forge
conda config --set channel_priority true
```

Now, when you use the `conda` command to install, it will automatically install from conda-forge first:
`conda install shadie`

## Installing Local Packages
When you install programs by cloning repositories on GitHub, you will use a local installation with `pip`.

To avoid installing dependencies with pip, you can use the option `--no-deps` - however, you will then need to make sure to install any dependencies separetly with Conda-forge. 

```zsh
# clone the ipyrad repo to get git development version
git clone [repo URL]

# cd into the cloned local repo folder
cd ipyrad/

# do local pip install (-e) with --no-deps 
pip install -e . --no-deps
```