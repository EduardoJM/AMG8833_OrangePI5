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

On the scripts we need to change the bus number configuration to get access to the AMG8833 i2c protocol interface.

###  3.1. <a name='BusNumber'></a>Bus Number

When we create the `AMG8833()` instance, like on the `IR_cam_test.py` script, we can pass the `bus_num` argument:

```python
sensor = amg8833_i2c.AMG8833(addr=0x69, bus_num=2)
```

The `bus_num=2` is referencing that we are using `I2C2` bus. On the OrangePI5 we have some i2c bus interfaces:

<details>
  <summary>I2C Interfaces</summary>

  | I2C bus | SDA pin  | SCL pin  | dtbo    |
  | ------- | -------- | -------- | ------- |
  | I2C2_M0 | Pin 3    | Pin 5    | i2c2-m0 |
  | I2C2_M4 | Pin 10   | Pin 8    | i2c2-m4 |
  | I2C4_M3 | Pin 22   | Pin 32   | i2c4-m3 |
  | I2C5_M3 | Pin 27   | Pin 28   | i2c5-m3 |
  | I2C8_M2 | Pin 29   | Pin 7    | i2c8-m2 |

  From the Orange PI 5 Plus documentation, we have a information about `I2C2_M0` and `I2C2_m4`:

  > I2C2_M0 and I2C2_M4 can only use one of them at the same time, and they cannot be used at the same time.
</details>

Based on the above I2C information from the OrangePi we can change the `bus_num` based on the others pin configurations:

```
orangepi@orangepi:~$ sudo i2cdetect -y 2 #i2c2 command
orangepi@orangepi:~$ sudo i2cdetect -y 4 #i2c4 command
orangepi@orangepi:~$ sudo i2cdetect -y 5 #i2c5 command
orangepi@orangepi:~$ sudo i2cdetect -y 8 #i2c8 command
```

Making a parallel on the `i2cdetect` configuration above, we have a table of `bus_num` setting:

| I2C Bus | bus_num |
| ------- | ------- |
| I2C2_M0 | 2       |
| I2C2_M4 | 2       |
| I2C4_M3 | 4       |
| I2C5_M3 | 5       |
| I2C8_M2 | 8       |

> Remember that is necessary to open the i2c buses on the linux system (see page 225 on the OrangePI 5 Plus User Manual).

##  4. <a name='SoftwareOutput'></a>Software Output

###  4.1. <a name='ExampleOutput'></a>Example Output

The following plot is outputted by the example script:
 - /examples/IR_cam_test.py

![AMG8833 Plot Test](https://static1.squarespace.com/static/59b037304c0dbfb092fbe894/t/60008c350b092f4fbc949df7/1610648652687/AMG8833_IR_cam_test.png?format=1000w)

###  4.2. <a name='Real-TimeInterpolatedIRCamera'></a>Real-Time Interpolated IR Camera

The following plot is outputted by the example script:
 - /examples/IR_cam_interp.py

![AMG8833 Interpolated Real-Time](https://static1.squarespace.com/static/59b037304c0dbfb092fbe894/t/6000b926078d244fe1a01fb5/1610660212607/ir_cam_interp_video_demo.gif?format=1000w)
