# msvsd4bitservoadc


# Table of Contents
* [Week 0](# week-0)
  * Prerequisite
  * Open Source tools 



# Week 0

Prerequisite

1. Oracle Virtual box(https://www.virtualbox.org/wiki/Downloads)
2. Linux ubuntu(https://ubuntu.com/download/desktop)
3. Git

``` 
 sudo apt-get install git
 ```

Open Source tools

1. Magic

```
$  git clone git://opencircuitdesign.com/magic
$  cd magic
$	 ./configure
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
