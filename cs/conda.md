
# Conda Cheat Sheet 

![conda](https://user-images.githubusercontent.com/62952163/198683845-f5706e8b-182e-407d-88fd-85eb97f6ad45.png)

# Table of Contents
1. [What is Conda ? ](#what)
2. [Installation of Miniconda for Linux](#installation)
3. [Using Conda](#usage)
   - [Creating a new environment from scratch ?](#newenv)
   - [Creating an environment from a yml](#yml)
   - [Using the environment in a .ipynb](#nb)
4. [Updating Conda](#update)
5. [Uninstalling Conda](#uninstall)
6. [References](#references)


## 1. What is Conda ? <a name="what"></a>
Conda : package, depedency and environment management for **Python** (works also for R, Ruby, Lua, Scala, Java, JS, ..)

> If you need a package that requires a different version of Python, you do not need to switch to a different environment manager, because conda is also an environment manager. With just a few commands, you can set up a totally separate environment to run that different version of Python, while continuing to run your usual version of Python in your normal environment.
>
> <cite>[conda website](https://docs.conda.io/en/latest/miniconda.html)</cite>

### Miniconda ? Conda ? 
**Miniconda** is a free installer for Conda. 

> It is a small, bootstrap version of Anaconda that includes only conda.
>
> <cite>[conda website](https://docs.conda.io/en/latest/miniconda.html)<cite>

## 2. Installation of Miniconda for Linux <a name="installation"></a>

-  Download the installer and run it 
```{bash}
 wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
 bash Miniconda3-latest-Linux-x86_64.sh
```
- Follow the prompts on the installer screen. 
- To make the changes take effect, close and re-open your terminal window. 
- Make sure the installation is correct 
```{bash}
conda list 
```
The list of installed packages shows on screen, if the **conda** has been installed properly.

- If conda can't be found, add to path
```{bash}
export PATH="/home/usr/miniconda/bin:$PATH"
```
Make sure to **replace** /home/username/miniconda with your actual path.

- Disabling automatic base activation 
If you want to disable the base activation, to run your initial *python* for instance. 
```{bash}
conda config --set auto_activate_base false
```

## 3. Using Conda <a name="usage"></a>

### Creating a new environment <a name="newenv"></a>
#### Which Python ? 
- Create the directory where you want ot store your project.
```{bash}
mkdir example 
cd example
```
- Create and activate the env
```{bash}
conda create --name cobra  python=3.9
conda activate cobra
```
- Verify the *cobra* environment has been added and is active
```{bash}
conda info --envs
```
The active environment is also displayed in front of the prompt 
```{bash}
(cobra) $
```

- Verify which version of Python is running
```{bash}
python --version
```
#### Add Packages ? 
- Search if the package which not installed is available from *Anaconda*
```bash{bash}
conda search scipy
```
- Install it in the current environment
```{bash}
conda install scipy
```

- Check the package has been added
```{bash}
conda list
```
### Using the environment from a notebook <a name="nb"></a>
  
 ```{bash}
conda activate env_name
conda install ipykernel
python -m ipykernel install --user --name=env_name
 ```
   
 When using jupyter lab :  restart jupyter lab.
 
#### Using pip in the environment
```{bash}
conda install -n myenv pip
conda activate myenv
pip <pip_subcommand>
```

Always try to install the packages with conda first.
Pip should be run with : `--upgrade-strategy only-if-needed` (the default).

### Export environment 
```{bash}
conda env export > environment.yml
```

### Deactivate the environment
```{bash}
conda deactivate
```
### Creating an environment from an existing yml <a name="yml"></a>
```{bash}
conda env create -f environment.yml
```

## 4. Updating Conda <a name="update"></a>
```{bash}
conda update conda
```

## 5. Uninstalling Conda <a name="uninstall"></a>
```{bash}
conda init --reverse bash
rm -rf ~/miniconda3
rm -rf ~/.conda
if [ -f ~/.condarc ] && rm ~/.condarc
```


## 6. References <a name="references"></a>
1. [Conda, getting started tutorial](https://conda.io/projects/conda/en/latest/user-guide/getting-started.html#managing-python)
2. [Using pip in an Environment](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#using-pip-in-an-environment)
