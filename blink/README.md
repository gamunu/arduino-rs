# Rust Setup

You need a nightly Rust compiler for compiling Rust code for AVR. The correct version will be installed automatically due to the `rust-toolchain.toml` file.

## Install rust-src

```bash
rustup component add rust-src
```

## Installing avr-gcc
`avr-gcc` is toolchain required to build binary targeting avr

### macOS
```bash
xcode-select --install # if you haven't already done so
brew tap osx-cross/avr
brew install avr-gcc avrdude
```

### Ubuntu
```bash
sudo apt install avr-libc gcc-avr pkg-config avrdude libudev-dev build-essential
```

Next, install ["ravedude"](https://github.com/Rahix/avr-hal/tree/main/ravedude), a tool that seamlessly integrates flashing your board into the usual cargo workflow:

```bash
cargo +stable install ravedude
```

## Build and run

### Set the serial port connected to the Arduino

#### Linux

```bash
export RAVEDUDE_PORT=/dev/ttyUSB1
```

#### macOS

The following command will list out the serial USB devices

```bash
ls /dev/tty* | grep usb
```

identify and export the device path

```
export RAVEDUDE_PORT=/dev/tty.usbserial-130
```

```bash
cd blink
cargo run --bin blink
```