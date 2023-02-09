# msvsd4bitservoadc


# Table of Contents
## [Week 0](#week-0)
   * [Prerequisites](#prerequisites)
   * [Open Source tools](#open-source-tools)
   * CMOS Inverter


<a name="week-0"></a>
## Week 0

<a name="prerequisites"></a>
### Prerequisites

1. Oracle Virtual box (https://www.virtualbox.org/wiki/Downloads)
2. Linux ubuntu (https://ubuntu.com/download/desktop)
3. Git `sudo apt-get install git`
4. GCC >= 6.1.0  `sudo apt-get install gcc-6 g++-6`
5. Python >= 3.7 `sudo apt-get install python3.7`
 
<a name="open-source-tools"></a> 
### Open Source tools

1. Magic

Magic is a VLSI Layout tool.
To begin installing the open source tool, go to http://opencircuitdesign.com/magic/ and the following steps

```
$  git clone git://opencircuitdesign.com/magic
$  cd magic
$	./configure
```
while running the command `./configure` If you received the error `configure: error: cannot find /bin/csh—-cannot compile!` We must take the steps outlined below.
```
$ sudo apt-get install m4
$ sudo apt-get install tcsh
$ sudo apt-get install csh
$ sudo apt-get install libx11-dev
$ sudo apt-get install tcl-dev tk-dev
$ sudo apt-get install mesa-common- dev libglu1-mesa-dev
optional
$ sudo apt-get install libcairo2-dev
```
Magic requires the following additional packages to be compiled. After installing all of the packages and running the `./configure` command again
```
$  make
$  sudo make install
```


2. SKY130 PDKs

Process Design Kits, or OpenPDKs, are open source libraries and tools for designing and manufacturing integrated circuits (ICs). They provide a detailed set of design rules, library components, and other resources required for the physical design of an integrated circuit.

To begin installing the open source tool, go to http://opencircuitdesign.com/open_pdks/ and the following steps
```
$  git clone git://opencircuitdesign.com/open_pdks
$  open_pdks
$	./configure --enable-sky130-pdk
$  make
$  sudo make install

```
3. Netgen

Netgen is an open-source tool for creating electrical circuits and layouts automatically. It can generate a wide range of electrical circuits, such as full-custom layouts, standard cell-based layouts, and gate arrays. It can also generate routing data and physical masks for use in the fabrication of the final IC.
To begin installing the open source tool, go to http://opencircuitdesign.com/netgen/ and the following steps

```
$  git clone git://opencircuitdesign.com/netgen
$  cd netgen
$	./configure
$  make
$  sudo make install
```

4. Xschem

XSCHEM is an open-source schematic capture tool for designing electronic circuits. It is available at https://github.com/StefanSchippers/xschem, and installation instructions are provided. 
```
git clone https://github.com/StefanSchippers/xschem.git xschem
cd xschem
./configure --prefix=/home/venkat 
```
To avoid errors after running the `./configure` command, some additional libraries should be installed in the system.
``` 
sudo apt-get install flex
sudo apt-get install bison
sudo apt-get install libxpm-dev 
sudo apt-get install libx11-xcb-dev
sudo apt-get install libjpeg-dev
```
Rerun the `./configure` command after installing the libraries.
```
make -j4
make install
```
After installing xschem, we should install xschem_sky130 in order to obtain XSCHEM symbol libraries for the Google-Skywater 130nm process design kit. It is available at https://github.com/StefanSchippers/xschem_sky130, and installation instructions are provided. 

```
cd xschem_library
git clone https://github.com/StefanSchippers/xschem_sky130.git xschem_sky130
cd xschem_sky130/
```




5. Ngspice
```
 $ tar -zxvf ngspice-37.tar.gz
 $ cd ngspice-37
 $ mkdir release
 $ cd release
 $ ../configure  --with-x --with-readline=yes --disable-debug
 $ make
 $ sudo make install
 
 errors
 sudo apt-get install libxaw7-dev
 sudo apt-get install libreadline-dev

```

6. ALIGN tool

pre -

gcc >= 6.1.0
python >= 3.7

``` 
export CC=/usr/bin/gcc
export CXX=/usr/bin/g++
git clone https://github.com/ALIGN-analoglayout/ALIGN-public
cd ALIGN-public
sudo apt update
sudo apt install python3.10-venv
python3 -m venv general
source general/bin/activate
python3 -m pip install pip --upgrade

pip install -v .
error - wheels not found Could not build wheels for align, which is required to install pyproject.toml-based projects/ailed building wheel for gdspy
pip install --upgrade pip
pip install --upgrade setuptools
pip install wheel
sudo apt-get install python3-dev libffi-dev libssl-dev
pip install gdspy
pip install --no-binary :all: gdspy

align
pip install --upgrade pip
pip install --upgrade setuptools
pip install wheel
pip install align
pip install --no-binary :all: align

boost not found
sudo apt-get install libboost-all-dev
re-run user command


pip install -e .
pip install setuptools wheel pybind11 scikit-build cmake ninja
ip install -v -e .[test] --no-build-isolation
pip install -v --no-build-isolation -e . --no-deps --install-option='-DBUILD_TESTING=ON'

```

```
git clone https://github.com/ALIGN-analoglayout/ALIGN-pdk-sky130
```
SKY130_PDK to /home/venkat/PD/ALIGN-public/pdks
```
python3 -m venv general
source general/bin/activate
```
```
mkdir work && cd work
```
```
$ schematic2layout.py <NETLIST_DIR> -p <PDK_DIR> -c
```
```
schematic2layout.py ../examples/telescopic_ota -p ../pdks/FinFET14nm_Mock_PDK/
```
```
schematic2layout.py ../ALIGN-pdk-sky130/examples/five_transistor_ota -p ../pdks/SKY130_PDK/
```

## CMOS INVERTER

      
 
