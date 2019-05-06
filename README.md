## mango-env

This repo has a set of resources to set up a GCP friendly linux environment on a windows machine.

## Ubuntu for Windows

## Setting up your Environment

1. [Download cmder](https://cmder.net/) Cmder is an enhanced terminal and I much prefer it to Powershell or the Ubuntu interface.
2. [Open Powershell and install the Windows subsystem for Linux.](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
3. [Download and install Ubuntu for Windows.](https://tutorials.ubuntu.com/tutorial/tutorial-ubuntu-on-windows#0)
4. [Set up Bash for Ubuntu in cmder.](https://gingter.org/2016/11/16/running-windows-10-ubuntu-bash-in-cmder/)

Note that you can access your Ubuntu files at `C:\Users\your-name\AppData\Local\Packages\CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc\` (or somewhere similar). Also when the terminal starts you can log in as a superuser (sudo) by executing `sudo -s`. This makes things easier.

Also note that Ubuntu should ship with git installed already.

5. [Install Ananconda for Linux](https://www.digitalocean.com/community/tutorials/how-to-install-anaconda-on-ubuntu-18-04-quickstart) Whilst you could install Python3 and packages manually, Anaconda is a lot easier, and whilst the `conda` package manager isn't as good as `pip` a lot of the bugs around interoperability with `pip` have been removed. There is a list of all the packages that ship with Anaconda [here](https://docs.anaconda.com/anaconda/packages/py3.7_linux-64/).

6. You might also need to initialise Anaconda. You can do this by running:
```bash
eval "$(/home/{YOUR_USER_NAME}/anaconda3/bin/conda shell.bash hook)"
conda init
```

7. Test that everything is working by running `conda --version`.
8. Test the package manager by running `conda install seaborn`.
9. You can start Jupyter by executing `jupyter notebook --allow-root`. This should start the Notebook Server. You'll probably have to copy and paste the localhost link into your browser however.

**NOTE:** For all package installations try with `conda` first and if the package is unavailable, try with `pip3`. Conda does optimise some packages for speed (in particular `scikit-learn` and `tensorflow`) and this is also (probably) a good way to avoid pip and conda conflicts.

10. [Create a GCP Account](https://cloud.google.com/) Be sure to also sign up for the $300 free credit.

11. [Install the pre-requisites software for GCP](https://cloud.google.com/python/setup) Be sure to select the Linux tab to get the right instructions. This guide contains the pre-requisites (e.g. Python 2, 3 & pip). It will detect your Anaconda Python3 installation and just download and install Python2 (which is required by GCP).

12. [Install the GCP SDK for Ubuntu & Initialise your GCP Account](https://cloud.google.com/sdk/docs/quickstart-debian-ubuntu). This allows you to interact with the GCP platform from the Ubuntu command line. Note that your installation may hang (mine did) but you can Ctrl+C to exit. There is a list of useful gcloud commands [here](https://gist.github.com/pydevops/cffbd3c694d599c6ca18342d3625af97)

13. Install the GCP SDK (aka google-cloud python package) for Python by executing `pip3 install google-cloud`. There is a huge list of code based resources [here](https://github.com/googleapis/google-cloud-python).

**NOTE:** There are many different ways to interact with GCP (e.g. command line, GCP website, Python) as there are a TON of tutorials, references, guides etc. Generally I think it's best to try and interact with GCP either through the command line or Python before trying the web interface since this aids repeatablility and once you get the hang of it, it is a lot quicker. However there are some things that you can't do with the command line, so you will have to use the web interface for these tasks.

## Setting up IntelliJ

IntelliJ is an IDE (Integrated Development Environment)


## Jargon buster

`sudo`: stands for 'super-user do' and is a way to run administrator commands in Linux. Note that you can do a lot of damage with sudo if you're not careful, so it's best to check thigns out before running any form of linux sudo command, especially if you're logged in with `sudo -s`

`apt`: stands for 'Advanced Packaging Tool' which basically means that it's the package manager for Ubuntu, similar to how `pip` is the package manager for Python.

`ssh`: is a cryptographic network protocol for operating network services securely over an unsecured network. Typical applications include remote command-line login and remote command execution, but any network service can be secured with SSH. 

## Useful Commands

```bash

# General Commands

ls                   # Lists the current directory
cd {NAME}            # Changes to the specified directory
cd ..                # Changes to the parent directory (aka up one level)
mkdir {NAME}         # Creates a new directory
sudo ...             # Executes the subsequent command as a super user
sudo -s              # Logs you in as sudo to your Ubuntu installation
apt-get update       # Updates your local ubuntu package list to the newest version
conda install {NAME} # Install a package using conda
pip3 install {NAME}  # Install a package using pip

# Gcloud Commands

gcloud config set project {NAME} # Set the default GCP project
gcloud auth login                # Login or switch user

```

## Further Resources

* [GCloud Cheet Sheet](https://gist.github.com/pydevops/cffbd3c694d599c6ca18342d3625af97)
* [List of GCP Resources](https://github.com/gregsramblings/google-cloud-4-words)
* [GCP GCloud API Reference](https://cloud.google.com/sdk/gcloud/reference/)
* [GCP Python SDK Github](https://github.com/googleapis/google-cloud-python)
* [GCP Python API reference](https://cloud.google.com/python/docs/reference/)
