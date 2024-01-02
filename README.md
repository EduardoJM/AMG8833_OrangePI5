# Python Thermal Camera with Orange PI (AMG8833)

This is a documentation of using AMG8833 infrared array on Orange PI 5 (Plus model) inspired and full-based on the original documentation and code of using it on Raspberry Pi 4 ([see repository here](https://github.com/makerportal/AMG8833_IR_cam)).

##  1. <a name='TableOfContents'></a>Table Of Contents

<!-- vscode-markdown-toc -->
* 1. [Table Of Contents](#TableOfContents)
* 2. [Hardware Configuration](#HardwareConfiguration)
	* 2.1. [Wiring Diagram](#WiringDiagram)
		* 2.1.1. [i2c](#i2c)
		* 2.1.2. [Power Supply](#PowerSupply)
		* 2.1.3. [Diagram](#Diagram)
* 3. [Software Configuration](#SoftwareConfiguration)
	* 3.1. [Bus Number](#BusNumber)
* 4. [Software Output](#SoftwareOutput)
	* 4.1. [Example Output](#ExampleOutput)
	* 4.2. [Real-Time Interpolated IR Camera](#Real-TimeInterpolatedIRCamera)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->

##  2. <a name='HardwareConfiguration'></a>Hardware Configuration

###  2.1. <a name='WiringDiagram'></a>Wiring Diagram

####  2.1.1. <a name='i2c'></a>i2c

Using the `40 Pin Expansion Interface Pin Instructions`, we have multiple i2c **SCL/SDA** pin's. We decided to use `I2C2_SCL_M4` and `I2C2_SDA_M4` (`GPIO1_A1` and `GPIO1_A0`) pins on the **Orange PI 5** board pins. See the pinout bellow:

<details>
  <summary>OrangePI 5 Plus Pinout</summary>

  ![OrangePI5 Plus Pinout](./.github/pinout.png)
</details>


####  2.1.2. <a name='PowerSupply'></a>Power Supply

The AMG8833 is powered by 5V pin on the OrangePI 5 board and we decided to use GND pin on the side of the `I2C2_SDA_M4` because the pins on the circled by dot line on the image on the section bellow is used by calor fan.

####  2.1.3. <a name='Diagram'></a>Diagram

The bellow image contains the connections of the OrangePI 5 Plus and AMG8833 used by the project:

![OrangePI 5 Plus and AMG8833 Diagram](./.github/hardware.png)

##  3. <a name='SoftwareConfiguration'></a>Software Configuration

TODO: write here

###  3.1. <a name='BusNumber'></a>Bus Number

TODO: write here

##  4. <a name='SoftwareOutput'></a>Software Output

###  4.1. <a name='ExampleOutput'></a>Example Output

The following plot is outputted by the example script:
 - /examples/IR_cam_test.py

![AMG8833 Plot Test](https://static1.squarespace.com/static/59b037304c0dbfb092fbe894/t/60008c350b092f4fbc949df7/1610648652687/AMG8833_IR_cam_test.png?format=1000w)

###  4.2. <a name='Real-TimeInterpolatedIRCamera'></a>Real-Time Interpolated IR Camera

The following plot is outputted by the example script:
 - /examples/IR_cam_interp.py

![AMG8833 Interpolated Real-Time](https://static1.squarespace.com/static/59b037304c0dbfb092fbe894/t/6000b926078d244fe1a01fb5/1610660212607/ir_cam_interp_video_demo.gif?format=1000w)
