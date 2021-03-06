Macromaker README file
======================

Macromaker is a python application with an easy interface for the construction of a quaternary structure, given a folder with interaction pairs of terciary structures in PDB format. Other freatures of macromaker are:

- Save / restore the executrion of a macrocomplex construction.
- Import into a pyhon project instead of using it as standalone application. 

Requeriments
============

There are some requeriments for using macromaker. As macromaker performs structural alignment, and can reduce energy of the final result, we need some specific software installed:

- [Python 3](https://www.python.org/) (https://www.python.org/)
- [STAMP](http://www.compbio.dundee.ac.uk/downloads/stamp/) (http://www.compbio.dundee.ac.uk/downloads/stamp/)
- [AmberTools 18](http://ambermd.org/AmberTools.php) (http://ambermd.org/AmberTools.php)

Third-party modules
===================

During the realization of the project, we used several python modules fount in http://pypi.org/. These modules are:

- [biopython](https://pypi.org/project/biopython/)
- [python-Levenshtein](https://pypi.org/project/python-Levenshtein/)
- [numpy](https://pypi.org/project/numpy/)

We have used some third party modules from github projects, that are not listed in setup.py, those are:

- [pdbremix/pdbstrip](https://github.com/boscoh/pdbremix) (https://github.com/boscoh/pdbremix)
- [center_of_mass](https://github.com/rasbt/protein-science/tree/master/scripts-and-tools/center_of_mass) (https://github.com/rasbt/protein-science/tree/master/scripts-and-tools/center_of_mass)
- [python-mkdoc](https://github.com/kata198/python-mkdoc) (https://github.com/kata198/python-mkdoc)


Installation
============

The easiest way to install macromaker is to download the repo and install via setup.py with:

    sudo python setup.py install

Usage
===== 

## macromaker

Macromaker is a very simple and intuitve quaternary structure builder, given a set of interaction pairs of terciary structures. 

The simples way to run will be:

    macromaker -i /path/to/pdb/folder/

This will produce a file named _macrocomplex.pdb_ in the current path.

If we want to specify the output we can run macrocomplex with -o argument:

    macromaker -i /path/to/pdb/folder/ -o /other/path/macrocomplex_name

Another interesting thing about macromaker is that it can build infinity structures, for avoiding that non-sense, a max of __200 chains__ is allower. Nevertheless, we can change that value with -m option.

    macromaker -i /path/to/infinite/pdb/ -m 300

Other feature of macromaker is that it can clean the original pdb files before starting to build the complex. __By default, waters and other hetero atoms are not removed.__

    macromaker -i /path/to/pdb/folder/ -c

The last awsome feature of macromaker is that it can pause and resume the execution of macrocomplex build process.

The creation of a rescue file is done automaticaly when canceling the execution of the program with __Ctrl+C__. This will create a _rescue.rtk_ file in the current path.

To resume the execution of a previous build, you can call macromaker with option -r.

    macromaker -i /path/to/pdb/folder/ -r

This will find a file called _rescue.rtk_ to use it as an input to resume the execution.

## macromaker-gui (unestable)

This is the graphical interface for macromaker. It can do the same as the non graphic interface. And as it is such an intuitive interface, we think that no usage is required.

__Due to deadlines, the gui has not been tested a lot.__

## correct-pdb

The main workflow of macromaker uses STAMP to do structural alignment.

During the proces of developing this project, we find out that some PDB broke our software. More concretly, STAMP is the responsable, because looking at the source code, we found out that STAMP looks for CA in specific position in PDB files.
  
So, some old PDB files that have right-justified the column of atom type, make our project crash. To bypass this, we created this script that reads a folder with PDB files, left-justify the atom type column.

    correct-pdb -i /path/to/pdb/folder/

This will create new PDB files and remove the old ones, so it seems to be a good idea to have a fisrt look at those PDBs before running macromaker...

Authors
=======

The project has been carried out by a group of students of the [Universitat Pompeu Fabra](https://www.upf.edu/)'s [MCs in Bioinformatics for Heath Sciences](https://www.upf.edu/web/bioinformatics/). These guys are:

- **[Medel, Brian](https://www.linkedin.com/in/brian-medel-lacruz-480327172/)**
- **[Pradas, Gerard](https://www.linkedin.com/in/gpradas/)**
- **[Velasco, Daniel](https://www.linkedin.com/in/daniel-velasco-guisado-670243182/)**


License
=======

Macromaker is open-source software licensed under the [GNU GLPv3](https://opensource.org/licenses/GPL-3.0).
