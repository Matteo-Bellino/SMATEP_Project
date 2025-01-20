# Exercises for the Statistical Methods and Analysis Techniques.

The exercise part of the class is contained in this folder. During the exercise classes, you will write code in _Python_ using a web-application called _jupyter notebook_ and upload your solutions to the course _gitlab_. Each week a new set of exercises will be presented and included in this folder. The students will upload their solutions in the same folder. Please named your own solutions as `Exercise1/Exercise1_LASTNAME.ipynb`. The teaching assistants will provide some feedback to the exercise the next class, if any. The solutions of each exercise will be uploaded the next class.

## Tools for the class

In this exercise class, we will use the following tools:
 * [Python](https://www.python.org/): a powerful programming language for data analysis.
 * [Anaconda](https://www.anaconda.com/): This is a powerful tool to install python libraries.
 * [Miniconda](https://docs.conda.io/en/latest/miniconda.html): This is a smaller version of Anaconda. For this class most likely the libraries in miniconda are sufficient enough for the exercises, but if you want the complete set of python libraries you can use anaconda.
 * [Jupyter notebooks](https://jupyter.org/): it is web-application and user-friendly tool to create code and include plots or comments. 
 * [gitlab](https://about.gitlab.com/): Git is a tool for versioning control code. We will use one of its variants: gitlab.
 * Terminals: even though we will use jupyter notebooks for coding, basic knowledge on terminals in linux is required.

## Set up Conda

To be able to use jupyter notebook, we would like you to set up the needed environment using Anaconda program. If you have never programmed or installed any packages within a bash shell or terminal, we recommend to follow the instructions for Anaconda installation below. For students, already familiar with programming in a shell terminal, we suggest to only install miniconda (follow Miniconda installation bellow). It takes much less memory and is sufficient for everything we will do during the course.

### Only for Windows users

If you have Windows 10, you have already access to a terminal. 
If you dont have Windows 10, you need to install a _client_ to access a terminal. There are a couple of these clients in the market, and one of them is [PuTTY](https://www.putty.org/). To install it, please follow the instructions from that website.

Unfortunately most of the teaching asistants do not use Windows but if you need support, please send us an email and we will try to help you.


### Anaconda installation

Please follow the instructions on how to install anaconda for your operating system from [here](https://docs.anaconda.com/anaconda/install/). Pick the **python 3** version corresponding to the operating system on your laptop, and follow the installation instructions on the web-site. Beware, this installation will need approximately 8 Gb.

To test if the program is correctly installed, you can follow the instructions below to run the program:
 * For Windows: Programs -> Anaconda navigator -> jupyter notebook -> new -> python3
 * For Linux: from the terminal type _anaconda-navigator_ -> jupyter notebook -> new -> python3
 * For Mac OS: _launch anaconda-navigator_  -> jupyter notebook -> new -> python

To test your setup, in the cell that appear when you create a new notebook, please type/copy:
```
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
import scipy as sp
```
and press `Shift+Enter`.
    
If **no output** is printed, your setup works. If some error is shown, it may be due to some missing package. Refer to [this website](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-pkgs.html) for installing the missing package.
If you have no clue about what to do to solve an installation error, try to google the error or send us an email. Meanwhile we will have a look on our side and go back to you as soon as possible.
    
In any case, **don't panic**, we will go through any remaining installation problems on the first exercise class.

### Miniconda installation

Remember that you do not need to have anaconda **and** miniconda at the same time. Install miniconda if you want a lighter version of anaconda. To install it please follow the instructions for your operating system from [here](https://docs.conda.io/projects/conda/en/latest/user-guide/install/).  When the installation is finished, close and open a new terminal window.
(If you are a Windows user, please look at the previous instructions on how to install a terminal)

### Create an Environment

The nicest feature of conda is the possibility to create separate and indipentend environments. This is useful especially for the final projects, during which you might want to install some fancy libraries without screwing up the environment that you used for the exercises. One way to create an environment consists in using an environment YAML file in which we specify the name of the environment and the packages we want to include. 

You can see that a file called ```environment.yml``` is already present at the root level of this repo. After cloning this repo (see last paragraph of this guide), in order to create the environment run:
```
conda env create -f environment.yml
```
Note that this command will create an environment with the most recent version of Python3. If you want to pick a specific/less recent version you can add another item to the ```dependencies``` list, e.g. ```python=3.8```.
Once your environment is created, you need to _ACTIVATE_ this environment, as:
```
conda activate STAMET-FS25
```

To test your setup, type `jupyter notebook` in your terminal. You will get a new tab opened in your browser. On the right top corner press `New` -> `Notebook (python 3)`. In the cell that appears when you create a new notebook, please type/copy :
To test your setup, in the cell that appear when you create a new notebook, please type/copy:
```
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
import scipy as sp
```
and press `Shift+Enter`.

If **no output** is printed, your setup works. If some error is shown, it may be due to some missing package. Refer to [this website](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-pkgs.html) for installing the missing package. 
If you have no clue about what to do to solve an installation error, try to google the error or send us an email. Meanwhile we will have a look on our side and go back to you as soon as possible.
    
In any case, **don't panic**, we will go through any remaining installation problems on the first exercise class.

### Getting fancy with mamba

You might have noticed that conda is not exactly fast. If you don't want to wait much every time you create a new environment you can use [mamba](https://github.com/mamba-org/mamba).
To install mamba follow the instructions reported in the [documentation](https://mamba.readthedocs.io/en/latest/installation.html).

From now on, every time you run one of the commands mentioned above, you can change the word ```conda``` with ```mamba``` and it will be much faster!

## Git: clone the repo and get started

Git is the tool that we use for managing the code in our repository. A very simple tutorial on how to install it in your operating system and the basic commands needed can be found [in this link](https://rogerdudler.github.io/git-guide/).

_Remember that you will use git to download the class repository to your computer, and to upload your exercises each class._

To upload files to our [central repository](https://gitlab.ethz.ch/mdonega/STAMET_FS21), you need to add your key to your gitlab account _one time only_. Some instructions can be found [in this website](https://gitlab.ethz.ch/profile/keys). 

Quick example:

1. Before reading how to *generate* an ssh key, you probably want to check if you already have one. They are usually located at ```~/.ssh```. So, if when you run 
```
ls ~/.ssh
```
you see an output that includes ```id_rsa``` and ```id_rsa.pub```, you don't need to generate a new key and you can directly skip to step 3, where you will learn how to upload it in gitlab;

2. In your terminal type:
```
ssh-keygen -C 'your_email@ethz.ch'
```
the outcome will look similar than this:
```
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/Nadezda/.ssh/id_rsa): /Users/Nadezda/.ssh/id_rsa
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /Users/Nadezda/.ssh/id_rsa.
Your public key has been saved in /Users/Nadezda/.ssh/id_rsa.pub.
```

3. After the previous step, a key was created in your computer. You need to copy that key to your gitlab account [in this website](https://gitlab.ethz.ch/profile/keys). To print out your key, using the same example:
```
cat /Users/Nadezda/.ssh/id_rsa.pub
```
this command `cat` only prints out your key which look like:
```
ssh-rsa AAAAB3NzaC1yc2EAfdsjfkhakdjsfhkalfaskafcqJG6Gw0Vhlz8xjSoVOGB2XDq+bHeYGj5MMyjSfF0V7tsxzJhf+gUqmM42zL4qPhEqEgGeLh7qrARWtoiKQ==your_email@ethz.ch
```
copy this line and add it as keys to your gitlab profile.

Note: in case you decide NOT to use the default name for the key (i.e. ```id_rsa.pub```, which is kept automatically if you press ENTER in the process) you have to add the key to the SSH agent. Follow [these instructions](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent) if this is the case.

After your key is properly included in your profile you can clone the repository:
```
git clone git@gitlab.ethz.ch:mdonega/STAMET_FS25.git
cd STATMET_FS25/
git checkout -t origin/STAMET_FS25
```
or, in just one step:
```
git clone -b STAMET_FS25 git@gitlab.ethz.ch:mdonega/STAMET_FS25.git
cd STAMET_FS25
```
First time and every Tuesday morning get the updates:
```
git pull origin STAMET_FS25
```
To push your project to the repository:
```
git add myNotebook.ipynb
git commit -m "my commit"
git push origin STAMET_FS25
```
To check the status of your repository:
```
git status
```
If you accidentaly made changes to files you did not want to change, you can retrive the original version by doing the following:
```
git checkout -- file.py
```

## Useful tutorials.

In addition, the following is a list of useful self-explanatory tutorials for the basic tools that you will need for the exercise class.:
 * [git - the simple guide](https://rogerdudler.github.io/git-guide/): the basics about git.
 * [Version Control with Git](https://swcarpentry.github.io/git-novice/): a more comprehensive git tutorial.
 * [Git Handbook](https://guides.github.com/introduction/git-handbook/): the official git handbook
 * [Plotting and Programming in Python](https://alistairwalsh.github.io/python-novice-gapminder/): quick and complete tutorial with useful examples. It also includes examples about mathplotlib.
 * [Python for data analysis](https://education.molssi.org/python-data-analysis/index.html): quick introduction of numpy, pandas and scipy.
 * [Jupyter Notebook: An Introduction](https://realpython.com/jupyter-notebook-introduction/): a simple introduction.


Disclaimer: there are many of these free tutorials online. Here is just a list gathered by the teaching assistants that they find them useful. 
