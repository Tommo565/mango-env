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

12. [Install the GCP SDK for Ubuntu](https://cloud.google.com/sdk/docs/quickstart-debian-ubuntu). This allows you to interact with 




## Docker


## Jargon buster

`sudo`: Stands for 'super-user do' and is a way to run administrator commands in Linux. Note that you can do a lot of damage with sudo if you're not careful, so it's best to check thigns out before running any form of linux sudo command, especially if you're logged in with `sudo -s`

`apt`: stands for 'Advanced Packaging Tool' which basically means that it's the package manager for Ubuntu, similar to how `pip` is the package manager for Python. 

## Useful Commands

```bash
ls               # Lists the current directory
cd {NAME}        # Changes to the specified directory
cd ..            # Changes to the parent directory (aka up one level)
mkdir {NAME}     # Creates a new directory
sudo ...         # Executes the subsequent command as a super user
sudo -s          # Logs you in as sudo to your Ubuntu installation
apt-get update   # Downloads the package lists and updates them to the newest versions
```
