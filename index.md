# Inception: System-wide Security Testing of Real-World Embedded Systems Software

Inception is a framework to perform security testing of real world firmware programs.

***Inception-translator*** generates a unified intermediate representation from C/C++ source code that also contains inline
assembly (or statically linked binary code). This representation is based on LLVM bytecode preserves as much as possible of the high-level semantics of the source code. This is useful to detect memory vulnerabilities. For example, knowing the size of a buffer makes it possible to detect an overflow. We call the intermediate representation resulting from this process mixed-IR.
 
***Inception-analyzer*** is a symbolic virtual machine built as an extension of the well knonw [Klee](https://klee.github.io/) tool. We have extended the memory management system of Klee in order to support our mixed-IR code, and to consider the memory mapped registers of peripherals. Inception may consider them as untrusted unconstrained symbolic inputs, or map those registers to the physical registers of a real device (using Inception-debbuger). Furthermore, we have extended Klee in order to support interrupts and multithreading.  

***Inception-debugger*** is a fast USB3.0 JTAG debugger (currently supporting ARM AHB-AP debug port). 
Inception-analyzer uses it to redirect read/write memory accesses and interrupts to a real target device.
Inception-debugger requires off-the-shelf hardware (Cypress Semiconductor FX3, Digilent ZYBO Zinq-7000 FPGA).

## Authors

Nassim Corteggiani, Giovanni Camurati, Aurélien Francillon.

## Getting started

### Installing the sofware

The easiest way is to use our Docker image. 
You can find more details on how to compile it [here](https://github.com/Inception-framework/docker).
Alternatively, you can bulld the necessary components on your machine (you can use our docker file as a reference). 

### Setting up the debugger

If you want you can skip this step and run all the examples that do not require redirection to the real device.

We are currently working on the release of the debugger. We will provide both source code and a synthesized design.
More details will be [here](https://github.com/Inception-framework/debugger).

### Quick tutorial

To help you getting started with Inception, we provide a very short and simple guide [here](https://github.com/Inception-framework/tutorial).This quick tutorial will teach you how to use Inception-translator on a very simple program, how to configure Inception-analyzer, and how to run the example. After this, you can move to our more complex examples.

### Examples

We provide a large set of examples [here](https://github.com/Inception-framework/usenix-samples).
This repository contains all the samples mentioned in our USENIX'18 paper. For each directory a README.md file is present to explain the purpose of the test and how to replay it. Many of them can be run also without any additional hardware.

### Verification

You can find our tool for verification [here](https://github.com/Inception-framework/verification). The README.md will explain you how our verification system works (comparison between execution in Inception-analyzer and execution on a real processor) and how to run all the pre-recorded tests without any additional hardware. If you have Inception-debugger and a Cortex-M3 with a AHB-AP JTAG port, you can create new tests.

## Publications

> **Inception: System-wide security testing of real-world embedded systems software**     
> Nassim Corteggiani, Giovanni Camurati, Aurélien Francillon   
> 27th USENIX Security Symposium (USENIX Security 18), Baltimore, MD (acceptance rate: 19.1%)  
> [PDF](http://s3.eurecom.fr/docs/usenixsec18_corteggiani.pdf)

## Other resources/coverage 

> [Open-Source Framework Detects Memory Corruptions in Embedded Software](https://www.maximintegrated.com/en/design/blog/open-source-framework.html)

## Official logo

![alt text][logo]

[logo]: https://raw.githubusercontent.com/Inception-framework/inception/master/Logo_inception.png "Inception official logo"
