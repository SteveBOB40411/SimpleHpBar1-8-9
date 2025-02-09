SimpleVisor is a simple, portable, Intel x64/EM64T VT-x specific hypervisor with two specific goals: using the least amount of assembly code (10 lines), and having the smallest amount of VMX-related code to support dynamic hyperjacking and unhyperjacking (that is, virtualizing the host state from within the host) while also supporting advanced features such as EPT and VPID. It currently runs on both Windows and in UEFI environments.

## Introduction

Have you always been curious on how to build a hypervisor? Has Intel's documentation (the many hundreds of pages) gotten you down? Have the samples you've found online just made things more confusing, or required weeks of reading through dozens of thousands of lines and code? If so, SimpleVisor might be the project for you.

Not counting the exhaustive comments which explain every single line of code, and specific Windows-related or Intel-related idiosyncrasies, SimpleVisor clocks in at about 500 lines of C code, and 10 lines of x64 assembly code, all while containing the ability to run on every recent version of 64-bit Windows, and supporting dynamic load/unload at runtime.

Additionally, SimpleVisor utilizes a lightweight OS-library for Windows-specific functionality, separating out the hypervisor pieces from the Windows-specific pieces. Leveraging this portable design, a UEFI version of SimpleVisor is also now available. Note however, that it does not have robust support for MP environments due to issues with UEFI, and that loading an operating system will eventually result in a crash as the OS will hit unimplemented code paths due to its re-configuration of processor resources. Virtualizing the entire boot of the operating system from UEFI is beyond the scope of the project.

SimpleVisor can be built with Visual Studio 2015 Update 3, and while older/newer compilers have not been tested and are not supported, it's likely that they can build the project as well. It's important, however, to keep the various compiler and linker settings as you see them, however.

SimpleVisor has currently been tested on the following platforms successfully:
