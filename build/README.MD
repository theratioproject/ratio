# <p style="text-align: center;" align="center">The Ratio Project Build Files</p>

This directory contains the platform dependent script that is used to setup the development environment to ensure easy building on various platforms. Each build script only work on the platform it is written for. 

The advantage of having different build file is to enable proper taming of each platform advantages for a better development and easy.

# Table of content
- [Naming Format](#naming-format)
- [Dist Folder](#dist-folder)
- [Script Flags](#script-flags)
    - [Configure](#configure)
    - [Install](#install)
    - [Build](#build)
    - [Uninstall](#uninstall)
    - [Debug](#debug)
    - [Architecture](#architecture)
        - [32 Bits](#32-bits)
        - [64 Bits](#64-bits)
    - [Keep](#keep)
    - [Help](#help)

## Naming Format

Each script has to follow the naming format. **Platform dash Build dot extension**. 

```
Platform-Build.ext
```

For The Operating System platform with variants like the *nix family or build file for backward incompatible version like Win.10 and Win.XP, **Platform dash osversion dash Build dot extension**.

```
Platform-System-Build.ext
```

Example: the folowing naming format for the linux, centos, windows platform

```
Linux-Build.sh
Linux-Centos-Build.sh
Windows-Build.bat
```

## Dist Folder

The dist folder will be used for holding binaries and temporary files generated or used during the build process. The dist folder is not meant to be commited to the repo, but used locally. 

## Script Flags

This are flags that can be used with the scripts to perform various build operations.

### Configure

Each build file will have the configure flags `-c` and `--configure` to prepare the system for building the project. 

The configuration function is to check if the platform has the neccasary toolchains to build the project if it does not,the system package manager to is used download the tools. If the system does not have package manager like the windows platform, an archive of tools can be downloaded from trusted source.

### Install

The install flags `-i` and `--install` will be used to build a distributable version of the project in the decided installation folder. The build will have no low level debugging feature but can be distributed. 

### Build 

The install flags `-b` and `--build` will be used to build a distributable version of the project in the folder specified after the flag. The build will have no low level debugging feature but can be distributed. 

### Uninstall

The install flags `-u` and `--uninstall` will be used to uninstalled the built project base on the version in the build script. 

### Debug

The install flags `-d` and `--debug` will be used to build a distributable version of the project in the parent directory of the project. The build will have full low level debugging feature with lot of flags to fully debug and trace the project at all stages.

### Architecture

There will be flags providing the developer with the option of what architectural version of the project to be build. Not all platform support the 32 bit version such as the MAC OSX, so the architecture build flag depends on the platform.

#### 32 Bits

The flags `x86` and `--32-bits` will be used to build 32 bits version of the project.

#### 64 Bits

The flags `x64` and `--64-bits` will be used to build 64 bits (x86_64) version of the project.

### Keep

The flags `-k` and `--keep` will determine if the temporary *./dist/* folder should be deleted after the build is successful.

### Help

The flags `-h` and `--help` will display the help message containing the flags that can be sent to the scripts. According to the flags above the help message is 

```
[FLAGS] :
    -c --configure  configure your system for ratio successful build
    -i --install    install ratio on your system
    -b --build      build ratio in the folder after the arg
    -u --uninstall  uninstall ratio from your system
    -d --debug      create a debugable version in ..\..\ source directory
    x86 --32-bits   build 32 bit version of ratio
    x64 --64-bits   build 64 bit version of ratio
    -k --keep       keep the */dist/ folder(s) in source tree
    -h --help       print this help message
```