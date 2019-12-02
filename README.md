<!-- ** DOCUMENTATION STEPS ** -->
<!-- STEP1: Update README.md -->
<!-- STEP2: Update CHANGELOG.md -->

<!-- ** PUBLISHING STEPS ** -->
<!-- STEP1: Update version in the Features section of the README.md file -->
<!-- STEP2: Change the [Unreleased] section by the version section of the CHANGELOG.md file and update its repository link -->
<!-- STEP3: Add a version comparison link to the CHANGELOG.md file -->
<!-- STEP4: Update version in the "version" field of the package.json file -->

<!-- TODO: Add a 'make clean' related command. -->

# ESP32 project manager for Visual Studio Code

ESP32 project manager for Visual Studio Code. Setup, build, flash and monitor ESP32 applications.

----------

## Features [Unreleased]

- `make` commands execution available for the integrated VSC terminal.

- Standard project structure for the use of this extension.\
This project structure allows the use of more than one application program or 'sub-project' that may have more than one entry point.\
The project structure is as follows:

>project (Project folder)
>- .gitignore (Git file) [Tracked by Git]
>- Makefile (ESP32 Makefile file) [Tracked by Git]
>- sdkconfig (ESP32 config file) [Ignored by Git]
>- sdkconfig.defaults (ESP32 default config values file) [Tracked by Git]
>- sdkconfig.old (Previous ESP32 config file) [Ignored by Git]
>>.vscode (VSC config folder)
>>- .gitignore (Git file) [Tracked by Git]
>>- browse.c_cpp.db* (VSC database files) [Ignored by Git]
>>- c_cpp_properties.json (VSC C/C++ config file) [Ignored by Git]
>>- settings.json (VSC workspace config file) [Ignored by Git]
>
>>build (ESP32 generated files when building) [Ignored by Git]
>
>>components (ESP32 user-defined components folder)
>>- .gitignore (Git file) [Tracked by Git]
>
>>main (ESP32 application container)
>>- .gitignore (Git file) [Tracked by Git]
>>- component.mk (ESP32-PM generated main pseudo-component makefile) [Ignored by Git]
>>- main.cpp (ESP32-PM generated  main entry point) [Ignored by Git]
>>>src (ESP32-PM sub-projects container)
>>>>sub_project_1 (ESP32-PM sub-project application container)
>>>>- main_1_sub_proj_1 (ESP32-PM sub-project entry point) [Tracked by Git]
>>>>- main_..._sub_proj_1 (ESP32-PM sub-project entry point) [Tracked by Git]
>>>>- main_n_sub_proj_1 (ESP32-PM sub-project entry point) [Tracked by Git]
>>>
>>>>sub_project_... (ESP32-PM sub-project application container)
>>>>- main_1_sub_proj_... (ESP32-PM sub-project entry point) [Tracked by Git]
>>>>- main_...\_sub_proj\_... (ESP32-PM sub-project entry point) [Tracked by Git]
>>>>- main_n_sub_proj_... (ESP32-PM sub-project entry point) [Tracked by Git]
>>>
>>>>sub_project_m (ESP32-PM sub-project application container)
>>>>- main_1_sub_proj_m (ESP32-PM sub-project entry point) [Tracked by Git]
>>>>- main_..._sub_proj_m (ESP32-PM sub-project entry point) [Tracked by Git]
>>>>- main_n_sub_proj_m (ESP32-PM sub-project entry point) [Tracked by Git]

### Supported OS

- **Linux** (tested on **Linux Mint**)
- **Windows** (tested in **Windows 7** and **Windows 10**)

### Commands

