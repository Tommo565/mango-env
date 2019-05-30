## mango-env

This repo has a set of resources to set up a GCP friendly linux environment on a Windows machine.

GCP uses Linux, specifically Ubuntu, as their OS for their products, so it makes sense to emulate that in your local environment so that code is transferrable from your local machine to the GCP platform.

### Creating and Setting up your Ubuntu Environment

1. [Download cmder](https://cmder.net/) cmder is an enhanced Windows terminal and has a lot of functionality that the Ubuntu terminal doesn't and it generally makes everything easier.
2. [Open Powershell and install the Windows subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10).
3. [Download and install Ubuntu for Windows](https://tutorials.ubuntu.com/tutorial/tutorial-ubuntu-on-windows#0).
4. Start Ubuntu for Windows in order to finish the installation and set it up. Note that you can access your Ubuntu files at `C:\Users\your-name\AppData\Local\Packages\CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc\` (or somewhere similar). Also note that Ubuntu should ship with git installed already.
5. [Set up Bash for Ubuntu in cmder](https://gingter.org/2016/11/16/running-windows-10-ubuntu-bash-in-cmder/). Note that in addition to this guide, you'll also have to:
    * Set the Start directory by clicking the Start Dir... button and copy and pasting the home directory of your linux installation above.
    * Go to Options (Burger menu) > Settings and then on the 'General' settings page select the task you created in the 'Choose your startup task...' dropdown menu.
6. Give yourself sudo permissions by executing `sudo usermod -aG sudo {YOUR USERNAME}`
7. Making sure that you're in your named home directory in Linux (e.g. the directory that's named with your username), give yourself folder permissions by running:
```bash
chown -R {USERNAME} ./
chmod -R u+rX ./
```

The first command makes the user own the directory. The second command gives them full read and access permissions. The r gives read permission, the X gives 'execute' permission to directories, and not files.

Note that if you're happy using the Ubuntu kernel, you needn't necessarily install cmder.

### Installing Anaconda3

8. [Install Ananconda for Linux](https://www.digitalocean.com/community/tutorials/how-to-install-anaconda-on-ubuntu-18-04-quickstart) Whilst you could install Python3 and packages manually, Anaconda is a lot easier, and whilst the `conda` package manager isn't as good as `pip` a lot of the bugs around interoperability with `pip` have been removed. There is a list of all the packages that ship with Anaconda [here](https://docs.anaconda.com/anaconda/packages/py3.7_linux-64/).

9. You might also need to initialise Anaconda. You can do this by running:
```bash
eval "$(/home/{YOUR_USER_NAME}/anaconda3/bin/conda shell.bash hook)"
conda init
```
And then restart cmder for the changes to take effect.

10. Test that everything is working by running `conda --version`.
11. Test the package manager by running `conda install seaborn`. This should also update Anaconda.
1. You can start Jupyter by executing `jupyter notebook`. This should start the Notebook Server. You'll probably have to copy and paste the localhost link into your browser however.

**NOTE:** When installing new packages, you should try `conda` first:
```bash
conda install {PACKAGE_NAME}
```

If the package isn't available, then try `conda-forge`, which is a community led collection of recipes, build infrastructure and distributions for the conda package manager:
```bash
conda install -c conda-forge {PACKAGE_NAME}
```

If the package you want isn't on conda-forge, then use pip3:
```bash
pip3 install {PACKAGE_NAME}
```

### Setting up GCP

13. [Create a GCP Account](https://cloud.google.com/) Be sure to also sign up for the $300 free credit.

11. [Install the pre-requisites software for GCP](https://cloud.google.com/python/setup) Be sure to select the Linux tab to get the right instructions. This guide contains the pre-requisites (e.g. Python 2, 3 & pip). It will detect your Anaconda Python3 installation and just download and install Python2 (which is required by GCP).

12. [Install the GCP SDK for Ubuntu & Initialise your GCP Account](https://cloud.google.com/sdk/docs/quickstart-debian-ubuntu). This allows you to interact with the GCP platform from the Ubuntu command line. Note that your installation may hang (mine did) but you can Ctrl+C to exit. There is a list of useful gcloud commands [here](https://gist.github.com/pydevops/cffbd3c694d599c6ca18342d3625af97)

13. Install the following packages on GCP:
```
conda install -c conda-forge google-api-python-client
conda install -c conda-forge google-cloud-sdk
conda install -c conda-forge google-cloud-storage
conda install -c conda-forge google-cloud-bigquery
pip2 install google-cloud-sdk
``` 


Note that this will take a while to do as it downgrades some of your packages to ensure compatibility with GCP. This is fine.

**NOTE:** There are many different ways to interact with GCP (e.g. command line, GCP website, Python) as there are a TON of tutorials, references, guides etc. Generally I think it's best to try and interact with GCP through the command line or Python if it's part of production code. However there are some things that you can't do with the command line, so you will have to use the web interface for these tasks.

## IntelliJ

IntelliJ is an IDE (Integrated Development Environment) which has excellent support from GCP. It's created by JetBrains who also create other IDEs such as PyCharm and WebStorm. 

### Why IntelliJ?

IntelliJ is one of two major IDEs well supported by GCP, the other being MS Visual Studio. Visual Studio is great in it's own right, but is set up primarily to be used wih Azure. Additionally the GCP / IntelliJ integration is better developed than Visual Studio, which at the time of writing is still in Beta.

You might be also wondering why I'm reccomending IntelliJ over PyCharm, and that's a great question. In short IntelliJ is far more extensible than PyCharm - some of the plugins that are developed are only available for IntelliJ, or are developed for IntelliJ first.

### Setting Up IntelliJ

1. [Download and install IntelliJ Community edition](https://www.jetbrains.com/idea/download/) Be sure to use the .exe file if possible.
2. Run the downloaded .exe file.
3. For the first **Installation Options** pop up, check all the boxes.
4. Install the to default JetBrains folder. Note that you'll need to restart your computer after the installation has completed.
5. Once you've installed it, there are a good set of [tutorials available from the JetBrains wbsite](https://www.jetbrains.com/idea/documentation/) to help you figure out how to use it and set it up. It can be a bit of a culture shock if coming from more simple text editors and Jupyter / RStudio but it does make a lot of things easier once you get the hang of it.
6. You can also install plugins for IntelliJ - these are handy ways to extend the functionality, help perform certain tasks or just make the interface look nicer! You can access the Plugins settings to browse / install / remove plugins by selecting File > Settings > Plugins or Ctrl + Alt + S to bring up the settings menu and then selecting plugins. Some plugins you might want to consider are as follows:

* [Python Community Edition](https://plugins.jetbrains.com/plugin/7322-python-community-edition) PLugin to turn IntelliJ into a Python IDE. Install this first!
* [Markdown Navigator](https://plugins.jetbrains.com/plugin/7896-markdown-navigator) Linting + a preview pane for Markdown documents.
* [GitToolBox](https://plugins.jetbrains.com/plugin/7499-gittoolbox) Some Helper tools for git and version control.
* [Cloud Code](https://plugins.jetbrains.com/plugin/8079-cloud-code) Tools for managing GCP. I expect this to be added to as time goes on.
* [Material Theme UI](https://plugins.jetbrains.com/plugin/8006-material-theme-ui) Tools and options for changing your UI.

TODO: I'm still figuring out IntelliJ myself but hope to add to this section of the guide shortly.

## Jargon buster

`sudo`: stands for 'super-user do' and is a way to run administrator commands in Linux. Note that you can do a lot of damage with sudo if you're not careful, so it's best to check things out before running any form of linux sudo command, especially if you're logged in with `sudo -s`

`apt`: stands for 'Advanced Packaging Tool' which basically means that it's the package manager for Ubuntu, similar to how `pip` is the package manager for Python.

`ssh`: is a cryptographic network protocol for operating network services securely over an unsecured network. Typical applications include remote command-line login and remote command execution, but any network service can be secured with SSH. 

## Useful Commands

```bash

# General Commands

ls                   # Lists the current directory
cd {NAME}            # Changes to the specified directory
cd ..                # Changes to the parent directory (aka up one level)
mkdir {NAME}         # Creates a new directory
rm {FILE_NAME}       # Delete a file
rm -r {DIR_NAME}     # Delete a directory
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

* [Conda Forge](https://conda-forge.org/)
* [GCloud Cheet Sheet](https://gist.github.com/pydevops/cffbd3c694d599c6ca18342d3625af97)
* [List of GCP Resources](https://github.com/gregsramblings/google-cloud-4-words)
* [GCP GCloud API Reference](https://cloud.google.com/sdk/gcloud/reference/)
* [GCP Python Client Libraries](https://cloud.google.com/python/docs/reference/)
* [GCP Python SDK Github](https://github.com/googleapis/google-cloud-python)
* [GCP Python API reference](https://cloud.google.com/python/docs/reference/)
* [Scripting gcloud commands](https://cloud.google.com/sdk/docs/scripting-gcloud)
* [Google Cloud for IntelliJ](https://cloud.google.com/code/docs/intellij/)
* [Setting up bash on IntelliJ](https://intellij-support.jetbrains.com/hc/en-us/community/posts/207698489-How-can-you-use-new-Bash-on-Ubuntu-on-Windows-terminal-in-Webstorm-)
