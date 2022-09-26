# SwitchBot API v1.1

- [SwitchBot API](#switchbot-api)
  - [Introduction](#introduction)
  - [About the New Version](#about-the-new-version)
  - [Getting Started](#getting-started)
  - [Authentication](#authentication)
    - [Open Token and Secret Key](#open-token-and-secret-key)
    - [How to Sign](#how-to-sign)
  - [Glossary](#glossary)
  - [API Usage](#api-usage)
    - [Host Domain](#host-domain)
    - [Sending a Request](#sending-a-request)
      - [Content-Type](#content-type)
      - [Request limit](#request-limit)
    - [Request Header](#request-header)
    - [Standard HTTP Error Codes](#standard-http-error-codes)
  - [Devices](#devices)
    - [Get device list](#get-device-list)
      - [Description](#description)
      - [Responses](#responses)
      - [Sample](#sample)
        - [Get all devices](#get-all-devices)
    - [Get device status](#get-device-status)
      - [Description](#description)
      - [Path parameters](#path-parameters)
      - [Responses](#responses)
      - [Sample](#sample)
        - [SwitchBot Meter example](#switchbot-meter-example)
        - [SwitchBot Curtain example](#switchbot-curtain-example)
    - [Send device control commands](#send-device-control-commands)
      - [Description](#description)
      - [Command set for physical devices](#command-set-for-physical-devices)
      - [Command set for virtual infrared remote devices](#command-set-for-virtual-infrared-remote-devices)
      - [Path parameters](#path-parameters)
      - [Request body parameters](#request-body-parameters)
      - [Response](#response)
      - [Errors](#errors)
      - [Sample](#sample)
        - [Bot example](#bot-example)
        - [Infrared remote device example](#infrared-remote-device-example)
  - [Scenes](#scenes)
    - [Get scene list](#get-scene-list)
      - [Description](#description)
      - [Response](#response)
      - [Errors](#errors)
      - [Sample](#sample)
        - [Get all scenes](#get-all-scenes)
    - [Execute manual scenes](#execute-manual-scenes)
      - [Description](#description)
      - [Path parameters](#path-parameters)
      - [Errors](#errors)
      - [Sample](#sample)
        - [Execute a scene](#execute-a-scene)
  - [Webhook](#webhook)
    - [Setup webhook](#setup-webhook)
      - [Description](#description)
      - [Request](#request)
        - [Request body parameters](#request-body-parameters)
      - [Response](#response)
    - [Query webhook](#query-webhook)
      - [Description](#description)
      - [Request](#request)
        - [Request body parameters](#request-body-parameters)
        - [queryUrl](#queryurl)
        - [queryDetails](#querydetails)
      - [Response](#response)
        - [queryUrl](#queryurl)
        - [queryDetails](#querydetails)
    - [Update webhook](#update-webhook)
      - [Description](#description)
      - [Request](#request)
        - [Request body parameters](#request-body-parameters)
      - [Response](#response)
    - [Delete webhook](#delete-webhook)
      - [Description](#description)
      - [Request](#request)
        - [Request body parameters](#request-body-parameters)
      - [Response](#response)
    - [Receive events from webhook](#receive-events-from-webhook)
      - [Motion Sensor](#motion-sensor)
      - [Contact Sensor](#contact-sensor)
      - [Meter](#meter)
      - [Meter Plus](#meter-plus)
      - [Lock](#lock)
      - [Indoor Cam](#indoor-cam)
      - [Pan/Tilt Cam](#pantilt-cam)
      - [Color Bulb](#color-bulb)
      - [LED Strip Light](#led-strip-light)
      - [Plug Mini (US)](#plug-mini-us)
      - [Plug Mini (JP)](#plug-mini-jp)

## Introduction
This document describes a collection of SwitchBot API methods, examples, and best practices for, but not limited to, IoT hobbyists, developers, and gurus to make their own smart home programs or applications. 

## About the New Version

We will stop adding support for new products on `v1.0` as we release `v1.1`.

Hence, we strongly recommend all SwitchBot users to migrate to the new API version because we have improved the authentication method. This will make the communication between your server and the SwitchBot server more secure.

## Getting Started
Please follow these steps,
1. Download the SwitchBot app on App Store or Google Play Store
2. Register a SwitchBot account and log in into your account
3. Generate an Open Token within the app
a) Go to Profile > Preference
b) Tap App Version 10 times. Developer Options will show up
c) Tap Developer Options
d) Tap Get Token
4. Roll up your sleeves and get your hands dirty with SwitchBot OpenAPI!

## Authentication
### Open Token and Secret Key

Note: You must update the app to the latest version, `V6.14` or later, in order to get the secret key.

In SwitchBot API `v1.1`, the authentication method has been improved. In order to gain access to private data through the API, you must generate a unique signature using a token and a secret key. When you make a request, the Authorization token and signature will be validated simultaneously.

You as a developer will then be able to add, delete, edit, and look up your data including profile data and data associated with the devices that have been added to your SwitchBot account.

To continue to use SwitchBot API `v1.0`, refer to the legacy document.



### How to Sign?

We have attached a python script for you to quickly generate a sign. If you prefer to write your own script or routine, here is the procedure.

1. Print the 13 digit timestamp and concatenate it with your `token`
2. Create a signature using your `secret` and the string produced in the previous step
3. Convert the signature to upper case



For instance,

```
# secret key
secret = "" # copy and paste from the SwitchBot app V6.14 or later
# open token
token = "" # copy and paste from the SwitchBot app V6.14 or later
t = 1661927531000
sign = HMAC-SHA256(token + t, secret).toUpperCase()
```



Python 2 example code

```python
import time
import hashlib
import hmac
import base64

# open token
token = '' # copy and paste from the SwitchBot app V6.14 or later
# secret key
secret = '' # copy and paste from the SwitchBot app V6.14 or later
nonce = ''
t = int(round(time.time() * 1000))
string_to_sign = '{}{}{}'.format(token, t, nonce)

sign = base64.b64encode(hmac.new(secret, msg=string_to_sign, digestmod=hashlib.sha256).digest())
print ('Authorization: {}'.format(token))
print ('t: {}'.format(t))
print ('sign: {}'.format(sign))
print ('nonce: {}'.format(nonce))

```



Python 3 example code

```python
import time
import hashlib
import hmac
import base64

# open token
token = '' # copy and paste from the SwitchBot app V6.14 or later
# secret key
secret = '' # copy and paste from the SwitchBot app V6.14 or later
nonce = ''
t = int(round(time.time() * 1000))
string_to_sign = '{}{}{}'.format(token, t, nonce)

string_to_sign = bytes(string_to_sign, 'utf-8')
secret = bytes(secret, 'utf-8')

sign = base64.b64encode(hmac.new(secret, msg=string_to_sign, digestmod=hashlib.sha256).digest())
print ('Authorization: {}'.format(token))
print ('t: {}'.format(t))
print ('sign: {}'.format(str(sign, 'utf-8')))
print ('nonce: {}'.format(nonce))
```



Javasscript example code

```javascript
    const token = "yourToken";
    const secret = "yourSecret";
    const t = Date.now();
    const nonce = "requestID";
    const data = token + t + nonce;
    const signTerm = crypto.createHmac('sha256', secret)
        .update(Buffer.from(data, 'utf-8'))
        .digest();
    const sign = signTerm.toString("base64");
    console.log(sign);

    const body = JSON.stringify({
        "command": "turnOn",
        "parameter": "default",
        "commandType": "command"
    });
    const deviceId = "MAC";
    const options = {
        hostname: 'api.switch-bot.com',
        port: 443,
        path: `/v1.1/devices/${deviceId}/commands`,
        method: 'POST',
        headers: {
            "Authorization": token,
            "sign": sign,
            "nonce": nonce,
            "t": t,
            'Content-Type': 'application/json',
            'Content-Length': body.length,
        },
    };

    const req = https.request(options, res => {
        console.log(`statusCode: ${res.statusCode}`);
        res.on('data', d => {
            process.stdout.write(d);
        });
    });

    req.on('error', error => {
        console.error(error);
    });

    req.write(body);
    req.end();
```


## Glossary

The following table provides definitions to the terms to be frequently mentioned in the subsequent sections.

| Term                         | Description                                                  |
| ---------------------------- | ------------------------------------------------------------ |
| Hub                          | Generally referred to these devices, SwitchBot Hub Model No. SwitchBot Hub S1/SwitchBot Hub Mini Model No. W0202200/SwitchBot Hub Plus Model No. SwitchBot Hub S1 |
| Hub Mini                     | Short for SwitchBot Hub Mini Model No. W0202200              |
| Hub Plus                     | Short for SwitchBot Hub Plus Model No. SwitchBot Hub S1      |
| Bot                          | Short for SwitchBot Bot Model No. SwitchBot S1               |
| Curtain                      | Short for SwitchBot Curtain Model No. W0701600               |
| Plug                         | Short for SwitchBot Plug Model No. SP11                      |
| Meter                        | Short for SwitchBot Thermometer and Hygrometer Model No. SwitchBot MeterTH S1 |
| Meter Plus (JP)              | Short for SwitchBot Thermometer and Hygrometer Plus (JP) Model No. W2201500 |
| Meter Plus (US)              | Short for SwitchBot Thermometer and Hygrometer Plus (US) Model No. W2301500 |
| Motion Sensor                | Short for SwitchBot Motion Sensor Model No. W1101500         |
| Contact Sensor               | Short for SwitchBot Contact Sensor Model No. W1201500        |
| Color Bulb                   | Short for SwitchBot Color Bulb Model No. W1401400            |
| Smart Fan                    | Short for SwitchBot Smart Fan Model No. W0601100             |
| Strip Light                  | Short for SwitchBot LED Strip Light Model No. W1701100       |
| Plug Mini (US)               | Short for SwitchBot Plug Mini (US) Model No. W1901400        |
| Plug Mini (JP)               | Short for SwitchBot Plug Mini (JP) Model No. W2001400        |
| Lock                         | Short for SwitchBot Lock Model No. W1601700                  |
| Robot Vacuum Cleaner S1      | Short for SwitchBot Robot Vacuum Cleaner S1 Model No. W3011000; currently only available in Japan |
| Robot Vacuum Cleaner S1 Plus | Short for SwitchBot Robot Vacuum Cleaner S1 Plus Model No. W3011010; currently only available in Japan |
| Cloud Service                | An SwitchBot app feature that 1. enables SwitchBot products to be discovered and communicated with third-party services voice control services, 2. allows users to create customized smart scenes and Android widgets. For BLE-based devices such as Bot and Curtain, you MUST first add a Hub/Hub Mini/Hub Plus and then enable Cloud Service on the Settings page in order to make use of the web API! |



## API Usage
### Host Domain
```
https://api.switch-bot.com
```

### Sending a Request
The following request types are supported,
- GET
- PUT
- POST
- DELETE

#### Content-Type
For `POST` requests, use `application/json; charset=utf8` as the `Content-Type`

#### Request limit
The amount of API calls per day is limited to **10000** times. Going over that limit will return "Unauthorized."

### Request Header

The following parameters need to be included into the header,

| Parameter     | Type   | Location | Required | Description                                                  |
| ------------- | ------ | -------- | -------- | ------------------------------------------------------------ |
| Authorization | String | header   | Yes      | Open Token acquired                                          |
| sign          | String | header   | Yes       | A signature generated from the token and secret key using a specific algorithm. |
| t             | Long   | header   | Yes       | A 13 digit timestamp (standard time). |
| nonce             | Long   | header   | Yes       | A random UUID generated by developers themselves to blend into the string to sign. |

### Standard HTTP Error Codes

The following table lists the most common HTTP error response,

| Code | Name                   | Description                                                  |
| :--- | :--------------------- | :----------------------------------------------------------- |
| 400  | Bad Request            | The client has issued an invalid request. This is commonly used to specify validation errors in a request payload. |
| 401  | Unauthorized           | Authorization for the API is required, but the request has not been authenticated. |
| 403  | Forbidden              | The request has been authenticated but does not have appropriate permissions, or a requested resource is not found. |
| 404  | Not Found              | Specifies the requested path does not exist.                 |
| 406  | Not Acceptable         | The client has requested a MIME type via the Accept header for a value not supported by the server. |
| 415  | Unsupported Media Type | The client has defined a contentType header that is not supported by the server. |
| 422  | Unprocessable Entity   | The client has made a valid request, but the server cannot process it. This is often used for APIs for which certain limits have been exceeded. |
| 429  | Too Many Requests      | The client has exceeded the number of requests allowed for a given time window. |
| 500  | Internal Server Error  | An unexpected error on the SmartThings servers has occurred. These errors should be rare. |





## Devices

The devices API is used to access the properties and states of SwitchBot devices and to send control commands to those devices.

### Get device list
```http
GET /v1.1/devices
```

#### Description
Get a list of devices, which include physical devices and virtual infrared remote devices that have been added to the current user's account.

Physical devices refer to the following SwitchBot products,
 -  Hub
 -  Hub Plus
 -  Hub Mini
 -  Bot (MUST enable Cloud Service first)
 -  Curtain (MUST enable Cloud Service first)
 -  Plug
 -  Meter (MUST enable Cloud Service first)
 -  Motion Sensor (MUST enable Cloud Service first)
 -  Contact Sensor (MUST enable Cloud Service first)
 -  Color Bulb
 -  Humidifier
 -  Smart Fan
 -  Strip Light
 -  Plug Mini (US)
 -  Plug Mini (JP)
 -  Lock
 -  Meter Plus (JP) (MUST enable Cloud Service first)
 -  Meter Plus (US) (MUST enable Cloud Service first)
 -  `new` Robot Vacuum Cleaner S1
 -  `new` Robot Vacuum Cleaner S1 Plus

Virtual infrared remote devices refer to virtual devices that are used to simulate infrared signals of a home appliance remote control. A SwitchBot Hub Plus / Hub Mini is required in order to be able to create these virtual devices within the app. The types of appliances supported include,
 -  Air Conditioner
 -  TV
 -  Light
 -  IPTV/Streamer
 -  Set Top Box
 -  DVD
 -  Fan
 -  Projector
 -  Camera
 -  Air Purifier
 -  Speaker
 -  Water Heater
 -  Vacuum Cleaner
 -  Others

#### Responses

The response is basically a JSON object, which contains the following properties,

| Key Name   | Value Type   |
| ---------- | ------------ |
| statusCode | Integer      |
| message    | String       |
| body       | Object<body> |

The body object contains the following properties,

| Key Name           | Value Type            | Description                               |
| ------------------ | --------------------- | ----------------------------------------- |
| deviceList         | Array<device>         | a list of physical devices                |
| infraredRemoteList | Array<infraredRemote> | a list of virtual infrared remote devices |

The deviceList array contains a list of objects with the following key-value attributes,

| Key                | Value Type      | Description                                                  |
| ------------------ | --------------- | ------------------------------------------------------------ |
| deviceId           | String          | device ID                                                    |
| deviceName         | String          | device name                                                  |
| deviceType         | String          | device type                                                  |
| enableCloudService | Boolean         | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String          | device's parent Hub ID                                       |
| curtainDevicesIds  | Array<deviceId> | only available for Curtain devices. a list of Curtain device IDs such that the Curtain devices are being paired or grouped |
| calibrate          | Boolean         | only available for Curtain/Lock devices. determines if the open position and the close position of a device have been properly calibrated or not |
| group              | Boolean         | only available for Curtain devices. determines if a Curtain is paired with or grouped with another Curtain or not |
| master             | Boolean         | only available for Curtain devices. determines if a Curtain is the master device or not when paired with or grouped with another Curtain |
| openDirection      | String          | only available for Curtain devices. the opening direction of a Curtain |

The infraredRemoteList array contains a list of objects with the following key-value attributes,
| Key         | Value Type | Description                   |
| ----------- | ---------- | ----------------------------- |
| deviceId    | String     | device ID                     |
| deviceName  | String     | device name                   |
| remoteType  | String     | device type                   |
| hubDeviceId | String     | remote device's parent Hub ID |

The response may contain the following codes and messages,

| Status Code | Body Content       | Message      | Description                                                  |
| ----------- | ------------------ | ------------ | ------------------------------------------------------------ |
| 100         | Device list object | success      | Returns an object that contains two device lists             |
| n/a         | n/a                | Unauthorized | Http 401 Error. User permission is denied due to invalid token. |
| 190         | n/a                | System error | Device internal error due to device states not synchronized with server |

#### Sample

##### Get all devices

Request

```http
GET https://api.switch-bot.com/v1.1/devices
```

Response

```js
{
    "statusCode": 100,
    "body": {
        "deviceList": [
            {
                "deviceId": "500291B269BE",
                "deviceName": "Living Room Humidifier",
                "deviceType": "Humidifier",
                "enableCloudService": true,
                "hubDeviceId": "000000000000"
            }
        ],
        "infraredRemoteList": [
            {
                "deviceId": "02-202008110034-13",
                "deviceName": "Living Room TV",
                "remoteType": "TV",
                "hubDeviceId": "FA7310762361"
            }
        ]
    },
    "message": "success"
}
```


### Get device status
```http
GET /v1.1/devices/{deviceId}/status
```

#### Description
Get the status of a physical device that has been added to the current user's account.

Physical devices refer to the following SwitchBot products,

 -  Bot
 -  Plug
 -  Curtain
 -  Meter
 -  Motion Sensor
 -  Contact Sensor
 -  Color Bulb
 -  Humidifier
 -  Smart Fan
 -  Strip Light
 -  Plug Mini (US)
 -  Plug Mini (JP)
 -  Lock
 -  Meter Plus (JP)
 -  Meter Plus (US)
 -   `new` Robot Vacuum Cleaner S1
 -   `new` Robot Vacuum Cleaner S1 Plus

#### Path parameters

| Name     | Type   | Required | Description |
| -------- | ------ | -------- | ----------- |
| deviceId | String | Yes      | device ID   |

#### Responses
The response is basically a JSON object, which contains the following properties,

| Key Name   | Value Type   |
| ---------- | ------------ |
| statusCode | Integer      |
| message    | String       |
| body       | Object<body> |

body object contains the following properties,
| Key                    | Value Type | Used by Products                                     | Description                                                  |
| ---------------------- | ---------- | ---------------------------------------------------- | ------------------------------------------------------------ |
| deviceId               | String     | All                                                  | device ID                                                    |
| deviceType             | String     | All                                                  | device type                                                  |
| hubDeviceId            | String     | All                                                  | device's parent Hub ID                                       |
| power                  | String     | Bot/Plug/Humidifier/Color Bulb/Strip Light/Plug Mini | ON/OFF state                                                 |
| humidity               | Integer    | Meter/Meter Plus/Humidifier                          | humidity percentage                                          |
| temperature            | Float      | Meter/Meter Plus/Humidifier                          | temperature in celsius                                       |
| nebulizationEfficiency | Integer    | Humidifier                                           | atomization efficiency %                                     |
| auto                   | Boolean    | Humidifier                                           | determines if a Humidifier is in Auto Mode or not            |
| childLock              | Boolean    | Humidifier                                           | determines if a Humidifier's safety lock is on or not        |
| sound                  | Boolean    | Humidifier                                           | determines if a Humidifier is muted or not                   |
| calibrate              | Boolean    | Curtain/Lock                                         | determines if a device has been calibrated or not            |
| group                  | Boolean    | Curtain                                              | determines if a Curtain is paired with or grouped with another Curtain or not |
| moving                 | Boolean    | Curtain                                              | determines if a Curtain is moving or not                     |
| slidePosition          | Integer    | Curtain                                              | the percentage of the distance between the calibrated open position and closed position that Curtain has traversed |
| mode                   | Integer    | Smart Fan                                            | fan mode                                                     |
| speed                  | Integer    | Smart Fan                                            | fan speed                                                    |
| shaking                | Boolean    | Smart Fan                                            | determines if the fan is swinging or not                     |
| shakeCenter            | Integer    | Smart Fan                                            | the fan's swing direciton                                    |
| shakeRange             | Integer    | Smart Fan                                            | the fan's swing range, 0~120°                                |
| moveDetected           | Boolean    | Motion Sensor/Contact Sensor                         | determines if motion is detected                             |
| brightness             | String     | Motion Sensor/Contact Sensor                         | if the ambient environment is bright or dim                  |
| openState              | String     | Contact Sensor                                       | open/close/timeOutNotClose                                   |
| brightness             | Integer    | Color Bulb/Strip Light                               | the brightness value, range from 1 to 100                    |
| color                  | String     | Color Bulb/Strip Light                               | the color value, RGB "255:255:255"                           |
| colorTemperature       | Integer    | Color Bulb                                           | the color temperature value, range from 2700 to 6500         |
| lackWater              | Boolean    | Humidifier                                           | determines if the water tank is empty or not                 |
| voltage                | Float      | Plug Mini                                            | Current voltage of the device (Unit: V)                      |
| weight                 | Float      | Plug Mini                                            | the power consumption of the device for the day (Unit: W/min) |
| electricityOfDay       | Integer    | Plug Mini                                            | How long the device has been used for the day (Unit: min)    |
| electricCurrent        | Float      | Plug Mini                                            | current of the device (Unit: A) at the moment                |
| lockState              | String     | Lock                                                 | determines if the lock is locked or not                      |
| doorState              | String     | Lock                                                 | determines if the door is closed or not                      |
| workingStatus          | String     | Robot Vacuum Cleaner S1/ S1 Plus                     | the working status of the device, e.g. Cleaning, Paused      |
| onlineStatus           | String     | Robot Vacuum Cleaner S1/ S1 Plus                     | determines if the device is online or offline                |
| battery                | Integer    | Robot Vacuum Cleaner S1/ S1 Plus                     | the battery level                                            |

The reponses may contain the following codes and message,

| Status Code | Body Content       | Message      | Description                                                  |
| ----------- | ------------------ | ------------ | ------------------------------------------------------------ |
| 100         | Device list object | success      | Returns an object that contains two device lists             |
| n/a         | n/a                | Unauthorized | Http 401 Error. User permission is denied due to invalid token. |
| 190         | n/a                | System error | Device internal error due to device states not synchronized with server |

#### Sample

##### SwitchBot Meter example

Request the status of a SwitchBot Thermometer and Hygrometer

Request

```http
GET https://api.switch-bot.com/v1.1/devices/C271111EC0AB/status
```

Response


```js
{
    "statusCode": 100,
    "body": {
        "deviceId": "C271111EC0AB",
        "deviceType": "Meter",
        "hubDeviceId": "FA7310762361",
        "humidity": 52,
        "temperature": 26.1
    },
    "message": "success"
}
```

##### SwitchBot Curtain example

Request the status of a SwitchBot Curtain

Request

```http
GET https://api.switch-bot.com/v1.1/devices/E2F6032048AB/status
```

Response


```js
{
    "statusCode": 100,
    "body": {
        "deviceId": "E2F6032048AB",
        "deviceType": "Curtain",
        "hubDeviceId": "FA7310762361",
        "calibrate": true,
        "group": false,
        "moving": false,
        "slidePosition": 0
    },
    "message": "success"
}
```



### Send device control commands

```http
POST /v1.1/devices/{deviceId}/commands
```

#### Description

Send control commands to physical devices and virtual infrared remote devices.

#### Command set for physical devices

The table below describes all the available commands for physical devices,

| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Bot                          | command     | turnOff             | default                                                      | set to OFF state                                             |
| Bot                          | command     | turnOn              | default                                                      | set to ON state                                              |
| Bot                          | command     | press               | default                                                      | trigger press                                                |
| Plug                         | command     | turnOn              | default                                                      | set to ON state                                              |
| Plug                         | command     | turnOff             | default                                                      | set to OFF state                                             |
| Curtain                      | command     | setPosition         | index0,mode0,position0<br />e.g. `0,ff,80`                   | mode: 0 (Performance Mode), 1 (Silent Mode), ff (default mode) <br />position: 0~100 (0 means opened, 100 means closed) |
| Curtain                      | command     | turnOff             | default                                                      | equivalent to set position to 100                            |
| Curtain                      | command     | turnOn              | default                                                      | equivalent to set position to 0                              |
| Humidifier                   | command     | turnOff             | default                                                      | set to OFF state                                             |
| Humidifier                   | command     | turnOn              | default                                                      | set to ON state                                              |
| Humidifier                   | command     | setMode             | `auto` or `101` or<br />  `102` or `103` or `{0~100}`        | auto, set to Auto Mode,<br />101, set atomization efficiency to 34%,<br />102, set atomization efficiency to 67%,<br />103, set atomization efficiency to 100% |
| Smart Fan                    | command     | turnOn              | default                                                      | set to ON state                                              |
| Smart Fan                    | command     | turnOff             | default                                                      | set to OFF state                                             |
| Smart Fan                    | command     | setAllStatus        | power,fanMode,<br />fanSpeed,shakeRange<br/>e.g. `on,1,1,60` | power: off/on,<br />fanMode: 1/2,<br />fanSpeed: 1/2/3/4,<br />shakeRange: 0~120<br/>fanMode: 1 (Standard), 2 (Natural) |
| Color Bulb                   | command     | turnOn              | default                                                      | set to ON state                                              |
| Color Bulb                   | command     | turnOff             | default                                                      | set to OFF state                                             |
| Color Bulb                   | command     | toggle              | default                                                      | toggle state                                                 |
| Color Bulb                   | command     | setBrightness       | `{1-100}`                                                    | set brightness                                               |
| Color Bulb                   | command     | setColor            | `"{0-255}:{0-255}:{0-255}"`                                  | set RGB color value                                          |
| Color Bulb                   | command     | setColorTemperature | `{2700-6500}`                                                | set color temperature                                        |
| Strip Light                  | command     | turnOn              | default                                                      | set to ON state                                              |
| Strip Light                  | command     | turnOff             | default                                                      | set to OFF state                                             |
| Strip Light                  | command     | toggle              | default                                                      | toggle state                                                 |
| Strip Light                  | command     | setBrightness       | `{1-100}`                                                    | set brightness                                               |
| Strip Light                  | command     | setColor            | `"{0-255}:{0-255}:{0-255}"`                                  | set RGB color value                                          |
| Plug Mini (US/JP)            | command     | turnOn              | default                                                      | set to ON state                                              |
| Plug Mini (US/JP)            | command     | turnOff             | default                                                      | set to OFF state                                             |
| Plug Mini (US/JP)            | command     | toggle              | default                                                      | toggle state                                                 |
| Robot Vacuum Cleaner S1      | command     | start               | default                                                      | start vacuuming                                              |
| Robot Vacuum Cleaner S1      | command     | stop                | default                                                      | stop vacuuming                                               |
| Robot Vacuum Cleaner S1      | command     | dock                | default                                                      | return to charging dock                                      |
| Robot Vacuum Cleaner S1      | command     | PowLevel            | `{0-3}`                                                      | set suction power level: 0 (Quiet), 1 (Standard), 2 (Strong), 3 (MAX) |
| Robot Vacuum Cleaner S1 Plus | command     | start               | default                                                      | start vacuuming                                              |
| Robot Vacuum Cleaner S1 Plus | command     | stop                | default                                                      | stop vacuuming                                               |
| Robot Vacuum Cleaner S1 Plus | command     | dock                | default                                                      | return to charging dock                                      |
| Robot Vacuum Cleaner S1 Plus | command     | PowLevel            | `{0-3}`                                                      | set suction power level: 0 (Quiet), 1 (Standard), 2 (Strong), 3 (MAX) |
| Lock                         | command     | lock                | default                                                      | rotate to locked position                                    |
| Lock                         | command     | unlock              | default                                                      | rotate to unlocked position                                  |

#### Command set for virtual infrared remote devices

The table below describes all the available commands for virtual infrared remote devices,

| deviceType                             | commandType | Command                    | command parameter                                            | Description                                                  |
| -------------------------------------- | ----------- | -------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| All home appliance types except Others | ""          | turnOn                     | default                                                      | every home appliance can be turned on by default             |
| All home appliance types except Others | command     | turnOff                    | default                                                      | every home appliance can be turned off by default            |
| Others                                 | `customize` | {user-defined button name} | default                                                      | all user-defined buttons must be configured with commandType=customize |
| Air Conditioner                        | command     | setAll                     | {temperature},{mode},{fan speed},{power state}<br />e.g. `26,1,3,on` | the unit of temperature is in celsius; <br />modes include 1 (auto), 2 (cool), 3 (dry), 4 (fan), 5 (heat); <br />fan speed includes 1 (auto), 2 (low), 3 (medium), 4 (high); <br />power state includes on and off |
|                                        |             |                            |                                                              |                                                              |
| TV, IPTV/Streamer,  Set Top Box        | command     | SetChannel                 | {channel number}, e.g. 15                                    | set the TV channel to switch to                              |
|                                        | command     | volumeAdd                  | default                                                      | volume up                                                    |
|                                        | command     | volumeSub                  | default                                                      | volume down                                                  |
|                                        | command     | channelAdd                 | default                                                      | next channel                                                 |
|                                        | command     | channelSub                 | default                                                      | previous channel                                             |
| DVD, Speaker                           | command     | setMute                    | default                                                      | mute/unmute                                                  |
|                                        | command     | FastForward                | default                                                      | fast forward                                                 |
|                                        | command     | Rewind                     | default                                                      | rewind                                                       |
|                                        | command     | Next                       | default                                                      | next track                                                   |
|                                        | command     | Previous                   | default                                                      | last track                                                   |
|                                        | command     | Pause                      | default                                                      | pause                                                        |
|                                        | command     | Play                       | default                                                      | play/resume                                                  |
|                                        | command     | Stop                       | default                                                      | stop                                                         |
| Speaker                                | command     | volumeAdd                  | default                                                      | volume up                                                    |
|                                        | command     | volumeSub                  | default                                                      | volume down                                                  |
| Fan                                    | command     | swing                      | default                                                      | swing                                                        |
|                                        | command     | timer                      | default                                                      | set timer                                                    |
|                                        | command     | lowSpeed                   | default                                                      | set fan speed to low                                         |
|                                        | command     | middleSpeed                | default                                                      | set fan speed to medium                                      |
|                                        | command     | highSpeed                  | default                                                      | set fan speed to high                                        |
| Light                                  | command     | brightnessUp               | default                                                      | brightness up                                                |
|                                        | command     | brightnessDown             | default                                                      | brightness down                                              |

>  Note: Most of the devices support `turnOn` or `turnOff`, which are case-sensitive. For infrared remote devices, when you have created customized buttons, you must set `commandType` to `customize`, otherwise the command will not work. `command` needs to be set to the name of the customized button.



#### Path parameters

| Name     | Type   | Required | Description |
| -------- | ------ | -------- | ----------- |
| deviceId | String | Yes      | device ID   |

#### Request body parameters

| Name        | Type   | Required | Description                                                 |
| ----------- | ------ | -------- | ----------------------------------------------------------- |
| command     | String | Yes      | the name of the command                                     |
| parameter   | String | No       | some commands require parameters, such as `SetChannel`      |
| commandType | String | No       | for customized buttons, this needs to be set to `customzie` |

#### Response

The response is basically a JSON object, which contains the following properties,

| Key Name   | Value Type   |
| ---------- | ------------ |
| statusCode | Integer      |
| message    | String       |
| body       | Object<body> |

#### Errors

| Error code/message          | Description                                                  |
| --------------------------- | ------------------------------------------------------------ |
| {"message": "Unauthorized"} | Http 401 Error. User permission is denied due to invalid token. |
| 151                         | device type error                                            |
| 152                         | device not found                                             |
| 160                         | command is not supported                                     |
| 161                         | device offline                                               |
| 171                         | hub device is offline                                        |
| 190                         | Device internal error due to device states not synchronized with server. Or command format is invalid. |

#### Sample

##### Bot example

Turn a Bot on

Request

```http
POST https://api.switch-bot.com/v1.1/devices/210/commands
```

```js
{
    "command": "turnOn",
    "parameter": "default",
    "commandType": "command"
}
```

Response

```js
{
    "statusCode": 100,
    "body": {},
    "message": "success"
}
```



Set the color value of a Color Bulb
Request

```http
POST https://api.switch-bot.com/v1.1/devices/84F70353A411/commands
```

```js
{
    "command": "setColor",
    "parameter": "122:80:20", // yellow
    "commandType": "command"
}
```

Response

```js
{
    "statusCode": 100,
    "body": {},
    "message": "success"
}
```


##### Infrared remote device example

Set an Air Conditioner

Request

```http
POST https://api.switch-bot.com/v1.1/devices/02-202007201626-70/commands
```

```js
{
    "command": "setAll",
    "parameter": "26,1,3,on",
    "commandType": "command"
}
```

Response

```js
{
    "statusCode": 100,
    "body": {},
    "message": "success"
}
```



Trigger a customized button

Request

```http
POST https://api.switch-bot.com/v1.1/devices/02-202007201626-10/commands
```

```js
{
    "command": "ボタン", // the name of the customized button
    "parameter": "default",
    "commandType": "customize"
}
```

Response

```js
{
    "statusCode": 100,
    "body": {},
    "message": "success"
}
```



## Scenes

The scenes API is used to access the smart scenes created by a user and to execute manual scenes.

### Get scene list

```http
GET /v1.1/scenes
```

#### Description

Get a list of manual scenes created by the current user.

#### Response

The response is basically a JSON object, which contains the following properties,

| Key Name   | Value Type   |
| ---------- | ------------ |
| statusCode | Integer      |
| message    | String       |
| body       | Object<body> |

The body object contains a list of objects, which has the following properties,

| Key       | Type   | Description    |
| --------- | ------ | -------------- |
| sceneId   | String | a scene's ID   |
| sceneName | String | a scene's name |

#### Errors

| Error code/message          | Description                                                  |
| --------------------------- | ------------------------------------------------------------ |
| {"message": "Unauthorized"} | Http 401 Error. User permission is denied due to invalid token. |
| 190                         | Device internal error due to device states not synchronized with server |

#### Sample

##### Get all scenes

Request

```http
GET https://api.switch-bot.com/v1.1/scenes
```

Response

```js
{
    "statusCode": 100,
    "body": [
        {
            "sceneId": "T02-20200804130110",
            "sceneName": "Close Office Devices"
        },
        {
            "sceneId": "T02-202009221414-48924101",
            "sceneName": "Set Office AC to 25"
        },
        {
            "sceneId": "T02-202011051830-39363561",
            "sceneName": "Set Bedroom to 24"
        },
        {
            "sceneId": "T02-202011051831-82928991",
            "sceneName": "Turn off home devices"
        },
        {
            "sceneId": "T02-202011062059-26364981",
            "sceneName": "Set Bedroom to 26 degree"
        }
    ],
    "message": "success"
}
```

### Execute manual scenes

```http
POST /v1.1/scenes/{sceneId}/execute
```

#### Description

Sends a request to execute a manual scene.

#### Path parameters

| Name    | Type   | Required | Description |
| ------- | ------ | -------- | ----------- |
| sceneId | String | Yes      | scene ID    |

The response is basically a JSON object, which contains the following properties,

| Key Name   | Value Type   |
| ---------- | ------------ |
| statusCode | Integer      |
| message    | String       |
| body       | Object<body> |

#### Errors

| Error code/message          | Description                                                  |
| --------------------------- | ------------------------------------------------------------ |
| {"message": "Unauthorized"} | Http 401 Error. User permission is denied due to invalid token. |
| 190                         | Device internal error due to device states not synchronized with server |

#### Sample

##### Execute a scene

Request

```http
POST https://api.switch-bot.com/v1.1/scenes/T02-202009221414-48924101/execute
```

Response

```js
{
    "statusCode": 100,
    "body": {},
    "message": "success"
}
```

## Webhook

### Configure webhook

#### Description
Configure the url that all the webhook events will be sent to

#### Request
```http
POST https://api.switch-bot.com/v1.1/webhook/setupWebhook
```

##### Request body parameters
| Key Name   | Value Type | Description                                           |
| ---------- | ---------- | ----------------------------------------------------- |
| action     | String     | the type of actions                                   |
| url        | String     | the url where all the events are sent to              |
| deviceList | String     | the list of device ids, currently only supports "ALL" |

Head

```js
{
    "Content-type":"application/json",
    "Authorization":your_token // enter your API token
}
```

Body

```js
{
    "action":"setupWebhook",
    "url":url1, // enter your url
    "deviceList":"ALL"
}
```

#### Response

Sample

```js
{
    "statusCode": 100,
    "body": {},
    "message": ""
}
```

### Get webhook configuration
#### Description
Get the current configuration info of the webhook

#### Request
```http
POST https://api.switch-bot.com/v1.1/webhook/queryWebhook
```

##### Request body parameters

| Key Name | Value Type | Description                                                  |
| -------- | ---------- | ------------------------------------------------------------ |
| action   | String     | the type of actions, currently supports "queryUrl", "queryDetails" |
| url      | String     | the url where all the events are sent to. you need to specify the url when using queryDetails |

##### queryUrl

Head

```js
{
    "Content-type":"application/json",
    "Authorization":your_token // enter your API token
}
```

Body

```js
{
    "action": "queryUrl"
}
```

##### queryDetails
Head

```js
{
    "Content-type":"application/json",
    "Authorization":your_token // enter your API token
}
```

Body

```js
{
    "action": "queryDetails",
    "urls":[url1] // get infos of a url
}
```


#### Response

##### queryUrl

```js
{
    "statusCode": 100,
    "body": {
        "urls": [url1] // the target url
    },
    "message": ""
}
```

##### queryDetails
```js
{
    "statusCode": 100,
    "body": [
        {
            "url":url1,
            "createTime":123456,
            "lastUpdateTime":123456,
            "deviceList": "ALL",
            "enable":true
        }
    ],
    "message": ""
}
```
### Update webhook configuration
#### Description
Update the configuration of the webhook

#### Request
```http
POST https://api.switch-bot.com/v1.1/webhook/queryWebhook
```

##### Request body parameters
| Key Name | Value Type | Description                                                  |
| -------- | ---------- | ------------------------------------------------------------ |
| action   | String     | the type of actions                                          |
| config   | Object     | the configuration details you want to update. you can change the current url or enable/disable the webhook. refer to the example below |

Head

```js
{
    "Content-type":"application/json",
    "Authorization":your_token // enter your API token
}
```

Body

```js
{
    "action": "updateWebhook",
    "config":{
        "url":url1,
        "enable":true
    }
}
```

#### Response
```js
{
    "statusCode": 100,
    "body": {},
    "message": ""
}
```

### Delete webhook
#### Description
Delete the configuration of the webhook

#### Request
```http
POST https://api.switch-bot.com/v1.1/webhook/deleteWebhook
```

##### Request body parameters
| Key Name | Value Type | Description                              |
| -------- | ---------- | ---------------------------------------- |
| action   | String     | the type of actions                      |
| url      | String     | the url where all the events are sent to |

Head

```js
{
    "Content-type":"application/json",
    "Authorization":your_token // enter your API token
}
```

Body

```js
{
    "action": "deleteWebhook",
    "url":url1
}
```

#### Response
```js
{
    "statusCode": 100,
    "body": {},
    "message": ""
}
```



### Receive events from webhook

When an event gets triggered, SwitchBot server will send a `POST` request to the url you have configured. Refer to the table below for a list of products that support webhook.

| Device Type  | **Product**     |
| ------------ | --------------- |
| WoPresence   | Motion Sensor   |
| WoContact    | Contact Sensor  |
| WoLock       | Lock            |
| WoCamera     | Indoor Cam      |
| WoPanTiltCam | Pan/Tilt Cam    |
| WoBulb       | Color Bulb      |
| WoStrip      | LED Strip Light |
| WoPlugUS     | Plug Mini (US)  |
| WoPlugJP     | Plug Mini (JP)  |
| WoMeter      | Meter           |
| WoMeterPlus  | Meter Plus      |

#### Motion Sensor

| Key Name       | Value Type | Description                                                  |
| -------------- | ---------- | ------------------------------------------------------------ |
| eventType      | String     | the type of events                                           |
| eventVersion   | String     | the current event version                                    |
| context        | Object     | the detail info of the event                                 |
| deviceType     | String     | the type of the device                                       |
| deviceMac      | String     | the MAC address of the device                                |
| detectionState | String     | the motion state of the device, "DETECTED" stands for motion is detected; "NOT_DETECTED" stands for motion has not been detected for some time |
| timeOfSample   | Long       | the time stamp when the event is sent                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoPresence",
        "deviceMac": DEVICE_MAC_ADDR,
        "detectionState": "NOT_DETECTED",
        "timeOfSample": 123456789
    }
}
```

#### Contact Sensor

| Key Name       | Value Type | Description                                                  |
| -------------- | ---------- | ------------------------------------------------------------ |
| eventType      | String     | the type of events                                           |
| eventVersion   | String     | the current event version                                    |
| context        | Object     | the detail info of the event                                 |
| deviceType     | String     | the type of the device                                       |
| deviceMac      | String     | the MAC address of the device                                |
| detectionState | String     | the motion state of the device, "DETECTED" stands for motion is detected; "NOT_DETECTED" stands for motion has not been detected for some time |
| doorMode       | String     | when the enter or exit mode gets triggered, "IN_DOOR" or "OUT_DOOR" is returned |
| brightness     | String     | the level of brightness, can be "bright" or "dim"            |
| openState      | String     | the state of the contact sensor, can be "open" or "close" or "timeOutNotClose" |
| timeOfSample   | Long       | the time stamp when the event is sent                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoContact",
        "deviceMac": DEVICE_MAC_ADDR,
        "detectionState": "NOT_DETECTED",
        "doorMode":"OUT_DOOR",
        "brightness": "dim",
        "openState": "open",
        "timeOfSample": 123456789
    }
}
```

#### Meter

| Key Name     | Value Type | Description                                |
| ------------ | ---------- | ------------------------------------------ |
| eventType    | String     | the type of events                         |
| eventVersion | String     | the current event version                  |
| context      | Object     | the detail info of the event               |
| deviceType   | String     | the type of the device                     |
| deviceMac    | String     | the MAC address of the device              |
| temperature  | Float      | the current temperature reading            |
| scale        | String     | the current temperature unit being used    |
| humidity     | Integer    | the current humidity reading in percentage |
| timeOfSample | Long       | the time stamp when the event is sent      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoMeter",
        "deviceMac": DEVICE_MAC_ADDR,
        "temperature": 22.5,
        "scale": "CELSIUS",
        "humidity": 31,
        "timeOfSample": 123456789
    }
}
```

#### Meter Plus

| Key Name     | Value Type | Description                                |
| ------------ | ---------- | ------------------------------------------ |
| eventType    | String     | the type of events                         |
| eventVersion | String     | the current event version                  |
| context      | Object     | the detail info of the event               |
| deviceType   | String     | the type of the device                     |
| deviceMac    | String     | the MAC address of the device              |
| temperature  | Float      | the current temperature reading            |
| scale        | String     | the current temperature unit being used    |
| humidity     | Integer    | the current humidity reading in percentage |
| timeOfSample | Long       | the time stamp when the event is sent      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoMeter",
        "deviceMac": DEVICE_MAC_ADDR,
        "temperature": 22.5,
        "scale": "CELSIUS",
        "humidity": 31,
        "timeOfSample": 123456789
    }
}
```

#### Lock

| Key Name     | Value Type | Description                                                  |
| ------------ | ---------- | ------------------------------------------------------------ |
| eventType    | String     | the type of events                                           |
| eventVersion | String     | the current event version                                    |
| context      | Object     | the detail info of the event                                 |
| deviceType   | String     | the type of the device                                       |
| deviceMac    | String     | the MAC address of the device                                |
| lockState    | String     | the state of the device, "LOCKED" stands for the motor is rotated to locking position; "UNLOCKED" stands for the motor is rotated to unlocking position; "JAMMED" stands for the motor is jammed while rotating |
| timeOfSample | Long       | the time stamp when the event is sent                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoLock",
        "deviceMac": DEVICE_MAC_ADDR,
        "lockState": "LOCKED",
        "timeOfSample": 123456789
    }
}
```

#### Indoor Cam

| Key Name       | Value Type | Description                                                  |
| -------------- | ---------- | ------------------------------------------------------------ |
| eventType      | String     | the type of events                                           |
| eventVersion   | String     | the current event version                                    |
| context        | Object     | the detail info of the event                                 |
| deviceType     | String     | the type of the device                                       |
| deviceMac      | String     | the MAC address of the device                                |
| detectionState | String     | the detection state of the device, "DETECTED" stands for motion is detected |
| timeOfSample   | Long       | the time stamp when the event is sent                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoCamera",
        "deviceMac": DEVICE_MAC_ADDR,
        "detectionState": "DETECTED",
        "timeOfSample": 123456789
    }
}
```

#### Pan/Tilt Cam

| Key Name       | Value Type | Description                                                  |
| -------------- | ---------- | ------------------------------------------------------------ |
| eventType      | String     | the type of events                                           |
| eventVersion   | String     | the current event version                                    |
| context        | Object     | the detail info of the event                                 |
| deviceType     | String     | the type of the device                                       |
| deviceMac      | String     | the MAC address of the device                                |
| detectionState | String     | the detection state of the device, "DETECTED" stands for motion is detected |
| timeOfSample   | Long       | the time stamp when the event is sent                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoPanTiltCam",
        "deviceMac": DEVICE_MAC_ADDR,
        "detectionState": "DETECTED",
        "timeOfSample": 123456789
    }
}
```

#### Color Bulb

| Key Name         | Value Type | Description                                                |
| ---------------- | ---------- | ---------------------------------------------------------- |
| eventType        | String     | the type of events                                         |
| eventVersion     | String     | the current event version                                  |
| context          | Object     | the detail info of the event                               |
| deviceType       | String     | the type of the device                                     |
| deviceMac        | String     | the MAC address of the device                              |
| powerState       | String     | the current power state of the device, "ON" or "OFF"       |
| brightness       | Integer    | the brightness value, range from 1 to 100                  |
| color            | String     | the color value, in the format of RGB value, "255:255:255" |
| colorTemperature | Integer    | the color temperature value, range from 2700 to 6500       |
| timeOfSample     | Long       | the time stamp when the event is sent                      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoBulb",
        "deviceMac": DEVICE_MAC_ADDR,
        "powerState": "ON",
        "brightness": 10,
        "color":"255:245:235",
        "colorTemperature":3500,
        "timeOfSample": 123456789
    }
}
```

#### LED Strip Light

| Key Name     | Value Type | Description                                                |
| ------------ | ---------- | ---------------------------------------------------------- |
| eventType    | String     | the type of events                                         |
| eventVersion | String     | the current event version                                  |
| context      | Object     | the detail info of the event                               |
| deviceType   | String     | the type of the device                                     |
| deviceMac    | String     | the MAC address of the device                              |
| powerState   | String     | the current power state of the device, "ON" or "OFF"       |
| brightness   | Integer    | the brightness value, range from 1 to 100                  |
| color        | String     | the color value, in the format of RGB value, "255:255:255" |
| timeOfSample | Long       | the time stamp when the event is sent                      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoStrip",
        "deviceMac": DEVICE_MAC_ADDR,
        "powerState": "ON",
        "brightness": 10,
        "color": "255:245:235",
        "timeOfSample": 123456789
    }
}
```

#### Plug Mini (US)

| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| eventType    | String     | the type of events                                   |
| eventVersion | String     | the current event version                            |
| context      | Object     | the detail info of the event                         |
| deviceType   | String     | the type of the device                               |
| deviceMac    | String     | the MAC address of the device                        |
| powerState   | String     | the current power state of the device, "ON" or "OFF" |
| timeOfSample | Long       | the time stamp when the event is sent                |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoPlugUS",
        "deviceMac": DEVICE_MAC_ADDR,
        "powerState": "ON",
        "timeOfSample": 123456789
    }
}
```

#### Plug Mini (JP)

| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| eventType    | String     | the type of events                                   |
| eventVersion | String     | the current event version                            |
| context      | Object     | the detail info of the event                         |
| deviceType   | String     | the type of the device                               |
| deviceMac    | String     | the MAC address of the device                        |
| powerState   | String     | the current power state of the device, "ON" or "OFF" |
| timeOfSample | Long       | the time stamp when the event is sent                |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoPlugJP",
        "deviceMac": DEVICE_MAC_ADDR,
        "powerState": "ON",
        "timeOfSample": 123456789
    }
}
```



----

* [SwitchBot (Official website)](https://www.switch-bot.com/)
* [Facebook @SwitchBotRobot](https://www.facebook.com/SwitchBotRobot/) 
* [Twitter @SwitchBot](https://twitter.com/switchbot) 