- `ESP32-PM: Create project` [ **Windows**, **Linux** ]: Create a new ESP32 project.
- `ESP32-PM: Set ESP-IDF API folder` [ **Windows**, **Linux** ]: Set the ESP-IDF API folder to be used with the active project.
- `ESP32-PM: Set 'msys32' folder` [ **Windows** ]: Set the 'msys32' folder to be used with the active project.
- `ESP32-PM: Set 'xtensa-esp32-elf' folder` [ **Linux** ]: Set the 'xtensa-esp32-elf' folder to be used with the active project.
- `ESP32-PM: Defconfig` [ **Windows**, **Linux** ]: Run the `make defconfig` command, which applies the default configuration values defined in the `sdkconfig.defaults` file.
- `ESP32-PM: Menuconfig` [ **Windows**, **Linux** ]: Run the `make menuconfig` command, which shows the configuration interface for a ESP32 project.
- `ESP32-PM: Build` [ **Windows**, **Linux** ]: Run the `make -j all` command, which builds the active sub-project using the active file as its entry point.
- `ESP32-PM: Flash` [ **Windows**, **Linux** ]: Run the `make flash` command, which flashes a built sub-project using a previously selected serial port.
- `ESP32-PM: Monitor` [ **Windows**, **Linux** ]: Run the `make monitor` command, which opens a terminal using a previously selected serial port.
- `ESP32-PM: Flash & Monitor` [ **Windows**, **Linux** ]: Run the `make flash monitor` command, which flashes a built sub-project and opens a terminal using a previously selected serial port.
- `ESP32-PM: Clean` [ **Windows**, **Linux** ]: Run the `make clean` command, which removes built files.
<!-- - `ESP32-PM: Remove auto-generated files` [**Windows**]: Remove files auto-generated by this extension. -->

----------

## Requirements

### For Windows

The following elements are required to be previously obtained:

1. The [Espressif 'msys32' folder](https://dl.espressif.com/dl/esp32_win32_msys2_environment_and_toolchain-20190611.zip) unzipped in a folder located in a path with no spaces.
2. The ESP-IDF by cloning [its repository](https://github.com/espressif/esp-idf) recursively (git clone --recursive \<repo\>) in a folder located in a path with no spaces. You could use any version.

### For Linux

The following elements are required to be previously obtained:

1. Installing the [prerequisites to compile with the ESP-IDF in Linux](https://docs.espressif.com/projects/esp-idf/en/latest/get-started-legacy/linux-setup.html#install-prerequisites).
3. The Espressif 'xtensa-esp32-elf' folder for [64-bit architecture](https://dl.espressif.com/dl/xtensa-esp32-elf-gcc8_2_0-esp32-2019r1-linux-amd64.tar.gz) or [32-bit architecture](https://dl.espressif.com/dl/xtensa-esp32-elf-gcc8_2_0-esp32-2019r1-linux-i686.tar.gz) unzipped in a folder located in a path with no spaces.
3. The ESP-IDF by cloning [its repository](https://github.com/espressif/esp-idf) recursively (git clone --recursive \<repo\>) in a folder located in a path with no spaces. You could use any version.

----------

## Usage

After meeting the requirements and installing this extension, you could follow the steps below:

### 1. Create a new project:

- Create a new project with the `ESP32-PM: Create project`.

### 2. Set important folders for the project:

- Set the ESP-IDF API folder with the `ESP32-PM: Set ESP-IDF API folder` command.
- For **Windows**, set the 'msys32' folder with the `ESP32-PM: Set 'msys32' folder` command.
- For **Linux**, set the 'xtensa-esp32-elf' folder with the `ESP32-PM: Set 'xtensa-esp32-elf' folder` command.

### 4. Set the project configuration:

You could run either the `ESP32-PM: Defconfig` or the `ESP32-PM: Menuconfig` command.

### 4. Build an application:

Use the `ESP32-PM: Build` command, which corresponds to the `make all` command. This command should be executed with an entry point file as the active VSC file.

Any entry point file should be contained in a sup-project folder and its name should start with the `main` string. This entry point could use the `.c` or the `.cpp` extension.

### 4. Execute other regular `make` commands (flash, monitor and clean):

These commands are often used with ESP32 projects based on GNU Make. They can be used with their corresponding extension command as long as the current workspace is an ESP32-PM project.

----------

## Known Issues

[Known issues](https://github.com/mrverdant13/esp32-pm-vsc-extension/issues).

----------

## Changelog

[Changelog](https://github.com/mrverdant13/esp32-pm-vsc-extension/blob/develop/CHANGELOG.md).

----------

## Licence

    Copyright (c) 2019 Karlo Fabio Verde Salvatierra

    All rights reserved.

    MIT License

    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.