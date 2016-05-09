# How to Setup and use Jupyter and Ipython notebook on Ubuntu 14.04"

### Introduction

This article will talk you through setting up a server running Ipython and Jupyter notebook and teach you how to connect to and use the notebook app.  By the end of this tutorial, you will be able to use a Python 2.7 using Ipython and Jupyer noteobok.  For the purposes of this tutorial, the walk through will be through using Python 2 (2.7.x) since many of the data science, scientific computing and high performance computing libraries support 2.7 and not 3.0+. 

IPython is an open sourced command shell which orginally developed for the Python Programming language which provides many features such as tab completion, history, interactive shells, browser-based notebook with support for code, text, mathematical expressions inline plots and many other features.  Project Jupyter is a spin off open sourced project which uses IPython as the kernel and provides a similar web notebook interface with support for Julia, R, Haskell and Ruby programming languages.  Jupyter Notebook is a web application that allows you to create and share documents that contain live code, equations, visualizations and explanatory text.  It is very useful as it enables rapid prototyping and reproducable code.  This tutorial will go over getting started with Ipython and Jupyter notebook.

This tutorial only uses open sourced software and package installers, namely apt-get and Pip.  Package installers are useful as they are small progams which made installing code convenient and managable.  Apt-get and Pip was useful as they allow to install open sourced software.  The offical Jupyter install tutorial suggests using the Anaconda distribution by Continuum Analytics which provides an installer and package management for many python packages. While being free to use (even for commercial), it is not fully open sourced and their script (.sh file) includes precompiled binary code.  Precompiled binary means that there was original source code used to generate the code you would be running.  It is not recommended to blindly use precompiled code since the content of the original source code is unknown and can create security flaws on your server.  For this reason is better to install packages on our own or using a fully open sourced package manager such as apt-get and Pip.

## Requirements

To get started, you will need a clean Ubuntu 14.04 server instance with a non-root user set up. The non-root user must be configured with sudo privileges. Learn how to set this up by following our [initial server setup guide](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04).

## Step 1 - Installing Python and Pip
First, update the system's package index. This will ensure that old or outdated packages do not interfere with the installation.

```command
sudo apt-get update
```

First let us install Python 2.7, Python Pip, and Python Development:

```command
  sudo apt-get -y install python2.7 python-pip python-dev
```
Installing `python2.7` will update python to the latest version of Python 2.7, and `python-pip` will install Pip which allows us to manage Python packages we would like to use.  Since some of Jupyter’s dependencies may require compilation, in which case you would need the ability to compile Python C-extensions. This means a C compiler and the Python headers which is installed with `python-dev`

## Step Two - Installing Ipython and Ipython Notebook 

By this point you should have Python 2.7 installed.  This can be checked using the following command:

```command
  python --version
```

This will output:

```
  Python 2.7.6
```
Depending on the lastest version of Python 2.7, the output might be different (for example 2.7.7, 2.7.8 etc.)

You can also check if Pip is installed using the following command:

```commend
    pip --version
```

Which will output:

```
    pip 1.5.4 from /usr/lib/python2.7/dist-packages (python 2.7)
```
Now that we have all of the requirements, let us begin by installing the Ipython and Ipython Notebook

```
  sudo apt-get -y install ipython ipython-notebook
```

## Step Three - Installing Jupyter Notebook

Now we can move onto installing Jupyter notebook:

```
  pip install jupyter

```

