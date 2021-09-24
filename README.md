# Protectli 8GB mSATA SSD RMA Tool

This tool is used to detect if a system is using a mSATA SSD storage device that has known failure rates exceeding that of which we tolerate.

## Synopsis

A batch of 8GB Protectli-brand mSATA SSDs has higher failure rates than we allow. This tool will identify if an affected SSD is attached to the system, and provide instructions on how to request an RMA with Protectli.

## Prerequisites

* A Linux distro
* `whiptail` or `dialog` for TUI
* `smartmontools` to read disk information

## Usage

1. Boot into a Linux environment on a machine containing a potentially-affected mSATA. (It doesn't necessarily need to be attached by mSATA. For example, you can use a USB-to-mSATA tool.)
1. Download the tool `rma-test`
1. Make the script executable `chmod +x rma-test`
1. Run the script with `./rma-test`

## Manual Method

You can also check RMA potential with the following command, replacing `sdX` with the appropriate device:

```
smartctl -a /dev/sdX
```

If all of the following are true, you may be eligible for RMA:

* The "Device Model" contains the string "SATAFIRM"
* The "Firmware Version" is "SBFM01W3"
* The "User Capacity" is exactly 8,012,390,400 bytes

## Changelog

* 1.0 (2021/09/24):
  * Initial tool release