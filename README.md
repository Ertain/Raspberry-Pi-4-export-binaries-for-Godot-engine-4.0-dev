# Export template binaries for the development version of Godot 4.0
## For Raspberry Pi 4

**These binaries will _only_ work with the development version released on December 10, 2021.**

These are export binaries for the development version of Godot engine 4.0, built on the Raspberry Pi 4 (8GB). A developer can (theoretically) make a game in the development version of Godot (the one released on December 10, 2021), then use one of the binaries here, and have it run on the Raspberry Pi 4.

The files contained here were built on Raspberry Pi OS (Buster). The files are 32-bit. They were built with the sources found [here](https://downloads.tuxfamily.org/godotengine/testing/4.0/4.0-dev.20211210/).

To build them yourself, first install the necessary build packages (a list is found [here](https://docs.godotengine.org/en/latest/development/compiling/compiling_for_linuxbsd.html), under the "Debian/Ubuntu" section). On Buster, don't install SCons from the repos; instead, install it from pip. This will give you an update-to-date version which can build the engine templates. Also install LLVM, clang, and `lld` (use the command `apt install llvm clang lld`). Finally, use the script below to build the engine template binaries.

Script to build the engine:

    #!/usr/bin/env bash
    # Script for building a development version of Godot engine 4.0.
    # -- December 28, 2021

    # Add the path to the Python3 version of Scons since it's installed locally. We need this in order to build a version of Godot 4.0.
    export PATH=$PATH:/home/pi/.local/bin/

    scons -j7 p=linuxbsd target=release_debug use_llvm=yes udev=yes tools=no

    exit 0

When exporting, select these files from the "Export" dialog, under "Custom Template".