## Install NumPy, SciPy, scikit-learn on Mac OS X for data miners

Add on and summarized from blog http://penandpants.com/2012/02/24/install-python/

Outline: 1. install Xcode --> 2. install pip --> 3. install brew --> 4. install NumPy --> 5. install gfortran (important!) --> 6. install SciPy --> 7. install matplotlib (useful) --> 8. install scikit-learn --> 9. test

Preamble: Python 2.5 ~ above is preinstalled in the current Mac OS lion. To make sure, in terminal (search in spotlight), type python after $, you should be able to see the python version installed and prompted to the python interpretation environment. Else type "sudo easy_install python" to intall python2.

1. Download Xcode from app store and install it. After that, open installed Xcode, go to Preferences -->   Download--> Command Line Tools, click 'install' to install the commands which are not installed in the shell.

2. The following steps will all be done in terminal.  For this step, sudo easy_install pip.

3.

ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
(updated according to source: http://brew.sh/)

export PATH=/usr/local/bin:/usr/local/share/python:$PATH

4. sudo pip install numpy

5. brew install gfortran  --> this is a critical step before installing scipy, as many dependencies of the latter is contained in this package

6. sudo pip install scipy

7. sudo pip install matplotlib

8. sudo pip install scikit-learn

9. launch python and test the installed packages.

(after $) python -->

(after >>>)

import numpy

import scipy

import matplotlib

import sklearn

Successfully installed all the packages if no error found after the import!

In addition, pandas can also be a handy library for data analysis, to install:

sudo pip install pandas

END
