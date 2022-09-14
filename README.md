# LIGGGHTS-PUBLIC-TACC_LS6_Installation
This repository provides the guidance to install LIGGGHTS-PUBLIC on Lonestar6 (ls6) at TACC, University of Texas Austin. <br/>
It requires a locally installed VTK. We use vtk-8.2 here. (NOTE: vtk-9.2-rc failed to compile with LIGGGHTS-PUBLIC.) <br/>
1. git clone LIGGGHTS.
```
git clone https://github.com/CFDEMproject/LIGGGHTS-PUBLIC.git
```
2. 
```
cd LIGGGHTS-PUBLIC
cd src
```
3. Copy the Makefile.ls6 from this repository to src/MAKE
4. Install VTK-8.2
```
wget https://www.vtk.org/files/release/8.2/VTK-8.2.0.tar.gz
tar -xvf VTK-8.2.0.tar.gz
cd vtk-8.2
mkdir -p build
cd build
ccmake ../
```
5. ccmake will invoke the GUI to adjust parameters for VTK. Make sure to turn USE MPI to "ON".
6. Modify the installation path in cmake_install.cmake because we don't have admin on HPCs.
7. After *make* and *make install*, vtk libs and include files would be installed in the path you specifiy in cmake_install.cmake.
```
make
make install
```
Now, vtk-8.2 will be installed. <br/>
8. Go back to LIGGGHTS-PUBLIC/src/MAKE, and modify the environment variables VTK_LIB, VTK_INC, VTC_PATH. <br/>
9. Go to LIGGGHTS-PUBLIC/src
```
make ls6
```
10. You should find the executable lmp_ls6 under LIGGGHTS-PUBLIC/src.

