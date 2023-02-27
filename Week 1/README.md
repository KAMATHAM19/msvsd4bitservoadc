
<a name="week-1"></a> 
## Week 1

| | Tools | Description|
|--|--|--|
| 1 | [Align](#align-tool)       | Analog netlist to GDS |
| 2 | [KLayout](#klayout)       | GDS viewer |


<a name="align-tool"></a>
1. ALIGN tool

ALIGN is an open-source analogue circuit layout generator. The goal of ALIGN (Analog Layout, Intelligently Generated from Netlists) is to automatically translate an analogue circuit's unannotated (or partially annotated) SPICE netlist to a GDSII layout.
Prerequisites in the system are required for installation. 
`gcc >= 6.1.0` 
`python >= 3.7`

Use the following commands to install ALIGN tool
```
# Setting the compiler paths 
export CC=/usr/bin/gcc
export CXX=/usr/bin/g++
# Clone the ALIGN source code to your local environment
git clone https://github.com/ALIGN-analoglayout/ALIGN-public
cd ALIGN-public
# Create a Python virtualenv
sudo apt install python3.10-venv
python3 -m venv general
source general/bin/activate
python3 -m pip install pip --upgrade
# some packages are required to be installed in the system 
sudo apt-get install libboost-all-dev
sudo apt install lp-solve
pip install --upgrade pip
pip install --upgrade setuptools
pip install wheel
sudo apt-get install python3-dev libffi-dev libssl-dev
# Install ALIGN as a USER
pip install -v .
# Install ALIGN as a DEVELOPER
pip install -e .
# For ALIGN (C++) Extension developers
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
2. KLayout 

KLayout is a GDS file viewer

```
sudo apt-get install qttools5-dev libqt5xmlpatterns5-dev qtmultimedia5-dev libqt5multimediawidgets5 libqt5svg5-dev
git clone https://github.com/KLayout/klayout.git
cd klayout/
./build.sh -prefix /usr/bin
```
