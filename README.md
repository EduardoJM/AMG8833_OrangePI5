# Python Thermal Camera with Orange PI (AMG8833)

This is a documentation of using AMG8833 infrared array on Orange PI 5 (Plus model) inspired and full-based on the original documentation and code of using it on Raspberry Pi 4 ([see repository here](https://github.com/makerportal/AMG8833_IR_cam)).

## Hardware Configuration

### Wiring Diagram

#### i2c

Using the `40 Pin Expansion Interface Pin Instructions`, we have multiple i2c **SCL/SDA** pin's. We decided to use `I2C2_SCL_M4` and `I2C2_SDA_M4` (`GPIO1_A1` and `GPIO1_A0`) pins on the **Orange PI 5** board pins. See the pinout bellow:

<details>
    <summary>OrangePI 5 Plus Pinout</summary>

    ### Heading
    ![Orange Pi 5 Plus](./.github/pinout.png)

</details>


#### Power Supply

The AMG8833 is powered by 5V pin on the OrangePI 5 board and we decided to use GND pin on the side of the `I2C2_SDA_M4` because the pins on the circled by dot line on the image on the section bellow is used by calor fan.

#### Diagram

The bellow image contains the connections of the OrangePI 5 Plus and AMG8833 used by the project:

![OrangePI 5 Plus and AMG8833 Diagram](./.github/hardware.png)

### - Real-Time Interpolated IR Camera - 

The following plot is outputted by the example script:
 - /examples/IR_cam_interp.py

![AMG8833 Interpolated Real-Time](https://static1.squarespace.com/static/59b037304c0dbfb092fbe894/t/6000b926078d244fe1a01fb5/1610660212607/ir_cam_interp_video_demo.gif?format=1000w)

### - Wiring Diagram - 

The AMG8833 is powered by the 5V pin on the Raspberry Pi, and wired to the SDA/SCL pins on GPIO 2 and GPIO 3, respectively. 

![Wiring diagram between AMG883 to RPI4](https://static1.squarespace.com/static/59b037304c0dbfb092fbe894/t/600078199e8a7b75b93b463d/1610643545338/amg8833_RPi4_wiring.png?format=1000w)

### - Example Output - 

The following plot is outputted by the example script:
 - /examples/IR_cam_test.py

![AMG8833 Plot Test](https://static1.squarespace.com/static/59b037304c0dbfb092fbe894/t/60008c350b092f4fbc949df7/1610648652687/AMG8833_IR_cam_test.png?format=1000w)
