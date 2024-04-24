# STM32F439ZI Nucleo Board Project

This project provides a basic example for the STM32F439ZI Nucleo board.

## Prerequisites

Before you begin, get the following required software:

- [USB driver for ST-Link](https://www.st.com/en/development-tools/stsw-link009.html)
- [GNU (GDB)](https://winlibs.com/)
- [OpenOCD](https://xpack.github.io/dev-tools/openocd/) -> [Download here](https://github.com/xpack-dev-tools/openocd-xpack/releases/)
- [Arm-GNU-toolchain](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads)

## Installation

Install the necessary Rust tools:

```bash
cargo install cargo-binutils
rustup component add llvm-tools
rustup target add thumbv7em-none-eabihf
```

## Usage

```bash
cargo build
```

```bash
cargo readobj -- --file-header
```

This should output something like the following:
  
  ```bash
ELF Header:
  Magic:   7f 45 4c 46 01 01 01 00 00 00 00 00 00 00 00 00
  Class:                             ELF32
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              EXEC (Executable file)
  Machine:                           ARM
  Version:                           0x1
  Entry point address:               0x80001AD
  Start of program headers:          52 (bytes into file)
  Start of section headers:          2257888 (bytes into file)
  Flags:                             0x5000400
  Size of this header:               52 (bytes)
  Size of program headers:           32 (bytes)
  Number of program headers:         5
  Size of section headers:           40 (bytes)
  Number of section headers:         23
  Section header string table index: 21
  ```

Open a terminal and run OpenOCD.

```bash
openocd -f board/stm32f4discovery.cfg
```

1. Connect the STM32F439ZI Nucleo board to the PC. Use the ST-Link connection CN1 and a Micro-USB B cable.

2. Open another terminal and run GDB with cargo run.

```bash
cargo run
```

Use GDB commands to navigate the code.
