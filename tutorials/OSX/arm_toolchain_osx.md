# What is the deal with ARM toolchains?

Points:
* Cortex-A & Cortex-R/M toolchains seem to be incompatible
* Bare-metal is different from Linux (which one does do you use for Linux kernel compilation?)
* Linaro claims optimizations over gcc (which means they use different source code)
* Can GCC be setup as cross platform?
* 

## Bare-metal vs Linux

## Options
1. GCC
2. Linaro
3. Code Sorcery

## Build your own toolchain

There are a few tools which let you compile your own toolchain from scratch. Some of them are:

1. buildroot
2. crosstool-NG