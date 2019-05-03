# Sensor Types

See also

* [Sensro Units](./SensorUnits.md)
* [Unit Prefixes](./UnitPrefixes.md)

Each sensor data that comes to the uBeac panel should have a sensor type property which is a digit that shows the type of the sensor. If you develop your software devices, you will need to be aware of these types to send a valid sensor data. These sensor types are as below:

| Tile | Code | Description | Unit | Source |
|------|:----:|-------------|:----:|--------|
| N/A | 0 | - | N/A | - |
| Custom | 1 | - | Custom | - |
| Location | 2 | - | degree (°) | - |
| Distance | 3 | - | [m , in , mi , yd](https://en.wikipedia.org/wiki/Unit_of_length) |  [Source](https://en.wikipedia.org/wiki/Distance) |
|Temperature | 4 | - | [C, F, K](https://en.wikipedia.org/wiki/Temperature_measurement#Comparison_of_temperature_scales) | - | - |
|Humidity | 5 | - | [%, grams/m³](https://www.engineersgarage.com/articles/humidity-sensor) | [source](https://en.wikipedia.org/wiki/Hygrometer) |
| Voltage | 6 | VLPC stands for visible-light photon counter and refers to a new high quantum efficiency multi-photon counting detector, which operates at visible wavelengths. The ability to be capable of counting the exact number of photons that are detected is extremel | Voltage (V) | [Source](https://www.electrical4u.com/voltage-sensor/) |
|Acceleration| 7 | An accelerometer is a device that measures proper acceleration. Proper acceleration, being the acceleration (or rate of change of velocity) of a body in its own instantaneous rest frame, is not the same as coordinate acceleration, being the acceleration in a fixed coordinate system.  | [m/s²](https://en.wikipedia.org/wiki/Metre_per_second_squared) | - |
|MagneticField| 8 | - | [Tesla](https://en.wikipedia.org/wiki/Tesla_(unit)) , [Gauss](https://en.wikipedia.org/wiki/Gauss_(unit)) | [Source](https://en.wikipedia.org/wiki/Magnetometer) |
| RotationalMotion | 9 | - | degree, radians | - |
| Proximity | 10 | - | [m , in , mi , yd](https://en.wikipedia.org/wiki/Unit_of_length) |  [Source](https://en.wikipedia.org/wiki/Proximity_sensor) |
| Illuminance | 11 |Photodetectors, also called photosensors, are sensors of light or other electromagnetic radiation. A photo detector has a p–n junction that converts light photons into current. The absorbed photons make electron–hole pairs in the depletion region| [lux](https://en.wikipedia.org/wiki/Lux#Non-SI_units_of_illuminance) | [Source](https://en.wikipedia.org/wiki/Photodetector) |
| Pressure | 12 |A pressure sensor is a device for pressure measurement of gases or liquids. Pressure is an expression of the force required to stop a fluid from expanding, and is usually stated in terms of force per unit area. A pressure sensor usually acts as a transducer; it generates a signal as a function of the pressure imposed. For the purposes of this article, such a signal is electrical. | [Pascal, bar, atm, Torr](https://en.wikipedia.org/wiki/Pascal_(unit)) | [Source](https://en.wikipedia.org/wiki/Pressure_sensor) |
| Counter | 13 | - | Count | - |
| Orientation | 14 | - | degree(°), radians | - |
| Gyroscope | 15 | A gyroscope is a device used for measuring or maintaining orientation and angular velocity. It is a spinning wheel or disc in which the axis of rotation is free to assume any orientation by itself. When rotating, the orientation of this axis is unaffected by tilting or rotation of the mounting, according to the conservation of angular momentum. | degree, radians | [Source](https://en.wikipedia.org/wiki/Gyroscope) |
|Sound | 16 | - | [dB, Hz](https://en.wikipedia.org/wiki/Sound_unit) | - | - |
|SignalStrength | 17 | - | dB, dBm | - | - |
|Processor | 18 | - | percent - % | - | - |
|Memory | 19 | - | percent - % | - | - |
|DiskSpace | 20 | - | Byte | - | - |
|BandWidth | 21 | - | bit/s - Byte/s | - | - |
|revolution | 22 | - | rpm | - | - |
|Bus | 23 | - | bit | - | - |

