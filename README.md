# mingw-contrib - A fix for missing or outdated libraries in LLVM-MinGW (ARMv7)

mingw-contrib is a fix for missing or outdated libraries in LLVM-MinGW (ARMv7). The original usage was to fix WMF (Windows Media Foundation), but now we need it for more. This was made mainly for Qt, but it can be used for any purposes. It doesn't overwrite any files in `include` or `lib`, so there's nothing to worry about. 

# Installing

## MXE
If you're using the [correct MXE sources](https://github.com/armdevvel/mxe-SHARED), then all you have to do is run `make mingw-contrib` in the root directory of MXE.

## From Source
To build mingw-contrib from source, all you need is CMake and LLVM-MinGW. After cloning the source, at the root of the directory you can build the project by running:

```c
mkdir build
cd build
// You can use plain CMake, but MXE provides armv7-w64-mingw32-cmake
armv7-w64-mingw32-cmake ..
make -j
make install
```

# Using

## bthprops

Since this is missing entirely and just created, you use it as normal! No changes needed.

## WMF

Since the headers and libraries don't overwrite anything, they're their own separate files. Lets use an example C++ file with some headers.

```c++
#include <mfapi.h>
#include <mfidl.h>
#include <mfreadwrite.h>
#include <propsys.h>
```

Building an applciation with this code and mingw-contrib will not work. You need to change it to:

```c++
#include <mfapi2.h>
#include <mfcaptureengine.h>
#include <mfd3d12.h>
#include <mfidl2.h>
#include <mfmediacapture.h>
#include <mfreadwrite2.h>
#include <propsys2.h>
```

As for the libraries, they're similar. Instead of libmfuuid.a and libpropsys.a (`-lmfuuid`, `-lpropsys`), you use libmfuuid2.a and libpropsys2.a (`-lmfuuid2`, `-lpropsys2`).

# Original Authors and Copying

Check [mingw-w64-info](mingw-w64-info). You can get the original source code at [SourceForge](https://sourceforge.net/projects/mingw-w64/files/mingw-w64/mingw-w64-release/).
