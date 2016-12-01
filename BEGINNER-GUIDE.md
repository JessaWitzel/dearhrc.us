# Beginners Readme for Contributing

Since our backend is going to be programmed in Python, we’ve chosen to use a
Pyramid Program as our framework. We chose to use Tox, because it makes managing
the virtual environment easier. We’re using a virtual environment to keep the
project dependencies from polluting the rest of our system. We chose to use Juju
because it makes managing and scaling easier. We are using Virtual Box for Juju
so we can deploy locally for testing. Instead of having to deploy to the public
cloud, we can deploy to a mini virtual cloud. (LXD)

In this document, commands that are to be entered into the terminal will be preceded by a dollar sign. When entering the command, exclude the dollar sign. 

________________________________________________________________

About Pyramid: http://www.pylonsproject.org/projects/pyramid/about

Pyramid documentation:
http://docs.pylonsproject.org/en/latest/docs/pyramid.html#pyramid-documentation

________________________________________________________________

Steps to take BEFORE installing Pyramid are contained here:
http://docs.pylonsproject.org/projects/pyramid/en/latest/narr/install.html#installing-chapter

________________________________________________________________

## Detailed steps and links for Mac OSX users:

**Install Homebrew:**
Info and instructions here: http://brew.sh/

Use Brew to install Python 3.4 or greater

    $ brew install python3

**Install Tox to run the virtual environment**

    $ pip3 install tox

Pip3 install means to install a python library. Tox is the actual python library.
Tox is a test environment manager - it manages the virtual environment for
running the project’s test and invokes the test runner, which for us is py.test.

**Create requirements.txt and tox.ini in the project directory (repo)**
Example tox.ini file: https://github.com/juju-solutions/matrix/blob/master/tox.ini

**Run Tox to create the virtual environment and install Pyramid**

    $ tox

When Tox installs Pyramid into the virtual environment, it adds the Python
Pyramid libraries as well as the Pyramid command line tools “pcreate” and “pserve”.

**Bootstrap the pyramid project using the alchemy scaffold:**
http://docs.pylonsproject.org/projects/pyramid/en/latest/narr/project.html#scaffolds-included-with-pyramid

**Create the Pyramid App using the “alchemy” scaffold:**

    $ .tox/py35/bin/pcreate -s alchemy dearhrc-backend

**Set up Virtual Box for running Ubuntu in OSX:**
Install and run Virtual Box: https://www.virtualbox.org/wiki/Downloads

**Install 64 bit desktop image ISO:**
Instructions: https://henricasanova.github.io/VirtualBoxUbuntuHowTo.html
https://www.ubuntu.com/download During configuration, accept all defaults except
for the image. For the image browse to the ISO file in downloads.

**Run and set up Virtual Machine**
Once the virtual machine is created, double click on it to run it. This will start the Ubuntu installation. Accept all defaults. Once Ubuntu is installed and running, open a terminal by pressing and releasing the command key and typing "terminal".

**Install Juju:**

    $ sudo apt install juju
    $ newgrp lxd
    $ sudo lxd init

**Bootstrap Juju to deploy Wordpress:**

    $ juju bootstrap lxd lxd

**Use Juju to deploy Wordpress:**

    $ juju deploy wordpress

**Use Juju to deploy MySQL:**

    $ juju deploy mysql

**Relate Wordpress and MySQL:**

    $ juju add-relation wordpress mysql
