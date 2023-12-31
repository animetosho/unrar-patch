### UnRAR 7.0 includes modifications which makes this patch (largely) obsolete. It is recommended that you use UnRAR 7.0 instead of this patch.

This repository is left for historical reference (or if you need a build for Windows on ARM). Original README follows.



---



[UnRAR](https://www.rarlab.com/rar_add.htm) includes SSE code to speed up AES/RS16/BLAKE2 computation, however it’s only enabled for Windows x86/x64 builds.

This repository provides a quick-n-dirty patch to enable the SSE code to compile in GCC/Clang, which allows these speed ups to be present in non-Windows builds.
UnRAR also includes AES acceleration code for ARM, but it isn’t enabled by default. This patch also enables this acceleration.

The [releases page](https://github.com/animetosho/unrar-patch/releases) hosts MacOS and static Linux builds for x64/ARM64 platforms, plus Windows ARM64.

See [the original UnRAR page](https://www.rarlab.com/rar_add.htm) for more info on UnRAR.

### Building

If you prefer, you can build this patched unrar with the following commands:

```
wget https://www.rarlab.com/rar/unrarsrc-6.2.10.tar.gz
tar zxf unrarsrc-6.2.10.tar.gz
cd unrar
patch -s -p1 < ../unrar-gcc.patch
#sed -i 's/^CXXFLAGS=/CXXFLAGS=-std=c++11 /' makefile  # if build otherwise fails
make
```

Note: the *unrar-vcx.patch* file is for patching the Visual C++ project files (*.vcxproj) for building Windows ARM64 binaries. If you wish to build these, you’ll need to apply both patches. As the .vcxproj files use Windows newlines, you may need to be careful with applying the vcx patch, as Unix tools don’t often like Windows newlines.