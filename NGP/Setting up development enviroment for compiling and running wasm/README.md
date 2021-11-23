
## Setting up Development Enviroment
In this tutorial i will be setting up development enviroment for compiling C programs to WASM and executing the WASM module using wasmtime runtime.

## Download Clang, a C/C++ Compiler.
Upstream Clang and LLVM (from 9.0 onwards) can compile for WASI out of the box, and WebAssembly support is included in them by default. 

#### Download and install clang : 
    sudo apt install clang

when installation is complete, run this command to verify your installation.
    
    clang --version
    
result:
    
    clang version 10.0.0-4ubuntu1 
    Target: x86_64-pc-linux-gnu
    Thread model: posix
    InstalledDir: /usr/bin
    
Next, download the WASI-sdk.The wasi-sdk provides a clang which is configured to target WASI and use the WASI sysroot by default if you put the extracted tree into /, so we can compile our program like:

    opt/wasi-sdk/share/sysroot/bin/clang demo.c -o demo.wasm
If you would want to extract it elsewhere, you can specify the sysroot directory like this:

    ~/wasi-sdk-12.0/bin/clang demo.c --sysroot <path to sysroot> -o demo.wasm
If you're using the wasi-sdk, the sysroot directory is located in opt/wasi-sdk/share/sysroot/ on Linux and mac.

This is just regular clang, configured to use a WebAssembly target and sysroot. The output name specified with the "-o" flag can be anything you want, and does not need to contain the .wasm extension. In fact, the output of clang here is a standard WebAssembly module:


## Install Runtime enviroment:
you could use either wasmtime or wasmer or other runtime enviroments

#### Install WASMTIME
The WASMTIME is a wasm runtime enviroment for running web assembly modules. The easiest way to install the wasmtime CLI tool is through our installation script. Linux and macOS users can execute the following:
    
    curl https://wasmtime.dev/install.sh -sSf | bash

This will download a precompiled version of wasmtime and place it in $HOME/.wasmtime, and update your shell configuration to place the right directory in PATH.
You can confirm your installation works by executing:

    wasmtime -V
    
result:    
    
    wasmtime 0.12.0

To run a wasm with wasmtime
    
    wasmtime <filename>.wasm

    
#### OR Install WASMER
WASMER is an open-source runtime for executing WebAssembly on the Server. To install it run the following command on yur terminal

    curl https://get.wasmer.io -sSfL | sh
    
To verify your installation:
    
    wasmer --version
result:
    
    wasmer 2.0.0

To run a wasm with wasmer

    wasmer run <filename>.wasm



## MY Reference:
about wasmtime: https://github.com/bytecodealliance/wasmtime/blob/main/docs/WASI-tutorial.md#executing-in-wasmtime-runtime

about wasmer: https://wasmer.io/

