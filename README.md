# msvsd4bitservoadc


# Table of Contents
## [Week 0](#week-0)
   * [Prerequisites](#prerequisites)
   * [Open Source tools](#open-source-tools)
   * [CMOS Inverter](#cmos-inverter)


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
<img width="920" alt="magic" src="https://user-images.githubusercontent.com/64173714/217902603-0b9c9eef-1d04-4b16-92b0-47859671e4f1.png">


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
<img width="922" alt="open_pdk" src="https://user-images.githubusercontent.com/64173714/217903616-ad0e3fc3-993c-4d41-bad9-7f43700431a5.png">

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
<img width="922" alt="netgen" src="https://user-images.githubusercontent.com/64173714/217904006-9be0048a-e810-40d4-8d72-75bdbd1a1089.png">

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
<img width="922" alt="xschem " src="https://user-images.githubusercontent.com/64173714/217904558-a577c075-d8a2-420f-b2c8-8a90bf9e345e.png">

5. Ngspice

ngspice is an open-source electronic circuit simulator that can be used for circuit analysis and simulation.
Download the tarball from https://sourceforge.net/projects/ngspice/files/ng-spice-rework/old-releases/37/ and unpack it
```
 $ tar -zxvf ngspice-37.tar.gz
 $ cd ngspice-37
 $ mkdir release
 $ cd release
 $ ../configure  --with-x --with-readline=yes --disable-debug
 ```
 To avoid errors after running the `./configure` command, some additional libraries should be installed in the system.
 ```
 sudo apt-get install libxaw7-dev
 sudo apt-get install libreadline-dev
 ```
 Rerun the `./configure` command after installing the libraries.
 ```
 $ make
 $ sudo make install
 ```
<img width="921" alt="ngspice" src="https://user-images.githubusercontent.com/64173714/217905232-11985213-ed63-4449-9146-add781f941f9.png">


6. ALIGN tool

ALIGN is an open-source analogue circuit layout generator. The goal of ALIGN (Analog Layout, Intelligently Generated from Netlists) is to automatically translate an analogue circuit's unannotated (or partially annotated) SPICE netlist to a GDSII layout.
Prerequisites in the system are required for installation. 
`gcc >= 6.1.0` 
`python >= 3.7`

Use the following commands to install ALIGN tool

1.Setting the compiler paths 
```
export CC=/usr/bin/gcc
export CXX=/usr/bin/g++
```

2.Clone the ALIGN source code to your local environment
```
git clone https://github.com/ALIGN-analoglayout/ALIGN-public
cd ALIGN-public
```
3.Create a Python virtualenv
```
sudo apt update
sudo apt install python3.10-venv
python3 -m venv general
source general/bin/activate
python3 -m pip install pip --upgrade
```

4.Install ALIGN as a USER
```
pip install -v .
```
If the error message "boost not found" appears while running as user, install the necessary libraries `sudo apt-get install libboost-all-dev` and rerun the user command.

To avoid errors in the installation we required build wheels and setuptools for align and gdspy
for gdspy
```
pip install --upgrade pip
pip install --upgrade setuptools
pip install wheel
sudo apt-get install python3-dev libffi-dev libssl-dev
pip install gdspy
pip install --no-binary :all: gdspy
```
for align
```
pip install --upgrade pip
pip install --upgrade setuptools
pip install wheel
pip install align
pip install --no-binary :all: align
```
5. Install ALIGN as a DEVELOPER
```
pip install -e .
```
6.For ALIGN (C++) Extension developers
```
pip install setuptools wheel pybind11 scikit-build cmake ninja
ip install -v -e .[test] --no-build-isolation
pip install -v --no-build-isolation -e . --no-deps --install-option='-DBUILD_TESTING=ON'
```
Adapting ALIGN to Sky130 technology

Clone the following ALIGN-public directory repository
```
git clone https://github.com/ALIGN-analoglayout/ALIGN-pdk-sky130
```
move `SKY130_PDK` folder to `/home/venkat/PD/ALIGN-public/pdks`

Running ALIGN TOOL

Run the following commands every time we start the tool in a new terminal
```
python3 -m venv general
source general/bin/activate
```
Make a new directory and switch to it
```
mkdir work && cd work
```
General syntax for providing inputs
```
$ schematic2layout.py <NETLIST_DIR> -p <PDK_DIR> -c
```
Running a Example
```
schematic2layout.py ../examples/telescopic_ota -p ../pdks/FinFET14nm_Mock_PDK/
```
<img width="926" alt="week 0 align -1 " src="https://user-images.githubusercontent.com/64173714/217905400-0bc80b96-65fd-4f0a-b535-bc58447fe04a.png">

Running a Example on Sky130pdk

```
schematic2layout.py ../ALIGN-pdk-sky130/examples/five_transistor_ota -p ../pdks/SKY130_PDK/
```
<img width="925" alt="align 2" src="https://user-images.githubusercontent.com/64173714/217905324-340322ca-53a0-4713-9e90-5b6c970abe7c.png">
 
Verifying the installation of open_pdk

To create an initial working directory, copy the following files:
```
$ mkdir LABS
$ cd LABS
$ mkdir mag
$ mkdir netgen
$ mkdir xschem
$ cd xschem
$ cp /home/venkat/PD/open_pdks/sky130/sky130A/libs.tech/xschem/xschemrc .
$ cp /home/venkat/PD/open_pdks/sky130/sky130A/libs.tech/ngspice/spinit .spiceinit
$ cd ../mag
$ cp /home/venkat/PD/open_pdks/sky130/sky130A/libs.tech/magic/sky130A.magicrc .magicrc
$ cd ../netgen
$ cp /home/venkat/PD/open_pdks/sky130/sky130A/libs.tech/netgen/sky130A_setup.tcl .
```
<a name="cmos-inverter"></a>

## CMOS INVERTER

  A CMOS inverter is a type of digital circuit that converts a digital input signal from one state (e.g., 0 or 1) to its opposite state (e.g., 1 or 0). It is a fundamental component of digital electronics that is widely used in digital systems such as microprocessors, digital logic circuits, and digital-to-analog converters.

A CMOS inverter is typically made up of two complementary transistors, one p-type (pMOS) and one n-type (nMOS). The pMOS transistor pulls the output high, while the nMOS transistor pulls the output low. When the inverter's input is high (1), the nMOS transistor is turned on and the pMOS transistor is turned off, resulting in a low output. When the inverter's input is low (0), the pMOS transistor is turned on and the nMOS transistor is turned off, resulting in a high output.

One of the primary advantages of CMOS inverters is their low power consumption, as the transistors are only turned on when the input changes state, rather than constantly drawing current. Moreover, CMOS inverters are highly scalable and easily integrated into larger circuits, making them a popular choice for digital system design.    

## Creating Inverter Schematic using xschem
The schematic circuit is created by connecting components from the open_pdk library and performing dc analysis.

<img width="922" alt="new inv" src="https://user-images.githubusercontent.com/64173714/217958297-1a19653e-2b18-4c21-95f0-0581908c9495.png">

DC analysis would be used to create a Voltage Transfer Characteristics (VTC) curve for the circuit. It will sweep the value of Vin from high to low to determine how the circuit works with respect to different voltage levels in the input. When the simulation is run, the plot shown below is obtained.

<img width="737" alt="dc plot2" src="https://user-images.githubusercontent.com/64173714/217958433-acfb5f75-26ed-4396-aa74-793e08e94a16.png">

The schematic circuit is created by connecting components from the open_pdk library and performing transient analysis.

<img width="923" alt="transient sch" src="https://user-images.githubusercontent.com/64173714/217958466-b3f6650e-7248-400f-bfbf-6537ebb4876c.png">

Transient analysis of a circuit is the simulation of the circuit's electrical behaviour over time, specifically its response to changing input signals.

<img width="745" alt="tran grap" src="https://user-images.githubusercontent.com/64173714/217958494-7689ef31-a95a-4bcc-840f-be18e72d1dc7.png">
