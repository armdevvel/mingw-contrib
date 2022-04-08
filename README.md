# wmffix - A fix for WMF on LLVM-MinGW

wmffix is a fix for the usage of WMF (Windows Media Foundation) on LLVM-MinGW for Windows on ARM32, based on MinGW's CRT libraries and headers. This was made mainly for Qt's multimedia library, but it can be used for any WMF purposes. It doesn't overwrite any files in `include` or `lib`, so there's nothing to worry about. 

# Installing

## MXE
If you're using the [correct MXE sources](https://github.com/armdevvel/mxe), then all you have to do is run `make wmffix` in the root directory of MXE.

## From Source
To build wmffix from source, all you need is CMake and LLVM-MinGW. After cloning the source, at the root of the directory you can build the project by running:

```
mkdir build
cd build
// You can use plain CMake, but MXE provides armv7-w64-mingw32-cmake
armv7-w64-mingw32-cmake ..
make -j
make install
```

# Original Authors and Copying

Check [mingw-w64-info](mingw-w64-info). You can get the original source code at [SourceForge](https://sourceforge.net/projects/mingw-w64/files/mingw-w64/mingw-w64-release/).