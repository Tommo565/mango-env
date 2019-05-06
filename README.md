## mango-env

This repo has a set of resources to set up a GCP friendly linux environment on a windows machine.

### Ubuntu for Windows

1. [Download cmder](https://cmder.net/) Cmder is an enhanced terminal and I much prefer it to Powershell or the Ubuntu interface.
2. [Open Powershell and install the Windows subsystem for Linux.](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
3. [Download and install Ubuntu for Windows.](https://tutorials.ubuntu.com/tutorial/tutorial-ubuntu-on-windows#0)
4. [Set up Bash for Ubuntu in cmder.](https://gingter.org/2016/11/16/running-windows-10-ubuntu-bash-in-cmder/)

Note that you can access your Ubuntu files at `C:\Users\your-name\AppData\Local\Packages\CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc\` (or somewhere similar). Also when the terminal starts you can log in as a superuser (sudo) by executing `sudo -s`. This makes things easier.

Also note that Ubuntu should ship with git and Python2 installed already.

5. [Install Ananconda for Linux](https://www.digitalocean.com/community/tutorials/how-to-install-anaconda-on-ubuntu-18-04-quickstart) Whilst you could install Python3 and packages manually, Anaconda is a lot easier, and whilst the `conda` package manager isn't as good as `pip` a lot of the bugs around interoperability with `pip` have been removed. There is a list of all the packages that ship with Anaconda [here](https://docs.anaconda.com/anaconda/packages/py3.7_linux-64/).

6. Test that everything is working by running `conda --version`.
7. Test the package manager by running `conda install seaborn`.


## Docker
