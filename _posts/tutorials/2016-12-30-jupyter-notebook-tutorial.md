# How to Install, Run and Connect to Jupyter and Ipython Notebook on a Remote Server (Ubuntu 14.04)

### Introduction

This article will talk you through setting up a server running Ipython and Jupyter notebook and teach you how to connect to and use the notebook app on a remote server.  Jupyer notebook (or simply notebooks) are documents produced by the Jupyter Notebook App which contain both computer code (e.g. Python) and rich text elements (paragraph, equations, figures, links, etc...) which aides in presenting reproducable research. 

By the end of this tutorial, you will be able to use Python 2.7 using Ipython and Jupyer notebook.  For the purposes of this tutorial, the walk through will be through using Python 2 (2.7.x) since many of the data science, scientific computing and high performance computing libraries support 2.7 and not 3.0+. 

IPython is an open sourced command shell which originally developed for the Python Programming language which provides many features such as tab completion, history, interactive shells, browser-based notebook with support for code, text, mathematical expressions in-line plots and many other features.  Project Jupyter is a spin off open sourced project which uses IPython as the kernel and provides a similar web notebook interface with support for Julia, R, Haskell and Ruby programming languages.  Jupyter Notebook is a web application that allows you to create and share documents that contain live code, equations, visualizations and explanatory text.  It is very useful as it enables rapid prototyping and reproducible code.  This tutorial will go over getting started with Ipython and Jupyter notebook.

This tutorial only uses open sourced software and package installers, namely apt-get and Pip.  Package installers are useful as they are small programs which made installing code convenient and manageable.  Apt-get and Pip was useful as they allow to install open sourced software.  The official Jupyter install tutorial suggests using the Anaconda distribution by Continuum Analytics which provides an installer and package management for many python packages. While being free to use (even for commercial), it is not fully open sourced and their script (.sh file) includes precompiled binary code.  Precompiled binary means that there was original source code used to generate the code you would be running.  It is not recommended to blindly use precompiled code since the content of the original source code is unknown and can create security flaws on your server.  For this reason is better to install packages on our own or using a fully open sourced package manager such as apt-get and Pip.

## Requirements

To get started, you will need a clean Ubuntu 14.04 server instance with a non-root user set up. The non-root user must be configured with sudo privileges. Learn how to set this up by following our [initial server setup guide](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04).

## Step 1 - Installing Python 2.7 and Pip

In this section will will install Python 2.7 and Pip.  First, update the system's package index. This will ensure that old or outdated packages do not interfere with the installation.

```command
sudo apt-get update
```

Next Nextlet us install Python 2.7, Python Pip, and Python Development:

```command
sudo apt-get -y install python2.7 python-pip python-dev
```

Installing `python2.7` will update python to the latest version of Python 2.7, and `python-pip` will install Pip which allows us to manage Python packages we would like to use.  Since some of Jupyter’s dependencies may require compilation, in which case you would need the ability to compile Python C-extensions. This means a C compiler and the Python headers which is installed with `python-dev`

## Step Two - Installing Ipython and Jupyter Notebook 

In this section we will install Ipython and Jupyter Notebook.  By this point you should have Python 2.7 installed.  This can be checked using the following command:

```command
python --version
```

This will output:

```
[secondary_label output]
Python 2.7.6
```

Depending on the lastest version of Python 2.7, the output might be different (for example 2.7.7, 2.7.8 etc.).

You can also check if Pip is installed using the following command:

```command
pip --version
```

Which will output:

```
[secondary_label output]
pip 1.5.4 from /usr/lib/python2.7/dist-packages (python 2.7)
```

Similarly depending on your version of pip, the output might be slightly different.  Now that we have all of the requirements, let us begin by installing the Ipython and Ipython Notebook.

```command
  sudo apt-get -y install ipython ipython-notebook
```

Now we can move onto installing Jupyter notebook:

```command
sudo pip install jupyter
```

## Step Three - Running Jupyter Notebook

In this section we will run Jupyter notebook which is as simple as running the following command:

```command
jupyter notebook
```

When you run Jupyter notebook, it runs on a specific port number. The first notebook you are running will run generally on port `:8888`.  To check the specific port number Jupyter notebook is running on, you can press `CTRL+C` and a the following is a sample output:

```
[secondary_label output]
[I 15:17:08.147 NotebookApp] interrupted
Serving notebooks from local directory: ~/demo
0 active kernels 
The IPython Notebook is running at: http://localhost:8888/
```

