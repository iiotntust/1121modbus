![Alt text](https://github.com/iiotntust/1121modbus/blob/main/DSC_0386.JPG)
Image of a CT-less Powermeter
![Alt text](https://github.com/iiotntust/1121modbus/blob/main/DSC_0387.JPG)
Image of a Powermeter with a current transformer (CT)

### Modbus Tools and USB/RS485 Converter Driver: (Software)
* Modbus Tools source: https://www.modbustools.com/ (only 30-day trials)
  #### Recovery point setting (conduct the setting before you install the software)
  * https://www.asus.com/tw/support/faq/1018810/#Win11
* ModbusPoll: install on PC to read the devices in the network via RS485 or LAN.
* ModbusSlave: install on PC to simulate a device with Modbus Protocols (Modbus/RTU, TCP)
* Modbustool.7z: executable file (.exe), unlimited time to use, but Chinese GUI only
* ModbusTool(English): A free suite containing both Modbus Master and Slave programs (https://github.com/ClassicDIY/ModbusTool)
* USB/RS485 converter driver CH340 (source:https://www.wch.cn/download/CH341SER_EXE.html )
* RealTerm: A powerful serial terminal program
### Hands-ON Instruction: 
#### 1. Install the software and connect the device
1. Download and install the Modbus tools.
2. Plug-in the USB/RS485 converter (install the USB/RS485 converter driver, CH340 if necessary)
#### (Optional) Test the converters by connecting one to each end of the communication cable.  
![Alt text](https://github.com/iiotntust/1121modbus/blob/main/DSC_0388.JPG)
1. Connect the black conductor to A and the white conductor to B in the USB/RS485 converters' terminals.
2. Connect each conventer to the computer. Two free USB ports are necessary.
3. Open two Realterm instances and configure each with the appropriate COM port set by the OS.
4. If the terminals and converters are configured correctly, when text is typed in one terminal,
5. It should appear inside the other. Remember to close the RealTerm programs after use as they will interfere with other programs will use the converters.
#### 2. change the slave's ID
- Because we have two slaves, so we need to change ID first.
- Making modbus poll can recognize they are different device.
- Before we adjusting the meter's ID, notice that we can only change device's ID by one master and one slave at the same environment.
- In this hands-on, we chose to change power meter's ID from one to ten.(All device are default ID1)
1. Follow the schematic here:  
![image](https://github.com/iiotntust/1121modbus/blob/b70c1803ebb63e15933e1eb40781c30892abbe2b/picture/slaveID_adjust.png)
2. Check meter's manual, find which register is refer to RTU address.(Hint: adjust modbus-RTU address)
> [!CAUTION]
> - Notice that before you modify your ID, make sure you are reading right definition(for meter is input register), serial setting have to set None parity and meter should connect with power supply.  
> - Otherwise you won't see the responce OK but you still can modify ID
3. Find which fuction code should we use.(Hint: writing register)
#### (Optional) PC-to-PowerMeter
1. Use read power meter voltage and current by PC with ModbusPoll
#### 3. wiring the USB to RS485 convertor connection with temp./humi. sensor and power meter.  
![S__88981511](https://github.com/iiotntust/1121modbus/assets/56021651/3f29d30f-97e3-4a5a-bf7d-8fee5a503cb7)
- Follow the schematic here:  
![image](https://github.com/iiotntust/1121modbus/blob/b70c1803ebb63e15933e1eb40781c30892abbe2b/picture/senser_meter.png)
#### 4. Read data of both humi-temp sensor and powermeter
1. wiring and setting (ID:1 humi./temp. sensor, ID:10 Power Meter);Manual can be found in "device_manual", 溫濕度計 and Peacefair電表)
* Be aware of we use different fuction code to set register's data from humi./temp. sensor and power meter.
2. Connection setting and reading  
![image](https://github.com/iiotntust/1121modbus/blob/b70c1803ebb63e15933e1eb40781c30892abbe2b/picture/1.png)
3. Use ModbusPull read the data from both Humi-Temp sensor and Powermeter  
![image](https://github.com/iiotntust/1121modbus/blob/b70c1803ebb63e15933e1eb40781c30892abbe2b/picture/6.png)
#### Additional: more detail about how to change ID and read register
1. Where is the function code in the meter's manual?(for writing register)  
![image](https://github.com/iiotntust/1121modbus/blob/b70c1803ebb63e15933e1eb40781c30892abbe2b/picture/2.png)
2. Where the address in the meter's manual if you want to modify the salve address?  
![image](https://github.com/iiotntust/1121modbus/blob/b70c1803ebb63e15933e1eb40781c30892abbe2b/picture/3.png)
3. Where is the function code in the meter's manual?(for reading register)  
![image](https://github.com/iiotntust/1121modbus/blob/b70c1803ebb63e15933e1eb40781c30892abbe2b/picture/4.png)
4. How to set the "read definition" function to read the power meter's register?
![image](https://github.com/iiotntust/1121modbus/blob/b70c1803ebb63e15933e1eb40781c30892abbe2b/picture/5.png)

### RS485-TTL Arduino
- https://forum.arduino.cc/t/how-to-read-rs485-data-in-arduino/673285!
- [image](https://github.com/user-attachments/assets/924b7c92-46ef-43ff-b9de-5a78256ec6c5)

