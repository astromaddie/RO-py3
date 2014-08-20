Installing the RO Python Package
================================

See the [Overview](Overview.html) for a summary of the RO package.

Prerequisites
-------------

-   Python 2.4 or later (with Tkinter if using timers or widgets)
-   numpy
-   simplejson, if using a Python older than 2.6
-   matplotlib (optional: used by RO.Wdg.StripChartWdg)
-   pyfits 1.1 or later (optional: used by RO.DS9)
-   PIL or Pillow (optional: used by RO.Wdg.GrayImageWdg)
-   pygame, including pygame.mixer (optional: used by RO.Sound to play sound files)
-   pip or easy\_install (optional, but makes installation easier)
-   twisted framework (optional: used by some classes in RO.Comm)

Installation
------------

If you have pip or easy\_install (you may have to use sudo or run as root):

> % pip install RO

or

> % easy\_install RO

If you prefer, you may manually download it from [PyPI](http://pypi.python.org/pypi?:action=display&name=RO) and run:

> % python setup.py install

or, since RO is pure python, simply copy the RO directory to site-packages.

### Installation for use withe eups

If you are wish to manage RO with the eups package management then install RO as follows (instead of using the above instructions):

Download the RO package from [PyPI](http://pypi.python.org/pypi?:action=display&name=RO)

Unpack it

Move the unpacked directory where you wish to leave it

cd into the main directory of the unpacked package (named ROPackage)

\$ eups declare -r . RO *version* (where *version* matches the version you downloaded)

Notes
-----

-   The code is presently pure python, though that may not always be so.
-   This code is provided "as is". Much of the code is quite well tested and is used daily, but some is not.
-   I cannot provide much technical support but am always happy to receive bug reports and patches.
-   The ups directory is for use with a package manager called eups; non-eups users can safely ignore it.

