# SPLIB

Sofa Python Library

This library should contains python code that could be useful for use with Sofa.

```python
```

////////////////////////// OUTDATED DOCUMENTATION...... 

# To build STLIB
There are two ways to compile plugins for SOFA. The most commonly used is the __In-tree build__, i.e. building the plugin while building SOFA from its sources on github. The second option, which is less commonly used but provides more flexibility, is the __Out-of-tree build__, where SOFA is pre-built and installed (from sources or by downloading its binaries) and the plugin is compiled as a standalone module, against the SOFA libraries
 
## In-tree build
First you need to have [SOFA](https://github.com/Sofa-framework/sofa) on your machine, since to build STLIB you will need to build it through SOFA.

`git clone https://github.com/sofa-framework/sofa.git`

Then clone STLIB

`git clone https://github.com/SofaDefrost/STLIB.git`

In the configurations of SOFA build settings, set `PLUGIN_SOFAPYTHON` to `ON` and `SOFA_EXTERNAL_DIRECTORIES` to the absolute path of STLIB `your_path/STLIB`

Then build SOFA

Now you should be able to use `import stlib` in python from inside SOFA (running the .py from runSofa)
## Out-of-tree build 
Either Download the latest binary release or build and install from the sources, as described on [sofa-framework's download page](https://www.sofa-framework.org/download/).
Remember the installation directory, you will need it later on.

Then clone STLIB

`git clone https://github.com/SofaDefrost/STLIB.git`

create a build/ folder next to your STLIB repository's directory, and in CMake-gui, set the source folder with <Browse Source>, and the newly created build folder with <Browse Build>

In the configurations of STLIB build settings, add the following CMake entries:
`CMAKE_PREFIX_PATH` = `SOFA_INSTALLATION_DIRECTORY`
`PLUGIN_SOFAPYTHON` = `ON`
`SOFA_BUILD_METIS` = `ON`

Configure, Generate, then build AND install the plugin. During the install step, STLIB will be deployed in SOFA's installation directory, and you will be able to use `import stlib` in python from inside SOFA (running the .py from runSofa)
