# Walkthrough with uBeac

Before we start, lets explore some definitions in uBeac ecosystem:

**Team**: An individual, a group within a company, or a collection of individuals from different companies who are working as a team.

**Gateway**: Hardware or software (even a simple http client) which can send sensor data to the uBeac panel.

**Device**: Hardware or software which contains one or more sensors.

With or without a device, you can experience many of the features uBeac provides by following the instructions below.

### 1. Registration

To start your uBeac journey, you need to go to register on the [uBeac website](http://ui.ubeac.io). Register with your email address and set a password (at least 8 characters including at least one upper-case and lower-case letter).

### 2. Confirmation

We will send you an email and ask you to confirm your email address by clicking on a link.

### 3. Creating a team

After registration and logging in to uBeac panel, you need to create a team. HOW? After creating a team, you can define all users which need access to this team and its data. Note that users need to register their email with uBeac before access may be given.

### 4. Creating building and floors

Whether or not you are concerned with location tracking, each team needs to create a building to locate physical gateways and devices digitally. Clicking on the Building tab in the left menu panel will take you to the Building page within which you may edit exisiting buildings or create new buildings. The uBeac panel creates a default floor for each building. By clicking on the Floor List icon on the bottom right of each building, you can edit the default floor and add more floors. You are also able to add floor plans via image upload and locate your gateways on floor plan.

### 5. Creating new gateway

Gateways send data to your uBeac panel. uBeac is designed to process data that is sent by almost any type of gateway. Here is a [list of gateways](./GatewayList.md) that are currently supported by uBeac. You can also use an [HTTP(s)](/uBeacProtocols.md#http-protocol-and-methods) client such as [Insomnia](https://insomnia.rest/), [Postman](https://www.getpostman.com/), [cURL](https://curl.haxx.se/), [HTTPie](https://httpie.org/) or [MQTT(s)](./uBeacProtocols.md#mqtt-protocol-and-methods) client such as [MQTTLens](https://chrome.google.com/webstore/detail/mqttlens/hemojaaeigabkbcookmlgmdigohjobjm?hl=en) or [MQTTBox](http://workswithweb.com/mqttbox.html) to send data to uBeac. This is completely explained in our [list of gateways](./GatewayList.md). To register a gateway, you need to select the manufacturer, product type, and related firmware version for your gateway. You will then be provided with a unique URL that you can set into your device

### 6. Getting data

Your provisioned device will now be sending data to your URL. You can see that raw data in your gateway details page. In this page, by clicking the details icon, a modal window will be shown which has three tabs: Devices, Body and Exceptions. If the gateway’s data was predefined as valid data, in the Devices tab you will be able to see devices and sensors that are detected automatically by uBeac. Otherwise based on raw data that you can see in gateway detail page, you need to define valid devices and sensors in Devices page.

If your device data needs to be validated, it is a simple two-step process. On the Gateway Details page, select your desired device from the raw feed and validate it on the Device page, using its MAC or UUID.

In the Body tab, you can see the request body. In the Exceptions tab, you can see if there are any exceptions during the processing of your request body. In that page you can also see the number of requests, devices and sensors. In the right pane, you can see all the members who have access to this gateway.

### 7. Devices

uBeac is able to detect all devices and sensors automatically from request data (if the gateway’s data was predefined as valid data). In this page you can see those devices. It is also possible for you to define new devices and sensors. In some gateways like Android applications that scan all the sensors in an area and relay the data, only some parts of this data are acceptable. Therefore, you need to define valid devices in this page to get valid data.

### 8. Create your dashboard

By clicking on Dashboard link in left menu pane, you can view your default dashboard. On the top right, you may click on the Add button to create a new dashboard. You can also choose to edit the default dashboard.

To show sample temperature data, you may click on the settings button on the top right of the page. Drag an indicator and drop it in the dashboard. You can define the position for this [widget](#9-widgets) and customize the size. By clicking on the settings button at the top right of the widget or Connect to data button on the bottom left of the widget, you can set the visual and data connection settings on the widget.

First, provide a name and description for your widget. Then, select your device type as well as your sensor (temperature in this example). If you can not see your device or sensor, check the device page or gateway details page to figure out what the problem is. 
You can also select the shape of your indicator, the Min and Max values, and the range of precision. Finally, save the widget and save the dashboard. Data will then appear in your finished widget.

### 9. Widgets

Widgets are tools that you can utilise to monitor and visualize your sensors data. Each widget has a unique shape and specific settings that makes you be able to show your sensor data in you favorite style. 
