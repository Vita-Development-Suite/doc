# Vita Development Suite

Development updates can be found on our [forum](https://forum.devchroma.nl/index.php/topic,332.0.html).

## Prerequisites

Install the following:

1. PlayStation®Vita Programmer Tool Runtime Library 3.570
2. Publishing Tools for PlayStation(R)Vita 2.31
3. SNC Toolchain for PSP2 3.570

Set the environment variable `SCE_ROOT_DIR` to the root of your Publishing Tools installation directory, such that the following path exists:

```
$SCE_ROOT_DIR/PSP2/Tools/Publishing Tools
```

Set the environment variable `SCE_PSP2_SDK_DIR` to the root of your SDK installation directory, such that the following paths exist:

```
$SCE_PSP2_SDK_DIR/host_tools
$SCE_PSP2_SDK_DIR/target
```

## Installation

Vita Development Suite releases are available from our [file host](https://bin.shotatoshounenwachigau.moe/vdsuite). Development builds are available as GitHub Actions workflow artifacts. Download and extract the components you want to use into your SDK installation directory.

### Installing GCC (optional)

1. Download and install the [GNU Arm Embedded Toolchain](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads).
2. Replace `bin/arm-none-eabi-ld` and `arm-none-eabi/bin/ld` with `psp2ld`.
3. Add `bin` to your `PATH` environment variable.

## Components

### PSP2 CMake Toolchains

CMake platform definitions, compiler definitions, and toolchain files for the Vita for the SNC compiler and GCC. The minimum required CMake version is 3.19. Please use the following compatibility table.

| Version | CMake |
| ------: | ----: |
|   0.1.0 |  3.19 |

### Libraries

Additional libraries for the Vita.

For user headers, add the following to your system include search paths:

```
$SCE_PSP2_SDK_DIR/target/include/vdsuite/user
$SCE_PSP2_SDK_DIR/target/include/vdsuite/common
```

For kernel headers, add the following to your system include search paths:

```
$SCE_PSP2_SDK_DIR/target/include/vdsuite/kernel
$SCE_PSP2_SDK_DIR/target/include/vdsuite/common
```

For system software 3.60 and multi-version libraries, add the following to your library search paths:

```
$SCE_PSP2_SDK_DIR/target/lib/vdsuite
```

For system software 3.65 libraries, add the following to your library search paths:

```
$SCE_PSP2_SDK_DIR/target/lib/vdsuite/365
$SCE_PSP2_SDK_DIR/target/lib/vdsuite
```

Please note the order of the paths, which are in decreasing priority.

If you are using CMake, the `VitaDevelopmentSuite` module provides the following variables:

```
VDSUITE_USER_INCLUDE_DIRECTORIES
VDSUITE_KERNEL_INCLUDE_DIRECTORIES
VDSUITE_LIBRARY_DIRECTORIES
VDSUITE_365_LIBRARY_DIRECTORIES
```

### Toolchain

Command lines tools for building executables and applications for the Vita. Use the `--help` flag to see usage.

#### libgen

Create stub libraries for the SN linker or for Vitasdk from EMD files and from Vitasdk import YAMLs. Can convert Vitasdk import YAMLs to EMD files.

#### pubgen

Package files into a VPK.

#### pubprx

Set SELF parameters. Compress and strip SELFs. Accepts either ELF or SELF as input.

#### pubsfo

Create and verify SFO files from SFX or YAML files.

#### emdc

Compiles EMD files.

### CMake Modules

CMake integration for the toolchain and libraries.
