# SPLIB

Sofa Python Library

This library should contains python code that could be useful for use with Sofa.
Historically SPLIB was part of a much larger framework called STLIB, but since the release of SofaPython3 it is now hosted as 
a separated package. 

# Versions
current: Sofa/master SofaPython3/master SPLIB/master 
deprecated: Sofa/21.01  SofaPython/21.01 the latest now version of SPLIB is available at: https://github.com/SofaDefrost/STLIB/releases/tag/SofaPython2-latest

# To build SPLIB
There are two ways to compile plugins for SOFA. The most commonly used is the __In-tree build__, i.e. building the plugin while building SOFA from its sources on github. The second option, which is less commonly used but provides more flexibility, is the __Out-of-tree build__, where SOFA is pre-built and installed (from sources or by downloading its binaries) and the plugin is compiled as a standalone module, against the SOFA libraries
 
## In-tree build
First you need to have [SOFA](https://github.com/Sofa-framework/sofa) on your machine, since to build STLIB you will need to build it through SOFA.

`git clone https://github.com/sofa-framework/sofa.git`

Then clone SPLIB

`git clone https://github.com/SofaDefrost/SPLIB.git`

In the configurations of SOFA build settings, set `PLUGIN_SOFAPYTHON3` to `ON` and `SOFA_EXTERNAL_DIRECTORIES` to the absolute path of SPLIB `your_path/STLIB`

Then build SOFA

Now you should be able to use `import splib` in python from inside SOFA (running the .py from runSofa)

## Out-of-tree build 
Either Download the latest binary release or build and install from the sources, as described on [sofa-framework's download page](https://www.sofa-framework.org/download/).
Remember the installation directory, you will need it later on.

Then clone SPLIB

`git clone https://github.com/SofaDefrost/SPLIB.git`

create a build/ folder next to your SPLIB repository's directory, and in CMake-gui, set the source folder with <Browse Source>, and the newly created build folder with <Browse Build>

In the configurations of SPLIB build settings, add the following CMake entries:
`CMAKE_PREFIX_PATH` = `SOFA_INSTALLATION_DIRECTORY`
`PLUGIN_SOFAPYTHON3` = `ON`

Configure, Generate, then build AND install the plugin. During the install step, SPLIB will be deployed in SOFA's installation directory, and you will be able to use `import stlib` in python from inside SOFA (running the .py from runSofa)
