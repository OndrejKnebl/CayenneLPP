# CayenneLPP

This is the Cayenne Low Power Payload encoder with Extended Data Types written in Python.

The Cayenne Low Power Payload (LPP) provides a convenient and easy way to send data over LPWAN networks such as LoRaWAN. The Cayenne LPP is compliant with the payload size restriction, which can be lowered down to 11 bytes, and allows the device to send multiple sensor data at one time. Cayenne LPP has several specific functions for some types of data, such as humidity, temperature, pressure, GPS and more.


More information can be found in the Cayenne LPP documentation: https://docs.mydevices.com/docs/lorawan/cayenne-lpp

## Usage
1. Import cayenneLPP.py to your script:
```Python
import src.cayenneLPP as cayenneLPP
```

2. Create lpp array:
```Python
lpp = []
```

3. Append your data to the array (for example add temperature 25.5 °C to channel 1):
```Python
lpp.append([1, "addTemperature", 25.5])
```

4. Call the cayenneLPP.encodeCayenneLPP(lpp) function, where lpp is array with your data. The function returns encoded data:
```Python
payload = cayenneLPP.encodeCayenneLPP(lpp)
```

### The whole code will look like this:
```Python
import src.cayenneLPP as cayenneLPP

lpp = []
lpp.append([1, "addTemperature", 25.5])

payload = cayenneLPP.encodeCayenneLPP(lpp)
print(payload)
```

The printed output (payload) will look like this:
```
016700ff
```


## Data types
### Format
```Python
lpp.append([channelNumber, "dataType", value])
```
### Data types

| Data type | Min value | Max value | Example |
| --- | --- | --- |  --- |
| addDigitalInput | 0 | 255 | ```lpp.append([1, "addDigitalInput", 0])``` |
| addDigitalOutput | 0 | 255 | ```lpp.append([1, "addDigitalOutput", 0])``` |
| addAnalogInput | -327.67 | 327.67 | ```lpp.append([1, "addAnalogInput", -327.67])``` |
| addAnalogOutput | -327.67 | 327.67 | ```lpp.append([1, "addAnalogOutput", -327.67])``` |
| addGenericSensor | 0 | 4294967295 | ```lpp.append([1, "addGenericSensor", 0])``` |
| addLuminosity | 0 | 65535 | ```lpp.append([1, "addLuminosity", 0])``` |
| addPresence | 0 | 255 | ```lpp.append([1, "addPresence", 0])``` |
| addTemperature | -3276.7 | 3276.7 | ```lpp.append([1, "addTemperature", -3276.7])``` |
| addRelativeHumidity | 0 | 100 | ```lpp.append([1, "addRelativeHumidity", 0])``` |
| addAccelerometer | -32.767 | 32.767 | ```lpp.append([1, "addAccelerometer", -32.767, -32.767, -32.767])``` |
| addBarometricPressure | 0 | 6553.5 | ```lpp.append([1, "addBarometricPressure", 0])``` |
| addVoltage | 0 | 655.34 | ```lpp.append([1, "addVoltage", 0])``` |
| addCurrent | 0 | 65.535 | ```lpp.append([1, "addCurrent", 0])``` |
| addFrequency | 0 | 4294967295 | ```lpp.append([1, "addFrequency", 0])``` |
| addPercentage | 0 | 255 | ```lpp.append([1, "addPercentage", 0])``` |
| addAltitude | -32767 | 32767 | ```lpp.append([1, "addAltitude", -32767])``` |
| addConcentration | 0 | 65535 | ```lpp.append([1, "addConcentration", 0])``` |
| addPower | 0 | 65535 | ```lpp.append([1, "addPower", 0])``` |
| addDistance | 0 | 4294967.295 | ```lpp.append([1, "addDistance", 0])``` |
| addEnergy | 0 | 4294967.295 | ```lpp.append([1, "addEnergy", 0])``` |
| addDirection | 0 | 65535 | ```lpp.append([1, "addDirection", 0])``` |
| addUnixTime | 0 | 4294967295 | ```lpp.append([1, "addUnixTime", 0])``` |
| addGyrometer | -327.67 | 327.67 | ```lpp.append([1, "addGyrometer", -327.67, -327.67, -327.67])``` |
| addColour | 0 | 255 | ```lpp.append([1, "addColour", 0, 0, 0])``` |
| addSwitch | 0 | 255 | ```lpp.append([1, "addSwitch", 0])``` |

| GPS | Longitude / Latitude Min value | Longitude / Latitude Max value | Altitude Min value | Altitude Max value| Example |
| --- | --- | --- | --- | --- | --- |
| addGPS | -838.8607 | 838.8607 | -83886.07 | 83886.07 | ```lpp.append([1, "addGPS", -838.8607, -838.8607, -83886.07])``` |







## Reference
- Inspired by the Cayenne LPP library: https://github.com/ElectronicCats/CayenneLPP
