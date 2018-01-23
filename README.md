# Python-Dev

Tips and tricks for python development.

## Managing Python

For managing python installs I use [pyenv](https://github.com/pyenv/pyenv) and [pyenv-virtualenv](https://github.com/pyenv/pyenv-virtualenv).

__pyenv__ Allows you to easily install and manage different versions of python (e.g. 2.7 and 3.6). Further you can set specific versions of python to run within specific directories, or set a default global version.

__pyenv-virtualenv__ allows you to create 'virtualenvs', or isolated python environments. This is useful if - say - you have two projects that both require the same library but one is unable to work with a newer version of that library. 

As a general rule - I create a virtualenv for every new project. 

## requirements.txt 

After I have installed packages for a project I run:

```
pip freeze > requirements.txt
```

This creates a file that looks like this:

```
alabaster==0.7.10
aniso8601==1.3.0
appnope==0.1.0
argcomplete==1.9.3
arrow==0.12.0
asn1crypto==0.23.0
```

Each line is a python package with an `==` and the exact version that was installed. If you send your project to someone else all they need to do is run:

```
pip install -r requirements.txt
```

Within a virtualenv, and all the packages will be installed using the versions listed in the `requirements.txt` file.

## Sublime Text And IPython

Sublime Text is my favorite text editor.

### Sublime-Text Packages

* Package UI - A visual way of examining what Python packages you have installed.
* SendCode - Send code to the terminal (iterm2)


### pyenv build system

In order for Sublime-Text to run the pyenv-specified version or virtualenv of python you are using you have to use a custom build system. Go to __Tools__ → __Build System__ → __New Build System...___ to create a new build system.

The text below can be used to create a pyenv build system. 
```
{
    "cmd": ["/usr/local/var/pyenv/shims/python", "-u", "$file"],
    "file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
    "selector": "source.python"
}
```
