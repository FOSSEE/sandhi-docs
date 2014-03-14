## Getting it
Sandhi, as mentioned earlier, is a free and open-source software, it can be downloaded and distributed freely under GNU GPL V3

### Pre-requisites

Sandhi is conglomeration of lot of libraries and softwares. It uses GNU Radio at its core. For computational purposes, Scilab and Octave can be interfaced with Sandhi. Sandhi uses a special wrapper called Sciscipy which allows one to call scilab functions from python without having to worry about datatype conversion.

---------------------------
### <a href='http://gnuradio.org/redmine/projects/gnuradio/wiki/UbuntuInstall#Install-the-Pre-Requisites'>Installing GNU Radio dependencies</a>

*If on Ubuntu 12.04, one can directly install using command*-


	sudo apt-get -y install git-core autoconf automake make libtool g++ python-dev swig \
	pkg-config libboost1.48-all-dev libfftw3-dev libcppunit-dev libgsl0-dev \
	libusb-dev sdcc libsdl1.2-dev python-wxgtk2.8 python-numpy \
	python-cheetah python-lxml doxygen python-qt4 python-qwt5-qt4 libxi-dev \
	libqt4-opengl-dev libqwt5-qt4-dev libfontconfig1-dev libxrender-dev \
	python-serial python-matplotlib

_Please note that Sandhi has been known to **not** work libboost1.49 available in Ubuntu 12.10_

-------------------------
### <a href='http://forge.scilab.org/index.php/p/sciscipy/'> Sciscipy </a>
Sciscipy is _must_ for Sandhi's control blocks to work; to install:

Clone sciscipy-1.0.0 from our repository; run _install_ script from the directory with **sudo** privileges to automatically pull all dependencies for Sciscipy, build and install it<br>

	git clone https://github.com/manojgudi/sciscipy-1.0.0.git
	cd sciscipy-1.0.0/
	sudo ./install


-------------------------------------------------------------------------

### Build it

    git clone http://github.com/manojgudi/sandhi.git
    cd sandhi/
    git submodule init
    git submodule update

-- UPDATING FROM EXISTING CHECKOUT --

    cd sandhi/
    git pull origin master
    git submodule update

-- Compiling source code --

    cd sandhi/
    mkdir build
    cd build/
    cmake ../
    make -j 2
    sudo make install
    sudo ldconfig

#### Current Build Status  [![Build Status](https://travis-ci.org/manojgudi/sandhi.png)](https://travis-ci.org/manojgudi/sandhi)


### Get Binary

Builds for Ubuntu 12.04 for 64bit Architecture:
http://fossee.in/sandhi_builds/


-------------------------------------------------------------------------
FAQ (Frequently Asked Questions)
--------------------------------------------------------------------------

    
1. I am not able to run SBHS with plant-controller block of Sandhi. <br>

Mostly you don't have sufficient permissions to access /dev/ttyUSB0 (which is SBHS device node in Ubuntu). To solve this, just add your user to _dialout_ group.
	
	sudo adduser `whoami` dialout
**Logout User** and check.

