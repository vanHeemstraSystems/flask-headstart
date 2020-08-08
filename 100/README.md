.. add breadcrumbs ..

# 100 Setup & Workflow

We use our Playground Server "Server - Flask" at LinuxAcademy, see https://app.linuxacademy.com/dashboard

## 101 Install Python 3.6+ and PIP

Check the installed version of Python

```
[cloud_user@wvanheemstra2c ~]$ python --version
Python 2.7.5
[cloud_user@wvanheemstra2c ~]$ python3 --version
-bash: python3: command not found
[cloud_user@wvanheemstra2c ~]$ 
```

Because the version Python 3.6+ is not yet installed, we have to install it.

Follow the instructions from [How to Install Python 3.6.4 on CentOS 7](https://www.rosehosting.com/blog/how-to-install-python-3-6-4-on-centos-7/)

```
[cloud_user@wvanheemstra2c ~]$ python3 --version
Python 3.6.8
```

To Code we will be using Visual Studio Code. First we need to open the Graphical Shell of our Linux CentOs7 Server and install the Google Chrome Browser, following these instructions at [How to Install Google Chrome Web Browser on CentOS 7](https://linuxize.com/post/how-to-install-google-chrome-web-browser-on-centos-7/).

Install Visual Studio Code using the Google Chrome Web Browser, by browsing to https://code.visualstudio.com/download
Follow the instructions on the webiste to download and install Visual Studio Code, see [How to Install RPM File on CentOs Linux](https://phoenixnap.com/kb/how-to-install-rpm-file-centos-linux).

NOTE: You have to shutdown and restart the Graphical Shell to see the Visual Studio Code icon under Applications > Programming.

Install Git on your CentOs 7 Server, following the instructions at [How to install Git on CentOs 7](https://linuxize.com/post/how-to-install-git-on-centos-7/)

Check if Git is installed, by asking for its version:

```
[cloud_user@wvanheemstra2c git]$ git --version
git version 2.22.0
```

In your terminal create a directory called "git' inside your home directory and clone this repository in there:

```
$home/cloud_user/ mkdir git
$home/cloud_user/ cd git
$home/cloud_user/git/ git clone https://github.com/vanHeemstraSystems/flask-headstart.git
```

In Visual Studio Code, set your Workspace Folder to the cloned repository "flask-headstart".

## 102 Install virtualenv

In Visual Studio Code, inside your Workspace Folder "flask-headstart" open a terminal and run the following instruction (for Python 3):

```
pip3 install virtualenv
```
To check the version of PIP (for Python 3) run:

```
[cloud_user@wvanheemstra2c flask-headstart]$ pip3 --version
pip 9.0.3 from /usr/lib/python3.6/site-packages (python 3.6)
```

## 103 Create our Project Directory

We are working in the Workspace folder, inside the cloned repsoitory "flask-headstart".

## 104 Create Virtual Environment

If the folder 'env' does not yet exist in the root directory, in the terminal in Visual Studio Code, inside the repository root directory, type the following to create a virtual environment (named 'env' which is a convention):

```
[cloud_user@wvanheemstra2c flask-headstart]$ virtualenv env
```

A new folder will have been created, called 'env", in the root directory of your repository:

```
[cloud_user@wvanheemstra2c flask-headstart]$ ls
100  200  300  400  500  600  env  README.md
```

Now is a good time to commit your changes back to the renmote repository:

```
git status
```
Create and add the following lines to .gitignore (if the file does not already exist):

```
touch .gitignore
vi .gitignore
```

```
__pycache__/
```

Now add all new files and changes, if any:

```
git add .gitignore
git add *
git commit -m "Add env folder and .gitignore"
git push
```

Now we have to activate the environment, by typing:

```
[cloud_user@wvanheemstra2c flask-headstart]$ source env/bin/activate
(env) [cloud_user@wvanheemstra2c flask-headstart]$ 
```

You will see at the start of your command line '(env)' indicating you are inside the virtual environment.

## 105 Install Required Packages

Having activated the environment (see end of previous section), install the required packages as follows:

```
(env) [cloud_user@wvanheemstra2c flask-headstart]$ pip3 install flask flask-sqlalchemy
```
