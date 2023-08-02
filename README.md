[UnRAR](https://www.rarlab.com/rar_add.htm) includes SSE code to speed up AES/RS16/BLAKE2 computation, however it’s only enabled for Windows x86/x64 builds.

This repository provides a quick-n-dirty patch to enable the SSE code to compile in GCC/Clang, which allows these speed ups to be present in non-Windows builds.
UnRAR also includes AES acceleration code for ARM, but it isn’t enabled by default. This patch also enables this acceleration.

The [releases page](releases) hosts MacOS and static Linux builds for x64/ARM64 platforms.

See [the original UnRAR page](https://www.rarlab.com/rar_add.htm) for more info on UnRAR.