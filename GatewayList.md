# List of supported Gateways

## 1. Hardware gateways

* **Raspberry Pi**: you can set up your Raspberry Pi to send request to uBeac panel. To learn how to do that, visit [Getting started with Raspberry Pi](./GettingStartedWithRaspberryPi.md) page.
* **Arduino**: you can set up your Arduino to send request to uBeac panel. To learn how to do that, visit [Getting started with Arduino](./GettingStartedWithArduino.md) page.
* **Ingics**: To learn how to configure Ingics gateway to send data, you can go to [uBeac YouTube channel](https://www.youtube.com/channel/UCxHu4X1zLUkS8amK5EwdBXg) and watch [related video](https://www.youtube.com/watch?v=JpZOgGGpgg0).
* **Minew**: Is a capable gateway which is able to send data over HTTP(s) and MQTT(s) protocols. You can go to [uBeac YouTube channel](https://www.youtube.com/channel/UCxHu4X1zLUkS8amK5EwdBXg) and watch [Minew configuration video](https://www.youtube.com/watch?v=7Qu_LLbRtRw).
* **April** Brothers: One of the easy to use gateways that you can configure it easily to send data. You can watch [April Brothers configuration video](https://www.youtube.com/watch?v=Pm5w7AYxl7Y) in [uBeac YouTube channel](https://www.youtube.com/channel/UCxHu4X1zLUkS8amK5EwdBXg) to learn how to configure it.
* **Blue Cats**: Is one of the top powerful gateways in the market. This gateway has lots of settings and makes you be able to send data over HTTP(s) and MQTT(s) protocols. You can go to [uBeac YouTube channel](https://www.youtube.com/channel/UCxHu4X1zLUkS8amK5EwdBXg) and watch [Blue Cats configuration video](https://www.youtube.com/watch?v=COH1n5OJoZ8).
* **Mist**: Is a versatile and powerful gateway that contains a lot of features and makes user be able to customize type of scan sensors and sending data. You can learn how to configure it by watching [configuration video](https://www.youtube.com/watch?v=DLCLJYjQW8g) in [uBeac YouTube channel](https://www.youtube.com/channel/UCxHu4X1zLUkS8amK5EwdBXg).
* **Jaalee**: You can easily configure this gateway by watching [related video](https://www.youtube.com/watch?v=WQUH05EvFmU) in [uBeac YouTube channel](https://www.youtube.com/channel/UCxHu4X1zLUkS8amK5EwdBXg).

## 2. Software gateways

* **Android applications**

    1. **Beacon Scanner**: Is an android application that scans all the sensors in the environment and sends to URL that you defined in it. To watch the [configuration video](https://www.youtube.com/watch?v=aLSFwgzvV9k), you can check the [uBeac YouTube channel](https://www.youtube.com/channel/UCxHu4X1zLUkS8amK5EwdBXg).
    2. **Data Collector**: This gateway scans the environment by cellphone’s sensors and sends that data to URL that defined in it. To know how to configure it you can watch [related video](https://www.youtube.com/watch?v=NpS9KnUspHk) in [uBeac YouTube channel](https://www.youtube.com/channel/UCxHu4X1zLUkS8amK5EwdBXg).
    3. **Ruuvi Station**: This application scans all Ruuvi sensors in environment and sends data to URL that defined in it. You can watch [configuration video](https://www.youtube.com/watch?v=fxAouF6eUpo) in [uBeac YouTube channel](https://www.youtube.com/channel/UCxHu4X1zLUkS8amK5EwdBXg) to know how to configure it.

* **uBeac Generic Gateways**

    1. **SingleDevice.SingleSensor**

       This gateway is utilized to get data for a specific sensor in each request. For example, in each request you can send temperature, humidity or other data types.[Download sample Postman file](https://cdn.ubeac.io/repo/uBeac.postman_collection.json). <a href="https://cdn.ubeac.io/repo/uBeac.postman_collection.json" download>Download sample Postman file</a>
       To parse the request correctly, you need to send data in this structure:  
       ```javascript
        {
            "mac": "1A:2A:3A:4A:5A:6A",
            "Type": 2,
            "ts": 1542326605,
            "unit": 30,
            "prefix": 0,
            "data": 123
        }
        ```
        **mac** : This shows the device mac or unique address. You can also use *"id", "uid", "name", "title" and "ip"* instead of that.

        **Type** : This Is a code that shows the type of sensor. Each sensor has a type number and a name. you need to put the type number to indicate the type of sensor. To know more about sensor types, you can refer to [SensorType list](./SensorTypes.md).

        **ts** : This shows the time that sensor sends data. This could be dateTime or timeStamp value. If you want to send [timestamp](https://en.wikipedia.org/wiki/Timestamp), you need to use *"ts" or "timestamp"* and if you want to send dateTime you need to use *"dt", "date", "datetime", "time"* instead of that. If you use both of them, the first one will replace by second one.

        **unit** : This is a code that shows the unit of data that should be considered in uBeac panel. For example, if you send temperature data, this can be a number related to centigrade or Fahrenheit. To know more about sensor units, you can refer to [unit list](./SensorUnits.md).

        **prefix** : This is a code that shows the scale of data. For example, for sending proximity data, unit can be meter and prefixes can be *milli, centi, kilo, hecto* and etc. Therefore, you need to select proper prefix from [prefix list](./UnitPrefixes.md).

        **data** : This shows the value(s) that sent from sensor. Sensor can send a single value like temperature or multiple values like GPS data which contains 2 or 3 fields. Both are accepted as below; you also can use *"item", "items", "value", "values"* instead of "data":

        ```javascript
        "data":
        {
            "lat": 123,
            "long": 123,
            "alt": 123
        }

        OR just

        "data" : 123
        ```
        It is also possible for you to do not send the *unit and prefix* to decrease the size of payload. Then you can go to uBeac panel and in device list, define them.

    2. **SingleDevice.MultipleSensor**

        This gateway is utilized to get data from multiple sensors in each request. For example, each request contains data from one device that contains, data from a temperature, humidity, proximity and some other sensors together.[Download sample Postman file](https://cdn.ubeac.io/repo/uBeac.postman_collection.json).
        To parse the request correctly, you need to send data in a specific format as below:

        ```javascript
        {
            "ip": "1A:2A:3A:4A:5A:6A",
            "ts": 1542326605,
            "sensors": [
                {
                "uid": "SignalStrength",
                "unit": 1,
                "prefix": 0,
                "Type": 2,
                "data": {
                    "rssi": -86,
                    "txPower": -59
                }
                },
                {
                "uid": "Temperature",
                "unit": 1,
                "prefix": 0,
                "Type": 3,
                "value": -59
                }
            ]
        }
        ```

        This request contains some properties related to device and array which contains sensors data. Now let’s describe each property:

        **mac** : This shows the device mac or unique address. You can also use *"id", "uid", "name", "title" and "ip"* instead of that.

        **ts** : This shows the time that sensor sends data. This could be dateTime or timeStamp value. If you want to send [timestamp](https://en.wikipedia.org/wiki/Timestamp), you need to use *"ts" or "timestamp"* and if you want to send dateTime you need to use *"dt", "date", "datetime", "time"* instead of that. If you use both of them, the first one will replace by second one.

        **sensors** : This indicates the list of sensors data and contains an array of sensor data. You can also use *"data", "item", "items", "value", "values" and "sensor"* instead of that.

        **uid** : This shows the name of sensor like *"Temperature", "Humidity", "Location"* and etc. You can also use *"id", "uid", "name", "title" and "ip"* instead of that.

        **Type** : This is a code that shows the type of sensor. Each sensor has a type number and a name. you need to put the type number to indicate the type of sensor. To know more about sensor types, you can refer to [SensorType list](./SensorTypes.md).

        **unit** : This is a code that shows the unit of data that should be considered in uBeac panel. For example, if you send temperature data, this can be a number related to centigrade or Fahrenheit. To know more about sensor units, you can refer to [unit list](./SensorUnits.md).

        **prefix** : This is a code that shows the scale of data. For example, for sending proximity data, unit can be meter and prefixes can be *milli, centi, kilo, hecto* and etc. Therefore, you need to select proper prefix from [prefix list](./UnitPrefixes.md).

        **data** : This shows the value(s) that sent from sensor. Sensor can send a single value like temperature or multiple values like GPS data which contains 2 or 3 fields. Both are accepted as below; you also can use *"item", "items", "value", "values" instead of "data"*:

        ```javascript
        "data":
        {
            "lat": 123,
            "long": 123,
            "alt": 123
        }

        OR just

        "data": 123
        ```
        It is also possible for you to do not send the *unit and prefix* to decrease the size of payload. Then you can go to uBeac panel and in device list, define them.

    3. **MultipleDevice.MultipleSensor**

        This gateway is utilized to get data from multiple devices in each request. For example, each request can contain, data from multiple devices that each one can contains some sensor data like a temperature, humidity, proximity and some other sensors together.[Download sample Postman file](https://cdn.ubeac.io/repo/uBeac.postman_collection.json).

        To parse the request correctly, you need to send data in a specific format as below:

        ```javascript
        [
            {
            "ip": "1A:2A:3A:4A:5A:6A",
            "ts": 1542326605,
            "sensors": [
                {
                "uid": "SignalStrength",
                "unit": 1,
                "prefix": 0,
                "Type": 2,
                "data": {
                "rssi": -86,
                "txPower": -59
                    }
                },
                {
                "uid": "Temperature",
                "unit": 2,
                "prefix": 0,
                "Type": 3,
                "value": 26
                }
            ]
        },
        {
            "mac": "1B:2B:3B:4B:5B:6B",
            "ts": 1542326605,
            "sensors": [
            {
                "uid": "SignalStrength",
                "unit": 1,
                "prefix": 0,
                "Type": 2,
                "data": {
                "rssi": -86,
                "txPower": -59
                }
            },
            {
                "uid": "Temp",
                "unit": 2,
                "prefix": 0,
                "Type": 3,
                "value": 39
            }
            ]
        }
        ]
        ```

        This request contains an array of devices and each device can contains multiple sensors. Each object, contains some properties related to a device and an array which contains sensors data. Now let’s describe each property:

        **mac** : This shows the gateway mac or unique address. You can also use *"id", "uid", "name", "title" and "ip"* instead of that.

        **ts** : This shows the time that sensor sends data. This could be dateTime or timeStamp value. If you want to send [timestamp](https://en.wikipedia.org/wiki/Timestamp), you need to use *"ts" or "timestamp"* and if you want to send dateTime you need to use *"dt", "date", "datetime", "time"* instead of that. If you use both of them, the first one will replace by second one.

        **sensors** : This indicates the list of sensors data and contains an array of sensor data. You can also use *"data", "item", "items", "value", "values" and "sensor"* instead of that.

        **uid** : This shows the name of sensor like *"Temperature", "Humidity", "Location"* and etc. You can also use *"id", "uid", "name", "title" and "ip"* instead of that.

        **Type** : This is a code that shows the type of sensor. Each sensor has a type number and a name. you need to put the type number to indicate the type of sensor. To know more about sensor types, you can refer to [SensorType list](./SensorTypes.md).

        **unit** : This is a code that shows the unit of data that should be considered in uBeac panel. For example, if you send temperature data, this can be a number related to centigrade or Fahrenheit. To know more about sensor units, you can refer to [unit list](./SensorUnits.md).

        **prefix** : This is a code that shows the scale of data. For example, for sending proximity sensor data, unit can be meter and prefixes can be *Milli, Centi, Kilo, Hecto* and etc. Therefore, you need to select proper prefix from [prefix list](./UnitPrefixes.md).

        **data** : This shows the value(s) that sent from sensor. Sensor can send a single value like temperature or multiple values like GPS data which contains 2 or 3 fields. Both are accepted as below; you also can use *"item", "items", "value", "values"* instead of "data":

        ```javascript
        "data":
        {
            "lat": 123,
            "long": 123,
            "alt": 123
        }

        OR just

        "data": 123
        ```
        It is also possible for you to do not send the *unit and prefix* to decrease the size of payload. Then you can go to uBeac panel and in device list, define them.

* **HTTP clients**

    1. **Postman**: You can easily use it to send HTTP(s) requests to uBeac. To do that you can add a [uBeac Generic Gateway Single Sensor](./GatewayList.md#2-software-gateways) (or any other gateways), into your panel and put its URL in Postman. You can choose GET, POST, PUT or PATCH request method, set “Content-Type” in request Headers as “application/json”. Then you can put request body to send a temperature as below:  
      This data shows 27°c temperature. For more information, visit uBeac Generic Gateways.  
        ```javascript
        {  
            "mac": "Sample MAC address",  
            "Type": 4,  
            "dateTime": "2019-01-30 13:44:33",
            "unit": 1,
            "prefix": 0,
            "data": 27
        }
        ```

* **MQTT clients**

    You can set up your [MQTT(s)](./uBeacProtocols.md#mqtt-protocol-and-methods) client to publish data to uBeac. To know how to do that, you can visit Getting started with MQTT page. Here we have a quick view on how to send data with a MQTT client:
    1. **MQTTLens**: Is one of the most popular MQTT clients. To set your gateway in this application, create a new connection, you can name it whatever you want, set URL to `hub.ubeac.io` and set the port to 1883 or 8883 then press create connection button. In next window in publish part, put your unique address as Topic and put the json below as a temperature data.

        ```javascript
        {
            "mac": "Sample MAC address",
            "Type": 4,
            "dateTime": "2019-01-30 13:44:33",
            "unit": 1,
            "prefix": 0,
            "data": 27
        }
        ```
        By publish this request you should be able to see that in your gateway detail page.
