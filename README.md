![](../../workflows/gds/badge.svg) ![](../../workflows/docs/badge.svg) ![](../../workflows/fpga/badge.svg)

# Overview

This project provides a template for generating an FPGA bitstream for a Wokwi based design for Tiny Tapeout.

# What is Tiny Tapeout?

TinyTapeout is an educational project that aims to make it easier and cheaper than ever to get your digital designs manufactured on a real chip.

To learn more and get started, visit https://tinytapeout.com.

# How to Use this Template

## 1. Create your design

Go to the Wokwi project template (https://wokwi.com/projects/388731863464378369).  

Using the drop down menu in the upper left, Save a Copy for your own project.

Create and simulate your design on Wokwi.

To program the FPGA demo board with your design, follow the next set of instructions.

## 2. Clone this repo

Create a GitHub account if you don't have one.  Log into your account and select the 'Use this template' button in the 
upper right to clone a new copy of this repo in your GitHub account.

## 3. Enable GitHub actions to build the results page

- [Enabling GitHub Pages](https://tinytapeout.com/faq/#my-github-action-is-failing-on-the-pages-part)

## 4. Edit info.yaml

Edit the [info.yaml](info.yaml) and change the wokwi_id to the ID of your Wokwi project. You can find the ID in the URL of your project, it's the big number after `wokwi.com/projects/`.

The GitHub action will automatically fetch the digital netlist from Wokwi and build the FPGA bitstream.

## 5. Generate and download your FPGA bitstream

Once GitHub Actions have been enabled for your forked copy of this repo, GitHub will automatically run the workflows found under the Actions menu for your repo.

When you make a change on Wokwi, you need to be sure to save your changes on the Wokwi web page.  Then go to the FPGA action in the GitHub Actions page for your repo and manually restart the workflow.

A green checkmark shows the workflow completed successfully.  Click on the workflow on the Actions summary page for the workflow.  At the bottom of the page you will find an Artifacts section with a bitstream link.  Click to download locally to your desktop.  Navigate to the downloaded file and click to unpack the zip file and get a 'wokwi.bin' file.

Follow the instruction to program the bitstream on your demo board.

## 6. Programming your bitstream on the FPGA board

### Put your board in 'Boot Mode'

While holding the 'Boot' button on the top carrier board, connect a USB from your desktop to the top carrier to power on the board.  

Release the 'boot' button.

Select from one of the options below to program the bitstream to the board.

### WebUSB DFU

Navigate to the follow web page.

https://devanlai.github.io/webdfu/dfu-util/

Click the 'Connect' button and select the device with 'Tiny Tapeout'.  A pop menu should appear.  Select the 'ICE40' interface.

Click the 'Choose File' button under Firmware Download.  Select the woki.bin file you downloaded previously.  Click the Download button.

Unplug and re-plug the USB in the top carrier to power cycle the board.

### dfu-util for Win64

Download and unzip the following executable...

https://files.ef.link/mest/win64.zip

dfu-util.exe will be installed under /win64

### dfu-util for Mac

brew install dfu-util

### Ubuntu
It's pre-installed… yay… but you don't have permission to use it. To open USB access:

echo 'ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="1d50", ATTRS{idProduct}=="6146", MODE="664", GROUP="plugdev", TAG+="uaccess"' | sudo tee /etc/udev/rules.d/50-usb.rules
sudo udevadm control --reload-rules
sudo udevadm trigger

## Verilog Projects

For Verilog projects, see the following repo for a template that supports Verilog based designs.

## Other Resources

- [FAQ](https://tinytapeout.com/faq/)
- [Digital design lessons](https://tinytapeout.com/digital_design/)
- [Learn how semiconductors work](https://tinytapeout.com/siliwiz/)
- [Join the community](https://discord.gg/rPK2nSjxy8)

## What next?

- Submit your design to the next shuttle [on the website](https://tinytapeout.com/#submit-your-design). The closing date is **November 4th**.
- Edit this [README](README.md) and explain your design, how it works, and how to test it.
- Share your GDS on your social network of choice, tagging it #tinytapeout and linking Matt's profile:
  - LinkedIn [#tinytapeout](https://www.linkedin.com/search/results/content/?keywords=%23tinytapeout) [matt-venn](https://www.linkedin.com/in/matt-venn/)
  - Mastodon [#tinytapeout](https://chaos.social/tags/tinytapeout) [@matthewvenn](https://chaos.social/@matthewvenn)
  - Twitter [#tinytapeout](https://twitter.com/hashtag/tinytapeout?src=hashtag_click) [@matthewvenn](https://twitter.com/matthewvenn)

