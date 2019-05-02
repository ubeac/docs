# uBeac Prtocols

We have provided different ways to communicate with uBeac. You can set your devices to communicate with uBeac over [HTTP(s)](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) and [MQTT(s)](http://mqtt.org/). We also provided this feature to communicate securely with uBeac over [SSL](https://en.wikipedia.org/wiki/SSL) and [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security).

## HTTP Protocol and Methods

The main protocol for transferring data in the internet is [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol). It is easily possible to secure data over this infrastructure by using [SSL](https://en.wikipedia.org/wiki/SSL) certificate. You can send data or set your devices to send data to uBeac over HTTP or HTTPS. The methods you can use to send data are *GET*, *POST*, *PUT*, *PATCH*. All of these request methods are acceptable by the **uBeac platform**.

HTTP is a *request/response* protocol. this means that every request that you send is answered by the server. This response includes a number (response code) and a body. For example, when you make a request to retrieve a file on a webpage (e.g. "Get me the file 'webside.html' “), you send a GET request. If the request is correct, the server will typically return a response with code *200*, along with the file that is requested (body).

Under the same logic, when a device sends a *POST* request to the uBeac’s server (i.e. sending the last value of a sensor), then the server sends back a response with the status of the request (response code), and a body, which would be the result of process.

An HTTP request also needs the parameters below:

* **Host**: Domain name or IP address that you want to send the request to.
* **Path**: This is typically the remaining portion of the URL that specifies the page, method or resource you want to consume. For example, if a gateway URL is: hub.ubeac.io/abcdefg then the path would be /abcdefg.
* **Headers**: Define the operating parameters of the HTTP request such as authentication, Content-Type, Content-Length, etc.
* **Body/Payload**: In the case of POST, PUT or PATCH requests, this is the data sent by your device to the server. GET requests typically do not have a body because they are meant to request data, not to send data.

By creating a gateway, you will get a unique URL (path) to send your devices and sensors data to your gateway. We have also provided some different security options for you to use in your HTTP(s) requests.
These features are as below:

1. **Using ‘username’ and ‘password’**: It is provided in uBeac for you to define a username and password in your gateway for your devices, set it in your request headers and send to uBeac. You just need to add a “username” and a “password” record in your request header. Only requests with correct username and password will be accepted by uBeac.

2. **Protocol Restriction**: It is provided in uBeac for you to restrict the communication protocols. There are for different protocols for you to choose, “HTTP”,” HTTPS”,” MQTT” and” MQTTS”. Only requests with selected protocols will be accepted by uBeac.

3. **IP Restriction**: It is provided in uBeac for you to creat whitelists or blacklists of IPs to get request only from trusted devices. In your gateway page you can define a specific IP or a range IP as allow or deny. By defining that as allow, only IP in that range will be accepted and set that as deny, Those IPs will be rejected.

    You can define IPs as wildcard like 192.468.0.* or a range of IPs using ‘/’ or ‘-‘ delimiter, like

        192.168.0.1-120,
        192.168.0.1/120,
        192.168.0.1-192.168.10.1,
        192.168.0.1/192.168.10.1 and etc.

    All of those IPs can be defined as Allowed or Denied.

## MQTT Protocol and Methods

[MQTT](http://mqtt.org/) is a machine-to-machine (M2M)/"Internet of Things" connectivity protocol. It was designed as an extremely lightweight *publish/subscribe* messaging transport. It is useful for connections with remote locations where a small code footprint is required and/or network bandwidth is at a premium.

A device state is likely the most commonly published message. When thinking in terms of sensor data, the device state is typically the value of one or more sensors. The time property is optional - when it is not included, uBeac assumes that the reported state is for the current time.

By creating a gateway, you will get a unique URL (path) (e.g. hub.ubeac.io/abcdefg) to send your devices and sensors data to your gateway. The topic you need to use in your devices to publish data is “abcdefg” and the URLs that you can use in your devices are as below:

`“mqtt(tcp)://hub.ubeac.io/” on port “1883”`

`“mqtts(tcp)://hub.ubeac.io/” on port “8883”`

We have also provided some different security options for you to use in your HTTP(s) requests.
These features are as below:

1. **Using ‘username’ and ‘password’**: It is provided in uBeac for you to define a username and password in your gateway for your devices, set it in your MQTT client and send to uBeac. Only requests with correct username and password will be accepted by uBeac.

2. **Protocol Restriction**: It is provided in uBeac for you to restrict the communication protocols. There are for different protocols for you to choose, “HTTP”,”HTTPS”,” MQTT” and” MQTTS”. Only requests with selected protocols will be accepted by uBeac.

3. **IP Restriction**: It is provided in uBeac for you to create whitelists or blacklists of IPs to get request only from trusted devices. In your gateway page you can define a specific IP or a range IP as allowed or denied. By defining that as allow, only IP in that range will be accepted and set that as deny, Those IPs will be rejected.

    You can define IPs as wildcard like 192.468.0.* or a range of IPs using ‘/’ or ‘-‘ delimiter, like

        192.168.0.1-120,
        192.168.0.1/120,
        192.168.0.1-192.168.1.1,
        192.168.0.1/192.168.1.1 and etc.

    All of those IPs can be defined as Allowed or Denied.