idVendor and idProduct values are hexadecimal numbers that uniqueluy identify the USB devices. 
Once finding the values, you can use these in Python code to interact with the joysticks using 'hid' library or other appropriate libraries for macOS.
This would be useful when certain usb devices that are well found and connected to code in windows comptuer don't work on mac. 
When modifying mac code to recognize usb devices, follow the steps below. 

1. Run this on mac terminal with connecting usbc converter, but not the joysticks yet. 
```
% ioreg -p IOUSB -c IOUSBDevice -l | grep -e '"idVendor" =' -e '"idProduct" ='
```
For example, you will find output as below. 
```
  | | |   "idProduct" = 10263
  | | |   "idVendor" = 8457
  | | |     "idProduct" = 49685
  | | |     "idVendor" = 1133
  | |       "idProduct" = 45322
  | |       "idVendor" = 1103
  |       "idProduct" = 2071
  |       "idVendor" = 8457
```

2. Then, run on mac terminal with usb joysticks connected to type c converter.
For example, you will find output as below.
```
  | | |   "idProduct" = 10263
  | | |   "idVendor" = 8457
  | | |     "idProduct" = 45322
  | | |     "idVendor" = 1103
  | |       "idProduct" = 49685
  | |       "idVendor" = 1133
  |       "idProduct" = 2071
  |       "idVendor" = 8457
```

4. Now, you will be able to identify which "idProduct" and "idVender" is referring to the specific joysticks.
5. On your virtual environment for python code, install hid library.
```
pip install hidapi

```
