[![Licensed under the MIT License](https://img.shields.io/badge/License-MIT-blue.svg)](https://github.com/microsoft/spatialaudio-unity/blob/master/LICENSE)

# Introduction 
This repository provides plugins and tools for integrating spatial audio and acoustics into your Unity 3D applications and games. This includes:
- A HoloLens 2 spatializer plugin which uses [Windows Sonic API](https://docs.microsoft.com/en-us/windows/win32/coreaudio/spatial-sound) to enable hardware offload of spatial audio processing, freeing up the CPU for your application.
- A sample Unity application that demonstrates proper usage of the HoloLens 2 spatializer plugin.
- Source code for the [Project Acoustics](http://aka.ms/acoustics) spatializer plugin.

# Getting started with Spatial Audio for Unity on HoloLens 2
Cloning this repository is not required to start using the Microsoft Spatializer in your Unity project. Visit our [documentation](https://docs.microsoft.com/en-us/windows/mixed-reality/spatial-sound-in-unity) for instructions on integrating the Microsoft Spatializer into your Unity project. For a more in-depth exploration of spatial audio, check out the [learning module](https://docs.microsoft.com/en-us/windows/mixed-reality/unity-spatial-audio-ch1). If you'd like to build the plugin yourself, see below.

## Required Software

| ![Windows Logo](Documentation/Images/128px_Windows_logo.png)<br>[Windows SDK 18362+](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) | ![VS Logo](Documentation/Images/128px_Visual_Studio_2019.png)<br>[Visual Studio 2019](https://visualstudio.microsoft.com/vs/) | ![CMake Logo](Documentation/Images/128px_CMake_logo.png)<br>[CMake](https://cmake.org/) | ![Unity3D logo](Documentation/Images/128px_Official_unity_logo.png)<br>[Unity 2019](https://unity.com/releases/2019-2?_ga=2.114950222.898171561.1571681098-1938809356.1563129846) | ![Python Logo](Documentation/Images/128pv_python_logo.png)<br>[Python 3+](https://www.python.org/downloads/) |
| :---: | :---: | :---: | :---: | :---: |
| Windows 10 May 2019 Update SDK to build the spatializer plugin.<br>Plugin will run on Windows 10 Fall Creator's update and higher and on HoloLens 2. | Visual Studio is used for code editing, deploying and building UWP app packages | CMake is required for generating Visual Studio 2019 projects | Unity 2019 is required to build the spatializer plugin package.<br>Plugin can be used on Unity 2018 LTS and higher versions. | Helper scripts for build and packaging use Python 3 and higher. 

### Branch Guide
- Master branch is used for building release candidates and official releases. Direct pull requests into master are not allowed.
- Develop branch is used for staging ongoing work for the next official release and merged with master after extensive review and testing. Direct pull requests into develop branch are not allowed.
- Use feature branches to bringup individual features. Once a feature is ready and tested a pull request can merge it into develop branch.

### Clone the Repository
`git clone https://github.com/microsoft/spatialaudio-unity.git --recurse-submodules`

If you forget to include submodules when cloning, add them with `git submodule update --init --recursive`

### Build Status
| Build | Branch | Status |
| :----:| :----: | :----: |
| Release | [master](https://github.com/microsoft/spatialaudio-unity/tree/master) | [![Release Build Status](https://dev.azure.com/microsoft/Analog/_apis/build/status/mixedreality/spatialaudio/unity/microsoft.spatialaudio-unity?branchName=master)](https://dev.azure.com/microsoft/Analog/_build/latest?definitionId=46637&branchName=master) |
| Validation | [develop](https://github.com/microsoft/spatialaudio-unity/tree/develop) | [![Validation Build Status](https://dev.azure.com/ms/spatialaudio-unity/_apis/build/status/microsoft.spatialaudio-unity?branchName=develop)](https://dev.azure.com/ms/spatialaudio-unity/_build/latest?definitionId=304&branchName=develop) |


### Local Build
- Launch "Developer Command Prompt for Visual Studio 2019".
- Switch directory to the root of your Git enlistment.
- Run the CMake script to generate Visual Studio 2019 projects:
  `python3 Tools\runcmake.py`
- Run the build script to build all flavors:
  `python3 Tools\build.py`
- To generate the Unity package:
  `python3 Tools\unity_package.py -u "c:\Program Files\Unity\Hub\Editor\2019.1.3f1\Editor" -v 0.1.0`
- To generate the NuGet package:
  `python3 Tools\nuget_package.py -v 0.1.0`

### Artifacts
- Build produces a NuGet package and a Unity asset package.
- Official Unity and NuGet packages are under [releases tab](https://github.com/microsoft/spatialaudio-unity/releases)
- NuGet package is also released to [NuGet](https://nuget.org).