[Jupyer notebook](http://jupyter-notebook-beginner-guide.readthedocs.org/en/latest/what_is_jupyter.html) (or notebooks) are documents produced by the Jupyter Notebook App which contain both computer code (e.g. Python) and rich text elements (paragraph, equations, figures, links, etc...). Notebook documents are both human-readable documents containing the analysis description and the results (figures, tables, etc..) as well as executable documents which can be run to perform data analysis.

### Installing Jupyter Notebook Custom Themes (Optional)

This step is optional.  Just like any other development environment, with Jupyter notebook, you can change the theme, color scheme and syntax highlighting.  I personally prefer dark themes such as [Oceans16](https://github.com/dunovank/jupyter-themes), you can follow the following steps to choose a different theme.

```
  pip install git+https://github.com/dunovank/jupyter-themes.git

```
We are going to install theme (-t) for ipython/jupyter version > 3.x (-J) with the toolbar (-T)

```
  jupyter-theme -J -t oceans16 -T

```

## Step Four - Running Jupyter Notebook

Running Jupyter notebook is as simple as running the following command:

```
  jupyter notebook

```

When you run Jupyter notebook, it runs on a specific port number. The first notebook you are running will run generally on port 8888.  If you are running Jupyter notebook on a local Linux computer, you can simply navigate to [localhost:8888](http://localhost:8888) to connect to Jupyter notebook.  If you are running Jupyter on a server (such as a Digital Ocean droplet) without a web browser, it will still run but give you an error stating that Ipython notebook requires JavaScipt as shown below.  This is expected since JavaScript is not necessary on a server without a web browser.  You can type q and then enter on the keyboard and confirm by to closing w3m by hitting y and then enter which will remove the error message (and show you which port Jupyter is running on).

![](/images/jupyter-server.png)

## Step Five - Connecting to the server using SSH Tunneling

In this section we will learn how to connect to Jupyter notebook using SSH tunneling.  While SSH tunneling might sound scary, the concept is very simple.  Since Juptyer notebook is running on a specific port such as 8888, 8889 etc, SSH tunneling enables you to connect to the server's port securely.  Since we are used to running Jupyter notebook on a specific port number, we can create a secure tunnel which listens on the the server's port (8888 for example) and securely forwards a port on our local computer on a specific port (8000 for example).

### Mac or Linux

If using Linux of Mac, this can be done simply by running the following SSH command:

```
  ssh -L 8888:localhost:8000 server_username@<server ip address>

```
You should change 8888 to the port which Jupyter notebook is running on, and optionally change port 8000 to one of your choosing (if 8000 is used by another process).  Your server_username is your username on the server and the `<server ip address>` could be an actual IP address or a URL depending on who is providing your virtual machine.  In the csclub example, the server_username is your csclub username (generally your quest ID) and the server ip would be for example [corn-syrup.uwaterloo.ca](http://corn-syrup.uwaterloo.ca).  The command I would run if my username is andrew.andrade is: 

```
  ssh -L 8888:localhost:8000 andrew.andrade@corn-syrup.uwaterloo.ca

```
If no error shows up after running the `ssh -L` command and you tunneled the port to 8000 (for example), you can simply navigate to [localhost:8000](http://localhost:8000) in your favourite web browser to connect to Jupyer notebook running on the server!


### Windows

If you are using windows, you can also easily tunnel ssh using putty.  As you may remember, you SSH into a server, you enter the server url into the host name as shown in the figure below (for connecting to corn-syrup from the uwaterloo csclub).

![](/images/putty.png)

Next click the `+ SSH` on the bottom left, and then click tunnels.  You can now enter the port you want to access Jupyter on your local machine (for example 8000), and set the destination as `localhost:8888` where 8888 is the number of the port that Jupyter notebook is running on.  Now click the add button and the ports should appear in the Forwarded ports: section.

For the example of uWaterloo's csclub, my Putty configuration screen looks like the following:

![](/images/putty-tunneling.png)

Finally you can hit open, and you will now both connect to the server via SSH and tunnel the desired ports.  If no error shows up and you tunneled the port to 8000 (for example), you can simply navigate to [localhost:8000](http://localhost:8000) in our favourite web browser to connect to Jupyter notebook running on the server!

# Using Jupyter notebook

Jupyter notebook will show all of the files and folders in the directory it is run from.  We can now create a new notebook file by click new > python2 from the top right.  This will open a notebook.  We can now run python code in the cell or change the cell to markdown (by Cell > Cell Type > Markdown) and write notes and even put equations in  $$\LaTeX$$ by putting them between the `$$` symbols.  For example, to generate $$ y = x^2$$ you can write the following

```
$$ y = x^2$$
```

You can also download Jupyter Notebooks off the internet and open them in Jupyer.  For now let us make a simple plot from the Anscombe's quartet using the seaborn library.  We can do this by just typing the following into the first cell

```python 

import seaborn as sns
sns.set(style="ticks")
%matplotlib inline
# Load the example dataset for Anscombe's quartet
df = sns.load_dataset("anscombe")

# Show the results of a linear regression within each dataset
sns.lmplot(x="x", y="y", col="dataset", hue="dataset", data=df,
           col_wrap=2, ci=None, palette="muted", size=4,
           scatter_kws={"s": 50, "alpha": 1})

```

Please note we use `%matplotlib inline` for the plots to appear inline in the notebook (instead of a pop-up).  When using Jupyter Notebook, the easiest way to see a plot is in-line.

To get a quick tour of Jupyter notebook, you can go to Help > User Interface Tour as show below:

![](/images/jupyter.png)

Once you have installed everything and Jupyter is running you can move onto to installing R and RStudio by following the [Absolute Beginners Tutorial for Getting Started Doing Data Science using Servers](/beginner-tutorial-getting-started-with-data-science-using-servers).
