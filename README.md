# msvsd4bitservoadc


# Table of Contents
### [Week 0](#week-0)
   * [Prerequisites](#prerequisites)
   * [Open Source tools](#open-source-tools)
   * Inverter


<a name="week-0"></a>
# Week 0

<a name="prerequisites"></a>
### Prerequisites

1. Oracle Virtual box (https://www.virtualbox.org/wiki/Downloads)
2. Linux ubuntu (https://ubuntu.com/download/desktop)
3. Git `sudo apt-get install git`
4. GCC >= 6.1.0  `sudo apt-get install gcc-6 g++-6`
5. Python >= 3.7 `sudo apt-get install python3.7`
 
<a name="open-source-tools"></a> 
## Open Source tools

1. Magic

```
$  git clone git://opencircuitdesign.com/magic
$  cd magic
$	./configure
$  make
$  sudo make install

```
while running the command `./configure` if you got an error `configure: error: cannot find /bin/csh---cannot compile!` we need to follow the steps shown below

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
After compiling these commands run ./configure 

2. SKY130 PDKs

```
$  git clone git://opencircuitdesign.com/open_pdks
$  open_pdks
$	./configure --enable-sky130-pdk
$  make
$  sudo make install

```
3. Netgen

```
$  git clone git://opencircuitdesign.com/netgen
$  cd netgen
$	./configure
$  make
$  sudo make install
```
4. Xschem
```
$  git clone https://github.com/StefanSchippers/xschem.git xschem_git
$ cd xschem_git
$	./configure
$  make
$  sudo make install
```
library
``` 
sudo apt-get install flex
sudo apt-get install bison
sudo apt-get install libxpm-dev 
```
5. Ngspice
```
sudo apt-get update
sudo apt-get install ngspice
sudo apt-get install xterm
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


      
 
