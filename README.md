# Galaxia - Mockgal

This repository holds a fork of the "Galaxia" synthetic galaxy modeling software
([Sharma et al., 2011](https://ui.adsabs.harvard.edu/abs/2011ApJ...730....3S))
created to facilitate the support of modern isochrone grids and
synthetic photometry within the original models, in particular magnitudes in
the [CASTOR](https://www.castormission.org) bands.
This fork was designed to be used in
[MockGal](https://github.com/nmdickson/MockGal).

This repo is forked from Galaxia version 0.7.2, as found
at [sourceforge](https://galaxia.sourceforge.net).

## Installation instructions

(This version has only been tested on Linux but should also work on MacOS)

1. Download (and unpack if necessary) the software and enter the directory.
Make sure that the "GalaxiaData" subdirectory has also been downloaded.
```bash
# tar -zxvf galaxia-mockgal.tar.gz
cd galaxia-mockgal
```

2. Configure and automatically create the make file. The prefix directory is
where the package will be installed (the executable under $prefix/bin). The
data directory should point to where the Galaxia data directory will be. This
does not need to be within the package source.
```bash
./configure --prefix=/home/user/galaxia --datadir=/home/user/galaxia/GalaxiaData
```

3. Make/compile.
```bash
make
make install
```

4. Make sure the `datadir` specified is populated (if given a separate location
above).
```bash
cp -r ./GalaxiaData /home/user/galaxia/GalaxiaData
```

5. If not already in your path, add the executable directory to the path, in
your `~/.bashrc` or other relevant login scripts.
```bash
export PATH=$PATH:/home/user/galaxia/bin
```

6. The first time Galaxia is run, you must generate the BHtree files, either
with or without warp and flare. This will take a long time, but only needs to
be run once. See the source paper for more details on this.
```bash
galaxia -s warp
# galaxia -s nowarp
```

7. Place any extra isochrones you might want to use (other than those included
in the original software) into the `$datadir/Isochrones/padova`. Make sure they
also have a `IsoFileDescriptor.txt` file included and match the expected
filename format.
(If the isochrone formatter hasn't yet been included in `MockGal`, just ask me
and I can provide some grids for use here).

For more installation and usage instructions, see the
[original documentation](https://galaxia.sourceforge.net/Galaxia3pub.html).
This fork of galaxia can also be used entirely through the `MockGal` library,
which will wrap calls around this executable, using the directories specified
above.


The original README is reproduced below:

# Original README

--------------------------------------------------------------

Galaxia is a code for synthetic modelling of the Milky Way
Copyright (C) 2012  Sanjib Sharma, Joss Bland-Hawthorn

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as
published by the Free Software Foundation, either version 3 of the
License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

--------------------------------------------------------------

For installation and usage see the html guide 
firefox GalaxiaData/docs/index.html

The output data is in EBF file format.
Libraries for reading and writing data in EBF file format 
are available at http://ebfformat.sourceforge.net.  
Currently supported languages are
C, C++, Java, Fortran, Python, IDL and Matlab. 

The data for Bullock and Johnston models 
are not included in the standard distribution so as to 
reduce the size of the distribution. 
This can be downloaded from 
http://www.physics.usyd.edu.au/~sanjib/code/bj.tar.gz

These can be easily plugged in by downloading them separately and 
then putting them in GalaxiaData/nbody1/ folder. 
cd GalaxiaData/nbody1
tar -zxvf bj.tar.gz 

Presently for inquiries mail me at bug.sanjib at gmail .
Comments, criticism, bug report and feedback are most welcome. 

--------------------------------------------------------------

