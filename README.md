# LabView
This LabView example is based on DATAQsdk ActiveX. It targets DI-2108, but it can also be applied to  DI-11xx, DI-21xx, DI-41xx and DI-47xx and others with appropriate modification, such as DeviceDriver and DeviceID, gain/range difference, please refer to https://www.dataq.com/resources/installations/web-help/sdk/, under Reference Materials->Device IDs and Device Drivers

**Extra Readings**
  - Please look at our new LabView example https://github.com/dataq-instruments/USB_Labview_Example 
  
  - See http://ultimaserial.com/lv8tutor.html and http://ultimaserial.com/lvtutor.html for how to dive into the block diagram level of LabView to modify the VI to suite your applications

  - See https://github.com/dataq-instruments/LabView-for-DI-2008 for DI-2008 example. This example is based on DataqSDK ActiveX, and it requires **32-bit** LabView

  - See https://github.com/dataq-instruments/LabView-Dio-Ain for how to use DIO while recording analog waveform. This example is based on DataqSDK ActiveX, and it requires **32-bit** LabView

  - See https://github.com/dataq-instruments/LabView-2108-CDC for how to access DI-11xx/2xxx/4xxx **_USB_** series via virtual COM port and program in  protocol level. When using this approach, either **32-bit** or **64-bit** LabView can be employed


**Test Drive**:

  1) Installation of LabView 2019 (**32-bit**)
  
  2) Installation of Dataq Software Suite
  
  3) Use any Dataq Instruments devices that support DataqSDK ActiveX. For more info about DataqSDK ActiveX, please refer to https://www.dataq.com/products/dataq-active-x/features.html 
  
  4) Here is what you will see <br/>
  ![alt text](https://www.dataq.com/resources/repository/labview.gif "ScreenCapture by LICECap")

:notebook:Foot notes:
  - It uses DI-2108 as the target device, since its input range is 10V, the math to convert raw ADC reading to voltage can be simplified as ADC/3276.8
  
  - For the immediate readings, the first scan is used directly
  
  - Use Dashboard to launch WinDaq to verify the operational status of the device if needed
  
:bug: LabView 2019 Glitch

  - It is noticed with LabView 2019, LabView failed to unload ActiveX on its way out if the activex is used inside the program, leaving the device connected to the device driver
  
  - To deal with problem, we added a work around in following steps in the example
  
  - After Stop, we will assign a new DeviceDriver (simply a non-existing file as space holder)<br/>
  Invoke DigitalOutput so that the "new" device driver will be used and release the real one<br/>
 
:boom: if you terminate the app without properly unloading ActiveX, you will not be able to restart LabView program nor WinDaq, and the WinDaq dashboard will show "Busy" status for the device, to resolve it

1) Right link on Window's task bar in the bottom of your screen

2) Select Task Manager

3) Under Processes tab, locate a Background processes named "DISCN???", where ??? matches the number in DI???NT.DLL you assigned to DeviceDriver

4) Terminate it. Everything will back to normal after this, you may use Windaq Dashboard to launch Windaq to verify it.

:boom: To debug DataqSDK-based LabView programs, the best way to generate debug messages from Dataqsdk. To do that

1) Locate TPDATAQ.INI in Windows directory (C:\Windows by default). 

2) Use any text editor to open it. 

3) Find the section Global

4) Change debug =0 to debug =2 

5) Run your program, DataqSDK will print out debug messages on every step

6) Attach the error msg to your support ticket  

7) Don't forget to change it back to debug=0 when debug is finished