If you are running Jupyter notebook on a local Linux computer, you can simply navigate to [localhost:8888](http://localhost:8888) to connect to Jupyter notebook.  If you are running Jupyter on a server (such as a Digital Ocean droplet), it will still run but it might give you an error stating that Ipython notebook requires JavaScipt as shown below:

![](http://i.imgur.com/48WFDWH.png)

This error is expected since JavaScript is not necessary on a server.  You can now follow Step Four to connect to the notebook using a server.

## Step Four - Connecting to the server using SSH Tunneling

In this section we will learn how to connect to Jupyter notebook using SSH tunneling.  While SSH tunneling might sound scary, the concept is very simple.  Since Jupyter notebook is running on a specific port on the Droplet such as `:8888`, `:8889` etc, SSH tunneling enables you to connect to the Droplet's port securely.

The first step in SSH tunneling is being able to connect to the server using SSH.  If you are using Linux or Mac you can follow our guide [How To Use SSH Keys with DigitalOcean Droplets using Linux or Mac](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets) if you don't know how to connect to the Droplet using SSH.  For those who are using Windows on your home computer you can follow our guide on [How To Use SSH Keys with PuTTY on DigitalOcean Droplets for Windows users](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-putty-on-digitalocean-droplets-windows-users).  The Windows and Putty users can then skip the next subsection, and follow's the Window's guide using Putty further below.

### SSH Tunneling using Mac or Linux

If using Linux of Mac, SSH tunneling can be done simply by running the following SSH command:

```command
ssh -L <^>8000<^>:localhost:<^>8888<^> <^>your_server_username<^>@<^>your_server_ip<^>
```

`ssh` is the standard command to open a ssh connection but `-L ` specifies that the given port on the local (client) host is to be forwarded to the given host and port on the remote side (droplet).  This means that what ever is running on second port number (ie `<^>:8888<^>`) on the droplet will appear on the first port number (ie. `<^>8000<^>`) on your local computer.  You should change `<^>:8888<^>` to the port which Jupyter notebook is running on, and optionally change port `<^>8000<^>` to one of your choosing (for example if `8000` is used by another process). It is recommended to use a port greater or equal to `8000` as those port numbers are unlikely to be used by another process. `<^>server_username<^>` is your username (ie sammy) on the droplet which you created and <^>your_server_ip<^> is the  IP address of your droplet.  For example if my username was `<^>sammy<^>` and the server address was `<^>111.111.111.111<^>` the command I would run is  `ssh -L <^>8000<^>:localhost:<^>8888<^> <^>sammy<^>@<^>111.111.111.111<^>`.  If no error shows up after running the `ssh -L` command, you can run Jupyter notebook:

```command
jupyter notebook
```

Now simply navigate to the local port, for example [http://localhost:<^>8000<^>](http://localhost:8000) (or what ever port number you choose) in your favourite web browser to connect to Jupyer notebook running on the server!  The next subsection provides instructions for those using Windows and Putty so if you follow the steps for Linux or Mac, you can skip the next subsection and move onto the section where we go over the basics of using the Jupyter Notebook.

### SSH Tunneling using Windows and Putty

If you are using windows, you can also easily tunnel ssh using Putty as outlined in [our guide here](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-putty-on-digitalocean-droplets-windows-users).  The server url or ip address is entered into the host name as shown:

![](http://i.imgur.com/SiOcXyL.png)

Next click the `+ SSH` on the bottom of the left pane, and then click tunnels.  You can now enter the port you want to access Jupyter on your local machine.  Generally choose  `<^>8000<^>`or greater (ie `<^>8001<^>`, `<^>8002<^>`, etc.)` and set the destination as `localhost:<^>8888<^>` where '<^>:8888<^> is the number of the port that Jupyter notebook is running on.  Now click the add button and the ports should appear in the Forwarded ports,  The Putty configuration screen should look like the following:

![](http://i.imgur.com/3kx9Etn.png)

Finally you can hit open, and you will now both connect to the server via SSH and tunnel the desired ports.  If no error shows up and you tunneled the port to `<^>:8000<^>` (for example), you can simply navigate to [http://localhost:<^>8000<^>](http://localhost:8000) in our favourite web browser to connect to Jupyter notebook running on the server!

## Step 5 - Using Jupyter Notebook

This section goes over the basics of using Jupyter Notebook.  By this point you should have Jupyer notebook running and you should be connected to it using a web browser.  Jupyter notebook is very powerful and has many features and this section will outline the very basic features just to get us started using the notebook.  Automatically Jupyter notebook will show all of the files and folders in the directory it is run from.  We can now create a new notebook file by click new > python2 from the top right:

![](http://i.imgur.com/fULT990.png)

This will open a notebook.  We can now run Python code in the cell or change the cell to markdown.  For example change the first cell to accept Markdown by Cell > Cell Type > Markdown.  We can now write notes using Markdown and even put equations in  LaTeX by putting them between the `$$` symbols.  For example, type the following into the cell after changing it to markdown :

```
# Simple Equation

Let us now implement the following equation in Python:
$$ y = x^2$$

where $x = 2$
```

To turn the markdown into rich text, press `CTRL+ENTER` and the following should be the result:

![](http://i.imgur.com/D4MeS7W.png)

You can use the markdown cells to make notes and document your code.  Now let us implement that simple equation and print the result.   Hit Insert > Insert Cell Below  to insert and cell and enter the following code:

```
x = 2
y = x*x
print y
```

To run the code, press `CTRL+ENTER`, the following should be the result:

![](http://i.imgur.com/l3bHNCO.png)

You now have the ability to include libraries and use the notebook as you would with any other Python development environment!


## Where To Go From Here?

Congratulations! You should be now able to write reproducible Python code and notes using markdown using Jupyter notebook running on a Droplet.  To get a quick tour of Jupyter notebook, you can go to Help > User Interface Tour as show below:

![](http://i.imgur.com/HXsLPzs.png)

In the future we will be releasing more advanced for running servers for data science which will make use of Jupyter notebook!
