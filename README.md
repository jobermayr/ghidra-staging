What is Ghidra Staging?
-----------------------

**Ghidra Staging** is an unofficial testing area of https://ghidra-sre.org. It contains bug fixes and features, which have not been integrated into the development branch yet. The idea of Ghidra Staging is to provide experimental or maybe useful features faster to end users and to give developers the possibility to discuss and improve their patches before they are integrated into the main branch. Ghidra Staging also tries to keep patches building against latest master branch.

Building
--------

Ghidra Staging is maintained as a set of patches which has to be applied on top of the development branch and thus sometimes patches are not exactly what they were when submitted as pull request. In order to build Ghidra Staging, the first step is to setup a build environment for Ghidra, including all required dependencies.

A general usecase for a quick try on Linux is to
- wget https://github.com/NationalSecurityAgency/ghidra/archive/refs/heads/master.zip
- unzip -x master.zip
- wget https://github.com/jobermayr/ghidra-staging/archive/refs/heads/master.zip
- unzip -x master.zip.1
- cd ghidra-master
- patch -p1 <../ghidra-staging-master/*.patch
- gradle -I gradle/support/fetchDependencies.gradle init
- [LC_MESSAGES=en] gradle buildGhidra
- cd build/dist/ghidra_xx.x_DEV

Keep in mind to clone Ghidra and Ghidra Staging instead of downloading zip-Files.

Contributing
------------

Ghidra Staging includes patches from https://github.com/NationalSecurityAgency/ghidra/pulls. To get a patch included just push it to your fork and create a pull request to upstream Ghidra.

On runtime issues keep in mind to compare results of plain master and Ghidra Staging. If the issue doesn't exist on master try to bisect the bad commit and report it directly to the corresponding upstream pull request.
