# Labview
This Labview example is based on DATAQsdk ActiveX. It targets DI-2108, but it also supports DI-11xx, DI-21xx, DI-41xx and DI-47xx and others with appropriate modification, such as DeviceDriver and DeviceID, gain/range difference, please refer to https://www.dataq.com/data-acquisition/software/developer-network/#3

Requirements:<br/>
  Installation of LabView 2019 (32-bit)<br/>
  Installation of Dataq Software Suite<br/>
  Dataq Instruments devices that support DataqSDK ActiveX<br/> 
  For more info about DataqSDK ActiveX, please refer to https://www.dataq.com/products/dataq-active-x/features.html


![alt text](https://www.dataq.com/resources/repository/labview.gif "ScreenCapture")

Foot notes:<br/>
  It uses DI-2108 as the target device, since its input range is 10V, the math to convert raw ADC reading to voltage can be simplified as ADC/3276.8 <br/>
  For the immediate readings, the first scan is used directly<br/>
  Use Dashboard to launch WinDaq to verify the operational status of the device if needed
  
  It is noticed with LabView 2019, LabView failed to unload ActiveX on its way out (we will try to contact them to see if they will resolve this issue), leaving the device connected to the device driver, so that you can't restart the program nor invoke WinDaq unless you do the following:
  
  Right click on Windows task bar and select Tas Manager<br/>
  From the Processes tab, find DISCN???, and terminate it<br/>
 
