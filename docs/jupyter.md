# Jupyter Notebooks

---

## Installation

Update, install pip for python3 and install `virtualenv`

```sh
sudo apt-get update
sudo apt-get install python3-pip
sudo pip3 install virtualenv
```

Create the Jupyter Notebooks folder

```sh
mkdir ~/Jupyter
cd ~/Jupyter
```

Inside the folder create a virtual environment

```sh
virtualenv env
```

Activate the virtual environment

```sh
source ~/Jupyter/env/bin/activate
```

Once activated the virtual environment install Jupyter Notebooks

```sh
pip install jupyter
```

Set the password:

```sh
jupyter notebook password
```

## Create and modify the configuration file

Create the configuration file:

```sh
jupyter notebook --generate-config
```

Edit the configuration file:

```sh
vim ~/.jupyter/jupyter_notebook_config.py
```

Inside the file add the next lines, in this case `IP=192.168.0.114` and `PORT=8888`:

```python
c.NotebookApp.open_browser = False
c.NotebookApp.ip = '192.168.0.114'
c.NotebookApp.port = 8888
c.NotebookApp.alow_remote_access = True
```

## Start a notebook

```sh
jupyter notebook
```
