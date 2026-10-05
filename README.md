What is Ghidra Staging?
-----------------------

**Ghidra Staging** is an unofficial testing area of [Ghidra](https://ghidra-sre.org). It contains bug fixes and features, which have not been integrated into the development branch yet. The idea of Ghidra Staging is to provide experimental or maybe useful features faster to end users and to give developers the possibility to discuss and improve their patches upstream before they are integrated into or handled differently on the master branch. Ghidra Staging also tries to keep patches building against latest upsteam master branch. Additionally it helps to detect upstream PRs that have become OBE or have already been fixed.

**Note:** Ghidra Staging is designed for rapid testing and user feedback of upstream Pull Requests. For official architectural discussions, please open an issue, discussion, or PR directly on the [Official NSA Ghidra Repository](https://github.com/NationalSecurityAgency/ghidra) (see Contributing).

Downloading
-----------

Current builds of Ghidra Staging are available for download:
1. Go to https://github.com/jobermayr/ghidra-staging/actions/workflows/build-ghidra-multi-platform-artifact.yml
2. Then choose first item of Build Ghidra Staging
3. On bottom are artifacts for Linux, macOS and Windows

Building
--------

Ghidra Staging is maintained as a set of patches which has to be applied on top of the development branch and thus sometimes patches are not exactly what they were when submitted as PR. In order to build Ghidra Staging, the first step is to setup a build environment for Ghidra, including all required dependencies.

A general usecase for building is:
1. git clone https://github.com/NationalSecurityAgency/ghidra.git
2. git clone https://github.com/jobermayr/ghidra-staging.git
3. cd ghidra
4. git am -3 ../ghidra-staging/*.patch
5. gradle -I gradle/support/fetchDependencies.gradle init
6. [LC_MESSAGES=en] gradle assembleAll
7. cd build/dist/ghidra_xx.x_DEV

Contributing
------------

Ghidra Staging includes patches from https://github.com/NationalSecurityAgency/ghidra/pulls. To get a patch included just push it to your fork and create a PR to upstream Ghidra.

Patches can occasionally break the runtime until the issue is detected and the patch fixed or moved to bad/. On runtime issues keep in mind to compare results of upstream master and Ghidra Staging. If the issue doesn't exist on upstream master try to bisect the bad commit and report it directly to the corresponding upstream pull request.
