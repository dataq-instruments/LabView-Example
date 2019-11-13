# Labview
Labview example based dataqsdk ActiveX. It is based on DI-2108, but it also supports DI-11xx, DI-21xx, DI-41xx and DI-47xx with appropriate modification to reflec the gain/range difference.

With modification to DeviceDriver and Device ID, it can support other devices, please refer to https://www.dataq.com/data-acquisition/software/developer-network/#3

Requirement:<br/>
  Installation of LabView 2019 (32-bit)<br/>
  Installation of Dataq Software Suite<br/>
  Dataq Instruments devices that supports DataqSDK activeX<br/> 
  For more info about DataqSDK ActiveX, please refer to https://www.dataq.com/products/dataq-active-x/features.html

Foot notes:<br/>
  It uses DI-2108 as the target device, since its input range is 10V, the math to convert raw ADC reading to voltage can be simplified as ADC/3276.8 <br/>
  For the immediate readings, the first scans is used directly<br/>
  Use Dashboard to launch WinDaq to verify the operational status of the device if needed
  

![alt text](https://https://www.dataq.com/resources/repository/labview.gif "ScreenCapture")
