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

1. Windows machine - 4GB RAM, 100GB Hard disk
2. Oracle Virtual box - 7.0.6 (https://www.virtualbox.org/wiki/Downloads)
3. Linux ubuntu - 22.04.1 (https://ubuntu.com/download/desktop)
4. Install Git -  `sudo apt-get install git`
5. Install GCC compiler -  `sudo apt-get install gcc g++`
6. Install Python - `sudo apt-get install python3`
 
<a name="open-source-tools"></a> 
### Open Source tools

| | Tools | Description|
|--|--|--|
| 1 | [Magic](#magic) | Circuit layout editor |
| 2 | [SKY130 PDKs](#sky130-pdks) | Sky130nm libraries    |
| 3 | [Netgen](#netgen)      | Netlist generator     |
| 4 | [Xschem](#xschem)      | Schematic editor      |
| 5 | [Ngspice](#ngspice)     | SPICE simulation      |
| 6 | [Align](#align-tool)       | Analog netlist to GDS |
| 7 | [KLayout](#klayout)       | GDS viewer |

<a name="magic"></a> 
1. Magic

Magic is a VLSI Layout tool. To begin installing the open source tool, go to http://opencircuitdesign.com/magic/ and download some additional system packages

```
# install M4 preprocessor
  sudo apt-get install m4
# install tcsh shell
  sudo apt-get install tcsh
# install csh shell
  sudo apt-get install csh
# install Xlib.h
  sudo apt-get install libx11-dev
# install tck/tk libraries
  sudo apt-get install tcl-dev tk-dev
# install OpenGL interface (magic -d OGL)
  sudo apt install mesa-common-dev libgl1-mesa-dev libglu1-mesa-dev freeglut3-dev
# install ncurses
  sudo apt-get install libncurses-dev

optional
# install cairo graphics interface (magic -d XR)
$ sudo apt-get install libcairo2-dev
```
After installing the additional packages, use these commands to install magic
```
$  git clone git://opencircuitdesign.com/magic
$  cd magic
$	./configure
$  make
$  sudo make install
```
To view the magic application, type `magic -d XR` in the terminal

<img width="922" alt="magic " src="https://user-images.githubusercontent.com/64173714/218270647-44fd6e14-a885-4431-8df3-e4a74a8e2aa9.png">

<a name="sky130-pdks"></a> 
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

<a name="netgen"></a> 
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

<a name="xschem"></a> 
4. Xschem

XSCHEM is an open-source schematic capture tool for designing electronic circuits. It is available at https://github.com/StefanSchippers/xschem, and installation instructions are provided. 

Please make sure we have the following packages installed
``` 
sudo apt-get install flex
sudo apt-get install bison
sudo apt-get install libxpm-dev 
sudo apt-get install libx11-xcb-dev
sudo apt-get install libjpeg-dev
sudo apt-get install gawk
sudo apt-get install mawk
sudo apt-get install xterm
sudo apt-get install tcl-tclreadline
sudo apt-get install libxpm4
sudo apt-get install libx11-xcb-dev
sudo apt-get install libxcb1
sudo apt-get install libxrender-dev
sudo apt-get install libxrender1
sudo apt-get install libx11-dev
```
After installing the additional packages, use these commands to install xschem

```
git clone https://github.com/StefanSchippers/xschem.git xschem
cd xschem
./configure --prefix=/home/venkat 
make 
make install
```
After installing xschem, we should install xschem_sky130 in order to obtain XSCHEM symbol libraries for the Google-Skywater 130nm process design kit. It is available at https://github.com/StefanSchippers/xschem_sky130, and installation instructions are provided. 

```
cd xschem_library
git clone https://github.com/StefanSchippers/xschem_sky130.git xschem_sky130
cd xschem_sky130/
```
<img width="922" alt="xschem " src="https://user-images.githubusercontent.com/64173714/217904558-a577c075-d8a2-420f-b2c8-8a90bf9e345e.png">

<a name="ngspice"></a> 
5. Ngspice

ngspice is an open-source electronic circuit simulator that can be used for circuit analysis and simulation.

The following packages might be needed to be installed on your system
```
sudo apt-get install adms
sudo apt-get install autoconf
sudo apt-get install libtool
sudo apt-get install libxaw7-dev
sudo apt-get install build-essential
sudo apt-get install libc6-dev
sudo apt update
sudo apt upgrade
sudo apt-get install manpages-dev man-db manpages-posix-dev
sudo apt-get install libreadline6-dev
sudo apt-get update -y
```
To install ngspice go to https://github.com/ngspice/ngspice and follow this commands
```
 git clone https://github.com/ngspice/ngspice.git ngspice
 cd ngspice
 ./autogen.sh --adms
 mkdir release
 cd release
 ../configure  --with-x --with-readline=yes --disable-debug
 make
 sudo make install
 ```

<img width="921" alt="ngspice" src="https://user-images.githubusercontent.com/64173714/217905232-11985213-ed63-4449-9146-add781f941f9.png">

Verifying the installation of open_pdk

To create an initial working directory, copy the following files:
```
$ mkdir Lab1
$ cd Lab1
$ mkdir mag
$ mkdir netgen
$ mkdir xschem
$ cd xschem
$ cp /usr/local/share/pdk/sky130A/libs.tech/xschem/xschemrc .
$ cp /usr/local/share/pdk/sky130A/libs.tech/ngspice/spinit .spiceinit
$ cd ../mag
$ cp /usr/local/share/pdk/sky130A/libs.tech/magic/sky130A.magicrc .magicrc
$ cd ../netgen
$ cp /usr/local/share/pdk/sky130A/libs.tech/netgen//sky130A_setup.tcl .
```
<a name="cmos-inverter"></a>

## CMOS INVERTER

  A CMOS inverter is a type of digital circuit that converts a digital input signal from one state (e.g., 0 or 1) to its opposite state (e.g., 1 or 0). It is a fundamental component of digital electronics that is widely used in digital systems such as microprocessors, digital logic circuits, and digital-to-analog converters.

A CMOS inverter is typically made up of two complementary transistors, one p-type (pMOS) and one n-type (nMOS). The pMOS transistor pulls the output high, while the nMOS transistor pulls the output low. When the inverter's input is high (1), the nMOS transistor is turned on and the pMOS transistor is turned off, resulting in a low output. When the inverter's input is low (0), the pMOS transistor is turned on and the nMOS transistor is turned off, resulting in a high output.

One of the primary advantages of CMOS inverters is their low power consumption, as the transistors are only turned on when the input changes state, rather than constantly drawing current. Moreover, CMOS inverters are highly scalable and easily integrated into larger circuits, making them a popular choice for digital system design.    

## Creating Inverter Schematic using xschem
The schematic circuit is created by connecting components from the open_pdk library and performing dc analysis (VTC).

<img width="925" alt="inverter schematic xschem dc" src="https://user-images.githubusercontent.com/64173714/218326583-704c08c3-c866-4124-8ca1-b5e7feaadc3a.png">

DC analysis would be used to create a Voltage Transfer Characteristics (VTC) curve for the circuit. It will sweep the value of Vin from high to low to determine how the circuit works with respect to different voltage levels in the input. When the simulation is run, the plot shown below is obtained.

<img width="659" alt="dc" src="https://user-images.githubusercontent.com/64173714/218326601-d4310d78-607a-4e88-9e84-dff5820cebea.png">


The schematic circuit is created by connecting components from the open_pdk library and performing transient analysis.

<img width="923" alt="inverter schematic xschem trans" src="https://user-images.githubusercontent.com/64173714/218344215-2a247de5-f210-47c1-99bc-8888a5bd6973.png">


Transient analysis of a circuit is the simulation of the circuit's electrical behaviour over time, specifically its response to changing input signals.

<img width="727" alt="tran" src="https://user-images.githubusercontent.com/64173714/218344227-314b2287-d26d-4236-b5ca-c0029ae695a7.png">

```
** sch_path: /home/venkat/pd/Lab1/inverter_schematic.sch
**.subckt inverter_schematic vout vin vin
*.opin vout
*.ipin vin
*.ipin vin

XM2 vout vin Gnd Gnd sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1

XM11 vout vin Vdd Vdd sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1

Vdd VDD Gnd 1.8
.save i(vdd)
vin vin Gnd pulse(0 1.8 0 500ps 500ps 4ns 10ns)
.save i(vin)
**** begin user architecture code

** opencircuitdesign pdks install
.lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt
.tran 0.01n 50n
.save all
**** end user architecture code
**.ends

.GLOBAL Gnd
.GLOBAL Vdd
.GLOBAL VDD
.end
```

Post-layout

<img width="722" alt="magic 1" src="https://user-images.githubusercontent.com/64173714/218344231-fcd77e6c-8670-4c2f-a8ae-a870de63f9e4.png">



<img width="923" alt="magic 2" src="https://user-images.githubusercontent.com/64173714/219140660-02598962-f936-4bba-8afc-f307b721b9db.png">

```
extract do local
extract all
ext2spice lvs
ext2spice cthresh 0 rthresh 0
ext2spice
```

<img width="922" alt="magic 3" src="https://user-images.githubusercontent.com/64173714/219159239-36a32a10-2527-44e5-a1ce-72da45aa52ac.png">

```
* NGSPICE file created from inverter_schematic.ext - technology: sky130A

.subckt sky130_fd_pr__nfet_01v8_648S5X a_n73_n100# a_n33_n188# a_15_n100# a_n175_n274#
X0 a_15_n100# a_n33_n188# a_n73_n100# a_n175_n274# sky130_fd_pr__nfet_01v8 ad=2.9e+11p pd=2.58e+06u as=2.9e+11p ps=2.58e+06u w=1e+06u l=150000u
C0 a_n73_n100# a_15_n100# 0.16fF
C1 a_n33_n188# a_n73_n100# 0.03fF
C2 a_n33_n188# a_15_n100# 0.03fF
C3 a_15_n100# a_n175_n274# 0.08fF
C4 a_n73_n100# a_n175_n274# 0.11fF
C5 a_n33_n188# a_n175_n274# 0.30fF
.ends

.subckt sky130_fd_pr__pfet_01v8_XGS3BL a_n73_n100# a_15_n100# w_n211_n319# a_n33_n197#
+ VSUBS
X0 a_15_n100# a_n33_n197# a_n73_n100# w_n211_n319# sky130_fd_pr__pfet_01v8 ad=2.9e+11p pd=2.58e+06u as=2.9e+11p ps=2.58e+06u w=1e+06u l=150000u
C0 w_n211_n319# a_15_n100# 0.06fF
C1 a_n33_n197# a_n73_n100# 0.03fF
C2 a_n33_n197# a_15_n100# 0.03fF
C3 a_n73_n100# a_15_n100# 0.16fF
C4 w_n211_n319# a_n33_n197# 0.26fF
C5 w_n211_n319# a_n73_n100# 0.09fF
C6 a_15_n100# VSUBS 0.02fF
C7 a_n73_n100# VSUBS 0.02fF
C8 a_n33_n197# VSUBS 0.05fF
C9 w_n211_n319# VSUBS 1.07fF
.ends

.subckt inverter_schematic
XXM2 vout vin vout VSUBS sky130_fd_pr__nfet_01v8_648S5X
XXM11 vout vout XM11/w_n211_n319# vin VSUBS sky130_fd_pr__pfet_01v8_XGS3BL
C0 vout XM11/w_n211_n319# 0.24fF
C1 vout vin 0.68fF
C2 vin XM11/w_n211_n319# 0.08fF
C3 vin VSUBS 0.61fF
C4 vout VSUBS 1.41fF
C5 XM11/w_n211_n319# VSUBS 1.10fF
.ends
```

```
 netgen -batch lvs /home/venkat/pd/Lab1/inverter_schematic.spice /home/venkat/pd/Lab1/mag/inverter_schematic.spice

```
<img width="633" alt="netgen" src="https://user-images.githubusercontent.com/64173714/219203441-98bfa8e7-152f-4436-890c-21d92800c69b.png">

<img width="923" alt="post trans" src="https://user-images.githubusercontent.com/64173714/219517375-daba3f48-3746-4341-8161-8e23cd705934.png">





<a name="week-1"></a> 
## Week 1

<a name="align-tool"></a>
6. ALIGN tool

ALIGN is an open-source analogue circuit layout generator. The goal of ALIGN (Analog Layout, Intelligently Generated from Netlists) is to automatically translate an analogue circuit's unannotated (or partially annotated) SPICE netlist to a GDSII layout.
Prerequisites in the system are required for installation. 
`gcc >= 6.1.0` 
`python >= 3.7`

Use the following commands to install ALIGN tool

1.Setting the compiler paths 
```
sudo apt-get install libboost-all-dev
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
some packages are required to be installed in the system 
```
pip install --upgrade pip
pip install --upgrade setuptools
pip install wheel
sudo apt-get install python3-dev libffi-dev libssl-dev
pip install gdspy
pip install --no-binary :all: gdspy
pip install align
pip install --no-binary :all: align
```

4.Install ALIGN as a USER
```
pip install -v .
```

5. Install ALIGN as a DEVELOPER
```
pip install -e .
```
6.For ALIGN (C++) Extension developers
```
pip install setuptools wheel pybind11 scikit-build cmake ninja
pip install -v -e .[test] --no-build-isolation
pip install -v --no-build-isolation -e . --no-deps --install-option='-DBUILD_TESTING=ON'
```
Adapting ALIGN to Sky130 technology

Clone the following ALIGN-public directory repository
```
git clone https://github.com/ALIGN-analoglayout/ALIGN-pdk-sky130
```
move `SKY130_PDK` folder to `/home/venkat/pd/ALIGN-public/pdks`

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
 
<a name="klayout"></a> 
7. KLayout 

KLayout is a GDS and OASIS file viewer

```
sudo apt-get install qttools5-dev libqt5xmlpatterns5-dev qtmultimedia5-dev libqt5multimediawidgets5 libqt5svg5-dev
git clone https://github.com/KLayout/klayout
cd klayout/
./build.sh -prefix /usr/bin
```
