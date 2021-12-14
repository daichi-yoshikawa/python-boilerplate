# <project-name>

## Introduction

## Example

## Usage

## Requisites

## (Option1) Steps to upload package to PyPi
### Step 0 Create PyPI account
[Pypi.org](https://pypi.org/)

[PyPI.org](https://pypi.org/)

### Step 1 Clean up egg-info and dist directories
```
$ rm -rf <path-to-root-of-project>/*.egg-info <path-to-root-of-project>/dist
```
Remove <package-name>.egg-info dir and dist dir if exists

### Step 2 Create package to distribute
```
$ python setup.py sdist bdist_wheel
```

### Step 3 Experimentally upload to PyPI and try to install
```
$ twine upload --repository testpypi dist/*
$ pip --no-cache-dir install --upgrade --index-url https://test.pypi.org/simple/<package-name>
```

### Step 4 Upload and install package and try to install
```
$ twine upload --repository pypi dist/*
$ pip --no-cache-dir install --upgrade <package-name>
```

## (Option2) Create virtualenv
### Step 1 Install requisites
```
$ sudo apt-get install git gcc make openssl libssl-dev libbz2-dev libreadline-dev libsqlite3-dev zlib1g-dev libffi-dev
```

### Step 1.5 Install tkinter(This may be needed to use matplotlib in virtualenv)
```
$ sudo apt-get install python3-tk python-tk tk-dev
```

### Step 2 Install pyenv
```
   $ cd ~
   $ git clone git://github.com/yyuu/pyenv.git ./pyenv
   $ mkdir -p ./pyenv/versions ./pyenv/shims
```

### Step 3 Set env variable
Add the following description in ~/.bashrc
```
export PYENV_ROOT=${HOME}/Documents/pyenv
if [ -d "${PYENV_ROOT}" ]; then
  export PATH=${PYENV_ROOT}/bin:$PATH
  eval "$(pyenv init -)"
fi
```
** Dec 2021 Update **
As mentioned below, you may need to use **eval "$(pyenv init --path)"** instead of **eval $(pyenv init -)** due to software update.
https://stackoverflow.com/questions/33321312/cannot-switch-python-with-pyenv

### Step 4 Enable update of .bashrc
```
   $ exec $SHELL -l
   $ . ~/.bashrc
```

### Step 5 Install pyenv-virtualenv
```
   $ cd $PYENV_ROOT/plugins
   $ git clone git://github.com/yyuu/pyenv-virtualenv.git
```

### Step 6 Install python
```
   $ pyenv install <version-you-install>
```
Eg.)
```
   $ pyenv install 3.7.8
```

### Step 7 Create local pyenv
```
   $ pyenv virtualenv <version-you-install> <pyenv-name>
```
Eg.)
```
   $ pyenv virtualenv 3.7.8 py378-webapp
```

### Step 8 Associate the created pyenv with work directory
```
   $ cd <path-to-work-dir>
   $ pyenv local <pyenv-name>
   $ pip install --upgrade pip
```
Eg.)
```
   $ cd ~/work/webapp
   $ pyenv local py378-webapp
   $ pip install --upgrade pip
```

Now you can enjoy python virtualenv.

