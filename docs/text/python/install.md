## Clean Installation
This tutorial will install Miniconda3 onto your computer. You may follow different instructions for installing python if you choose. If you already have Python3 installed on your computer, you can skip this tutorial. 

For Mac:
```zsh
#download the latest 64-bit version
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh

#install in batch mode
bash Miniconda3-latest-MacOSX-x86_64.sh -b 
```

For Linux:
```bash
#install the latest 64-bit version
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

# install in batch mode
bash Miniconda3-latest-Linux-x86_64.sh -b 
```

For Windows:
```bash
#install the latest 64-bit version
curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe

# install in batch mode
start /wait "" Miniconda3-latest-Windows-x86_64.exe /InstallationType=JustMe /RegisterPython=0 /S /D=%UserProfile%\Miniconda3
```

### Add conda to your path
**For Mac and Linux only**

If this is your first time installing, make sure you run this code to add conda to your path:
```~/miniconda3/condabin/conda init```

Then **restart your terminal** for changes to take effect. 


### Troubleshooting

*For Mac only*. If your install was successul, but your computer is still unable to find `conda` you may have to add it to your path manually. Find the `.zprofile` and/or `.zshrc` file (your computer may have one or both) by navigating to your `/home/username` directory and using the command:
```
ls -a
```

Open the file(s) and paste the following code in a new line the end any existing content. (Remember to replace the `username` part with your own username)
```
export PATH="/home/username/miniconda/bin:$PATH"
```

Save and **restart your terminal** for changes to take effect. 


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
# clone the shadie repo to get git development version
git clone https://github.com/elissasoroj/shadie

# cd into the cloned local repo folder
cd shadie/

# do local pip install (-e) with --no-deps 
pip install -e . --no-deps
```