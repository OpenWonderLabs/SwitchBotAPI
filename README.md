# SwitchBot API v1.1

- [Introduction](#introduction)
- [About the New Version](#about-the-new-version)
- [Getting Started](#getting-started)
- [Authentication](#authentication)
  * [Open Token and Secret Key](#open-token-and-secret-key)
  * [How to Sign?](#how-to-sign-)
- [Glossary](#glossary)
- [API Usage](#api-usage)
  * [Host Domain](#host-domain)
  * [Sending a Request](#sending-a-request)
    + [Content-Type](#content-type)
    + [Request limit](#request-limit)
  * [Request Header](#request-header)
  * [Standard HTTP Error Codes](#standard-http-error-codes)
- [Devices](#devices)
  * [Get device list](#get-device-list)
    + [Description](#description)
    + [Responses](#responses)
      - [Bot](#bot)
      - [Curtain](#curtain)
      - [Hub/Hub Plus/Hub Mini](#hub-hub-plus-hub-mini)
      - [Meter](#meter)
      - [Meter Plus](#meter-plus)
      - [Lock](#lock)
      - [Keypad](#keypad)
      - [Keypad Touch](#keypad-touch)
      - [Remote](#remote)
      - [Motion Sensor](#motion-sensor)
      - [Contact Sensor](#contact-sensor)
      - [Ceiling Light](#ceiling-light)
      - [Ceiling Light Pro](#ceiling-light-pro)
      - [Plug Mini (US)](#plug-mini--us-)
      - [Plug Mini (JP)](#plug-mini--jp-)
      - [Plug](#plug)
      - [Strip Light](#strip-light)
      - [Color Bulb](#color-bulb)
      - [Robot Vacuum Cleaner S1](#robot-vacuum-cleaner-s1)
      - [Robot Vacuum Cleaner S1 Plus](#robot-vacuum-cleaner-s1-plus)
      - [Humidifier](#humidifier)
      - [Indoor Cam](#indoor-cam)
      - [Pan/Tilt Cam](#pan-tilt-cam)
      - [Pan/Tilt Cam 2K](#pan-tilt-cam-2k)
      - [Virtual infrared remote devices](#virtual-infrared-remote-devices)
    + [Sample](#sample)
      - [Get all devices](#get-all-devices)
  * [Get device status](#get-device-status)
    + [Description](#description-1)
    + [Path parameters](#path-parameters)
    + [Responses](#responses-1)
      - [Bot](#bot-1)
      - [Curtain](#curtain-1)
      - [Meter](#meter-1)
      - [Meter Plus](#meter-plus-1)
      - [Lock](#lock-1)
      - [Keypad](#keypad-1)
      - [Keypad Touch](#keypad-touch-1)
      - [Motion Sensor](#motion-sensor-1)
      - [Contact Sensor](#contact-sensor-1)
      - [Ceiling Light](#ceiling-light-1)
      - [Ceiling Light Pro](#ceiling-light-pro-1)
      - [Plug Mini (US)](#plug-mini--us--1)
      - [Plug Mini (JP)](#plug-mini--jp--1)
      - [Plug](#plug-1)
      - [Strip Light](#strip-light-1)
      - [Color Bulb](#color-bulb-1)
      - [Robot Vacuum Cleaner S1](#robot-vacuum-cleaner-s1-1)
      - [Robot Vacuum Cleaner S1 Plus](#robot-vacuum-cleaner-s1-plus-1)
      - [Humidifier](#humidifier-1)
    + [Sample](#sample-1)
      - [SwitchBot Meter example](#switchbot-meter-example)
      - [SwitchBot Curtain example](#switchbot-curtain-example)
  * [Send device control commands](#send-device-control-commands)
    + [Description](#description-2)
    + [Command set for physical devices](#command-set-for-physical-devices)
      - [Bot](#bot-2)
      - [Curtain](#curtain-2)
      - [Lock](#lock-2)
      - [Humidifier](#humidifier-2)
      - [Plug](#plug-2)
      - [Plug Mini (US)](#plug-mini--us--2)
      - [Plug Mini (JP)](#plug-mini--jp--2)
      - [Color Bulb](#color-bulb-2)
      - [Strip Light](#strip-light-2)
      - [Robot Vacuum Cleaner S1](#robot-vacuum-cleaner-s1-2)
      - [Robot Vacuum Cleaner S1 Plus](#robot-vacuum-cleaner-s1-plus-2)
      - [Ceiling Light](#ceiling-light-2)
      - [Ceiling Light Pro](#ceiling-light-pro-2)
      - [Keypad](#keypad-2)
      - [Keypad Touch](#keypad-touch-2)
    + [Command set for virtual infrared remote devices](#command-set-for-virtual-infrared-remote-devices)
    + [Path parameters](#path-parameters-1)
    + [Request body parameters](#request-body-parameters)
    + [Response](#response)
    + [Errors](#errors)
    + [Sample](#sample-2)
      - [Keypad example](#keypad-example)
      - [Bot example](#bot-example)
      - [Infrared remote device example](#infrared-remote-device-example)
- [Scenes](#scenes)
  * [Get scene list](#get-scene-list)
    + [Description](#description-3)
    + [Response](#response-1)
    + [Errors](#errors-1)
    + [Sample](#sample-3)
      - [Get all scenes](#get-all-scenes)
  * [Execute manual scenes](#execute-manual-scenes)
    + [Description](#description-4)
    + [Path parameters](#path-parameters-2)
    + [Errors](#errors-2)
    + [Sample](#sample-4)
      - [Execute a scene](#execute-a-scene)
- [Webhook](#webhook)
  * [Configure webhook](#configure-webhook)
    + [Description](#description-5)
    + [Request](#request)
      - [Request body parameters](#request-body-parameters-1)
    + [Response](#response-2)
  * [Get webhook configuration](#get-webhook-configuration)
    + [Description](#description-6)
    + [Request](#request-1)
      - [Request body parameters](#request-body-parameters-2)
      - [queryUrl](#queryurl)
      - [queryDetails](#querydetails)
    + [Response](#response-3)
      - [queryUrl](#queryurl-1)
      - [queryDetails](#querydetails-1)
  * [Update webhook configuration](#update-webhook-configuration)
    + [Description](#description-7)
    + [Request](#request-2)
      - [Request body parameters](#request-body-parameters-3)
    + [Response](#response-4)
  * [Delete webhook](#delete-webhook)
    + [Description](#description-8)
    + [Request](#request-3)
      - [Request body parameters](#request-body-parameters-4)
    + [Response](#response-5)
  * [Receive events from webhook](#receive-events-from-webhook)
    + [Motion Sensor](#motion-sensor-2)
    + [Contact Sensor](#contact-sensor-2)
    + [Meter](#meter-2)
    + [Meter Plus](#meter-plus-2)
    + [Lock](#lock-3)
    + [Indoor Cam](#indoor-cam-1)
    + [Pan/Tilt Cam](#pan-tilt-cam-1)
    + [Color Bulb](#color-bulb-3)
    + [LED Strip Light](#led-strip-light)
    + [Plug Mini (US)](#plug-mini--us--3)
    + [Plug Mini (JP)](#plug-mini--jp--3)
    + [Robot Vacuum Cleaner S1](#robot-vacuum-cleaner-s1-3)
    + [Robot Vacuum Cleaner S1 Plus](#robot-vacuum-cleaner-s1-plus-3)
    + [Ceiling Light](#ceiling-light-3)
    + [Ceiling Light Pro](#ceiling-light-pro-3)
    + [Keypad](#keypad-3)
      - [Create a passcode](#create-a-passcode)
      - [Delete a passcode](#delete-a-passcode)
    + [Keypad Touch](#keypad-touch-3)
      - [Create a passcode](#create-a-passcode-1)
      - [Delete a passcode](#delete-a-passcode-1)

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



JavaScript example code

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

C# example code

```c#
using System;
using System.Diagnostics;
using System.Text;
using System.Security.Cryptography;
using System.Net.Http;

string token = "My Token";
string secret = "My Secret Key";
DateTime dt1970 = new DateTime(1970, 1, 1);
DateTime current = DateTime.Now;
TimeSpan span = current - dt1970;
long time = Convert.ToInt64(span.TotalMilliseconds);
string nonce = Guid.NewGuid().ToString();
string data = token + time.ToString() + nonce;
Encoding utf8 = Encoding.UTF8;
HMACSHA256 hmac = new HMACSHA256(utf8.GetBytes(secret));
string signature = Convert.ToBase64String(hmac.ComputeHash(utf8.GetBytes(data)));

//Create http client
HttpClient client = new HttpClient();
var request = new HttpRequestMessage(HttpMethod.Get, @"https://api.switch-bot.com/v1.1/devices");
request.Headers.TryAddWithoutValidation(@"Authorization", token);
request.Headers.TryAddWithoutValidation(@"sign", signature);
request.Headers.TryAddWithoutValidation(@"nonce", nonce);
request.Headers.TryAddWithoutValidation(@"t", time.ToString());

var response = await client.SendAsync(request);

Console.WriteLine(await response.Content.ReadAsStringAsync());
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
| Plug                         | Short for SwitchBot Plug Model No. SP11. Currently only available in Japan |
| Meter                        | Short for SwitchBot Thermometer and Hygrometer Model No. SwitchBot MeterTH S1 |
| Meter Plus (JP)              | Short for SwitchBot Thermometer and Hygrometer Plus (JP) Model No. W2201500 |
| Meter Plus (US)              | Short for SwitchBot Thermometer and Hygrometer Plus (US) Model No. W2301500 |
| Motion Sensor                | Short for SwitchBot Motion Sensor Model No. W1101500         |
| Contact Sensor               | Short for SwitchBot Contact Sensor Model No. W1201500        |
| Color Bulb                   | Short for SwitchBot Color Bulb Model No. W1401400            |
| Strip Light                  | Short for SwitchBot LED Strip Light Model No. W1701100       |
| Plug Mini (US)               | Short for SwitchBot Plug Mini (US) Model No. W1901400 and W1901401 |
| Plug Mini (JP)               | Short for SwitchBot Plug Mini (JP) Model No. W2001400 and W2001401 |
| Lock                         | Short for SwitchBot Lock Model No. W1601700                  |
| Keypad                         | Short for SwitchBot Lock Model No. W2500010                  |
| Keypad Touch                         | Short for SwitchBot Lock Model No. W2500020                  |
| Robot Vacuum Cleaner S1      | Short for SwitchBot Robot Vacuum Cleaner S1 Model No. W3011000. Currently only available in Japan. |
| Robot Vacuum Cleaner S1 Plus | Short for SwitchBot Robot Vacuum Cleaner S1 Plus Model No. W3011010. Currently only available in Japan. |
| Ceiling Light      | Short for SwitchBot Ceiling Light Model No. W2612230 and W2612240. Currently only available in Japan. |
| Ceiling Light Pro | Short for SwitchBot Ceiling Light Pro Model No. W2612210 and W2612220. Currently only available in Japan. |
| Indoor Cam | Short for SwitchBot Indoor Cam Model No. W1301200                  |
| Pan/Tilt Cam | Short for SwitchBot Pan/Tilt Cam Model No. W1801200                  |
| Pan/Tilt Cam 2K | Short for SwitchBot Pan/Tilt Cam 2K Model No. W3101100                  |

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
 -  `new` Keypad (MUST enable Cloud Service first)
 -  `new` Keypad Touch (MUST enable Cloud Service first)
 -  `new` Ceiling Light
 -  `new` Ceiling Light Pro

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

The `body` object contains the following properties,

| Key Name           | Value Type            | Description                               |
| ------------------ | --------------------- | ----------------------------------------- |
| deviceList         | Array<device>         | a list of physical devices                |
| infraredRemoteList | Array<infraredRemote> | a list of virtual infrared remote devices |

The response may contain the following codes and messages,

| Status Code | Body Content       | Message      | Description                                                  |
| ----------- | ------------------ | ------------ | ------------------------------------------------------------ |
| 100         | Device list object | success      | Returns an object that contains two device lists             |
| n/a         | n/a                | Unauthorized | Http 401 Error. User permission is denied due to invalid token. |
| 190         | n/a                | System error | Device internal error due to device states not synchronized with server |

The `deviceList` array contains a list of objects with the following key-value attributes,

##### Bot
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Bot*                                           |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                       |

##### Curtain
| Key                | Value Type      | Description                                                  |
| ------------------ | --------------- | ------------------------------------------------------------ |
| deviceId           | String          | device ID                                                    |
| deviceName         | String          | device name                                                  |
| deviceType         | String          | device type. *Curtain*                                       |
| enableCloudService | Boolean         | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String          | device's parent Hub ID                                       |
| curtainDevicesIds  | Array<deviceId> | a list of Curtain device IDs such that the Curtain devices are being paired or grouped |
| calibrate          | Boolean         | determines if the open position and the close position of a device have been properly calibrated or not |
| group              | Boolean         | determines if a Curtain is paired with or grouped with another Curtain or not |
| master             | Boolean         | determines if a Curtain is the master device or not when paired with or grouped with another Curtain |
| openDirection      | String          | the opening direction of a Curtain                           |

##### Hub/Hub Plus/Hub Mini
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Hub*, *Hub Plus*, or *Hub Mini*.               |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Meter
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Meter*                                         |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                       |

##### Meter Plus
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *MeterPlus*                                     |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                       |

##### Lock
| Key                | Value Type      | Description                                                  |
| ------------------ | --------------- | ------------------------------------------------------------ |
| deviceId           | String          | device ID                                                    |
| deviceName         | String          | device name                                                  |
| deviceType         | String          | device type. *Smart Lock*                                  |
| enableCloudService | Boolean         | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String          | device's parent Hub ID                                       |
| group              | Boolean         | determines if a Lock is grouped with another Lock or not |
| master             | Boolean         | determines if a Lock is the master device or not when grouped with another Lock in Dual Lock mode |
| groupName              | Boolean         | the name of the Lock group |
| lockDevicesIds              | Array<deviceId>         | a list of Lock device IDs such that the Lock devices are being grouped in Dual Lock mode |

##### Keypad
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Keypad*                                        |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                       |
| lockDeviceId       | String     | MAC address of the Lock that the current device is paired with |
| keyList            | Object     | a list of passcodes                                          |

`keyList` maintains a list of passcodes,

| Key        | Value Type | Description                                                  |
| ---------- | ---------- | ------------------------------------------------------------ |
| id         | Integer    | passcode ID                                                  |
| name       | String     | name of the passcode                                         |
| type       | String     | type of the passcode. *permanent*, a permanent passcode. *timeLimit*, a temporary passcode. *disposable*, a one-time passcode. *urgent*, an emergency passcode. |
| password   | String     | the passcode string encrypted with the developer secret key using the aes-128-cbc algorithm |
| iv         | String     | an arbitrary number used for the encryption                  |
| status     | String     | validity of the passcode. *normal*, the passcode is valid. *expired*, the passcode is invalid. |
| createTime | Long       | the time when the passcode is generated                      |

##### Keypad Touch
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Keypad Touch*                                  |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                       |
| lockDeviceId       | String     | MAC address of the Lock that the current device is paired with |
| keyList            | Object     | a list of passcodes                                          |

`keyList` maintains a list of passcodes,

| Key        | Value Type | Description                                                  |
| ---------- | ---------- | ------------------------------------------------------------ |
| id         | Integer    | passcode ID                                                  |
| name       | String     | name of the passcode                                         |
| type       | String     | type of the passcode. *permanent*, a permanent passcode. *timeLimit*, a temporary passcode. *disposable*, a one-time passcode. *urgent*, an emergency passcode. |
| password   | String     | the passcode string encrypted with the developer secret key using the aes-128-cbc algorithm |
| iv         | String     | an arbitrary number used for the encryption                  |
| status     | String     | validity of the passcode. *normal*, the passcode is valid. *expired*, the passcode is invalid. |
| createTime | Long       | the time when the passcode is generated                      |

##### Remote

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Remote*                                        |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                       |

##### Motion Sensor

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Motion Sensor*                                 |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                       |

##### Contact Sensor
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Contact Sensor*                                |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                       |

##### Ceiling Light
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Ceiling Light*                                 |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Ceiling Light Pro
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Ceiling Light Pro*                             |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Plug Mini (US)
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Plug Mini (US)*                                |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Plug Mini (JP)
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Plug Mini (JP)*                                |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Plug

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Plug*                                          |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Strip Light

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Strip Light*                                   |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Color Bulb

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Color Bulb*                                    |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Robot Vacuum Cleaner S1

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Robot Vacuum Cleaner S1*                       |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Robot Vacuum Cleaner S1 Plus

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Robot Vacuum Cleaner S1 Plus*                  |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Humidifier

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Humidifier*                                    |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Indoor Cam
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Indoor Cam*                                    |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Pan/Tilt Cam
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Pan/Tilt Cam*                                    |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Pan/Tilt Cam 2K
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Pan/Tilt Cam*                                    |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |


##### Virtual infrared remote devices


The `infraredRemoteList` array contains a list of objects with the following key-value attributes,

| Key         | Value Type | Description                   |
| ----------- | ---------- | ----------------------------- |
| deviceId    | String     | device ID                     |
| deviceName  | String     | device name                   |
| remoteType  | String     | device type                   |
| hubDeviceId | String     | remote device's parent Hub ID |

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
 -   `new` Keypad (MUST enable Cloud Service first)
 -  `new` Keypad Touch (MUST enable Cloud Service first)
 -  `new` Ceiling Light
 -  `new` Ceiling Light Pro

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

The reponses may contain the following codes and message,

| Status Code | Body Content       | Message      | Description                                                  |
| ----------- | ------------------ | ------------ | ------------------------------------------------------------ |
| 100         | Device list object | success      | Returns an object that contains two device lists             |
| n/a         | n/a                | Unauthorized | Http 401 Error. User permission is denied due to invalid token. |
| 190         | n/a                | System error | Device internal error due to device states not synchronized with server |

The `body` object contains the following properties,

##### Bot

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Bot*                                           |
| power              | String     | ON/OFF state                                                 |
| hubDeviceId        | String     | device's parent Hub ID                                       |

##### Curtain

| Key                | Value Type      | Description                                                  |
| ------------------ | --------------- | ------------------------------------------------------------ |
| deviceId           | String          | device ID                                                    |
| deviceType         | String          | device type. *Curtain*                                       |
| hubDeviceId        | String          | device's parent Hub ID                                       |
| calibrate          | Boolean         | determines if the open position and the close position of a device have been properly calibrated or not |
| group              | Boolean         | determines if a Curtain is paired with or grouped with another Curtain or not |
| moving             | Boolean         | determines if a Curtain is moving or not |
| slidePosition      | String          | the percentage of the distance between the calibrated open position and closed position that Curtain has traversed |

##### Meter
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Meter*                                         |
| hubDeviceId        | String     | device's parent Hub ID                                       |
| temperature            | Float      |  temperature in celsius                                       |
| humidity               | Integer    | humidity percentage |


##### Meter Plus
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Meter*                                         |
| hubDeviceId        | String     | device's parent Hub ID                                       |
| temperature            | Float      |  temperature in celsius                                       |
| humidity               | Integer    | humidity percentage |

##### Lock
| Key                | Value Type      | Description                                                  |
| ------------------ | --------------- | ------------------------------------------------------------ |
| deviceId           | String          | device ID                                                    |
| deviceType         | String          | device type. *Smart Lock*                                    |
| hubDeviceId        | String          | device's parent Hub ID                                       |
| lockState              | String     | determines if locked or not |
| doorState              | String     | determines if the door is closed or not  |
| calibrate          | Boolean         | determines if Lock has been calibrated or not |

##### Keypad

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Keypad*                                        |
| hubDeviceId        | String     | device's parent Hub ID                                       |

##### Keypad Touch

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Keypad Touch*                                  |
| hubDeviceId        | String     | device's parent Hub ID                                       |

##### Motion Sensor

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Motion Sensor*                                 |
| hubDeviceId        | String     | device's parent Hub ID                                       |
| moveDetected           | Boolean    | determines if motion is detected |
| brightness             | String     | the ambient brightness picked up by the sensor. *bright*  or *dim* |

##### Contact Sensor

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Contact Sensor*                                |
| hubDeviceId        | String     | device's parent Hub ID                                       |
| moveDetected           | Boolean    | determines if motion is detected |
| openState  | String | the open state of the sensor. *open*, *close*, or *timeOutNotClose* |
| brightness             | String     | the ambient brightness picked up by the sensor. *bright*  or *dim* |

##### Ceiling Light

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Ceiling Light*                                 |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| power | String | ON/OFF state |
| brightness | Integer | the brightness value, range from 1 to 100 |
| colorTemperature | Integer | the color temperature value, range from 2700 to 6500 |

##### Ceiling Light Pro

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Ceiling Light Pro*                             |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| power | String | ON/OFF state |
| brightness | Integer | the brightness value, range from 1 to 100 |
| colorTemperature | Integer | the color temperature value, range from 2700 to 6500 |

##### Plug Mini (US) 

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Plug Mini (US)*                                |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| voltage                | Float      | the voltage of the device, measured in Volt |
| weight                 | Float      | the power consumed in a day, measured in Watts |
| electricityOfDay       | Integer    | the duration that the device has been used during a day, measured in minutes  |
| electricCurrent        | Float      | the current of the device at the moment, measured in Amp |


##### Plug Mini (JP)

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Plug Mini (JP)*                                |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| voltage                | Float      | the voltage of the device, measured in Volt |
| weight                 | Float      | the power consumed in a day, measured in Watts |
| electricityOfDay       | Integer    | the duration that the device has been used during a day, measured in minutes  |
| electricCurrent        | Float      | the current of the device at the moment, measured in Amp |

##### Plug
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Plug*                        |
| power | String | ON/OFF state |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Strip Light

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Strip Light*                                   |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| power                  | String     | ON/OFF state                                                 |
| brightness             | Integer    | the brightness value, range from 1 to 100                    |
| color                  | String     |  the color value, RGB "255:255:255"                           |

##### Color Bulb

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Color Bulb*                                    |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| power                  | String     | ON/OFF state                                                 |
| brightness             | Integer    | the brightness value, range from 1 to 100                    |
| color                  | String     |  the color value, RGB "255:255:255"                           |
| colorTemperature | Integer | the color temperature value, range from 2700 to 6500 |

##### Robot Vacuum Cleaner S1

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Robot Vacuum Cleaner S1*                       |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| workingStatus    | String     | the working status of the device. *StandBy*, *Clearing*, *Paused*, *GotoChargeBase*, *Charging*, *ChargeDone*, *Dormant*, *InTrouble*, *InRemoteControl*, or *InDustCollecting* |
| onlineStatus    | String     | the connection status of the device. *online* or *offline* |
| battery                | Integer    |  the current battery level                                            |

##### Robot Vacuum Cleaner S1 Plus

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Robot Vacuum Cleaner S1 Plus*                  |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| workingStatus    | String     | the working status of the device. *StandBy*, *Clearing*, *Paused*, *GotoChargeBase*, *Charging*, *ChargeDone*, *Dormant*, *InTrouble*, *InRemoteControl*, or *InDustCollecting* |
| onlineStatus    | String     | the connection status of the device. *online* or *offline* |
| battery                | Integer    |  the current battery level                                            |

##### Humidifier

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Humidifier*                                    |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| power                  | String     | ON/OFF state                                                 |
| humidity               | Integer    | humidity percentage                                          |
| temperature            | Float      | temperature in celsius                                       |
| nebulizationEfficiency | Integer    | atomization efficiency percentage |
| auto                   | Boolean    | determines if a Humidifier is in Auto Mode or not            |
| childLock              | Boolean    | determines if a Humidifier's safety lock is on or not        |
| sound                  | Boolean    | determines if a Humidifier is muted or not                   |
| lackWater | Boolean | determines if the water tank is empty or not |

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

##### Bot
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Bot                          | command     | turnOff             | default                                                      | set to OFF state                                             |
| Bot                          | command     | turnOn              | default                                                      | set to ON state                                              |
| Bot                          | command     | press               | default                                                      | trigger press                                                |

##### Curtain
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Curtain                      | command     | setPosition         | index0,mode0,position0<br />e.g. `0,ff,80`                   | mode: 0 (Performance Mode), 1 (Silent Mode), ff (default mode) <br />position: 0~100 (0 means opened, 100 means closed) |
| Curtain                      | command     | turnOff             | default                                                      | equivalent to set position to 100                            |
| Curtain                      | command     | turnOn              | default                                                      | equivalent to set position to 0                              |

##### Lock
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Lock                         | command     | lock                | default                                                      | rotate to locked position                                    |
| Lock                         | command     | unlock              | default                                                      | rotate to unlocked position                                  |

##### Humidifier
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Humidifier                   | command     | turnOff             | default                                                      | set to OFF state                                             |
| Humidifier                   | command     | turnOn              | default                                                      | set to ON state                                              |
| Humidifier                   | command     | setMode             | `auto` or `101` or<br />  `102` or `103` or `{0~100}`        | auto, set to Auto Mode,<br />101, set atomization efficiency to 34%,<br />102, set atomization efficiency to 67%,<br />103, set atomization efficiency to 100% |

##### Plug
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Plug                         | command     | turnOn              | default                                                      | set to ON state                                              |
| Plug                         | command     | turnOff             | default                                                      | set to OFF state                                             |

##### Plug Mini (US)
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Plug Mini (US)           | command     | turnOn              | default                                                      | set to ON state                                              |
| Plug Mini (US)            | command     | turnOff             | default                                                      | set to OFF state                                             |
| Plug Mini (US)            | command     | toggle              | default                                                      | toggle state                                                 |

##### Plug Mini (JP)
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Plug Mini (JP)        | command     | turnOn              | default                                                      | set to ON state                                              |
| Plug Mini (JP)            | command     | turnOff             | default                                                      | set to OFF state                                             |
| Plug Mini (JP)            | command     | toggle              | default                                                      | toggle state                                                 |

##### Color Bulb
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Color Bulb                   | command     | turnOn              | default                                                      | set to ON state                                              |
| Color Bulb                   | command     | turnOff             | default                                                      | set to OFF state                                             |
| Color Bulb                   | command     | toggle              | default                                                      | toggle state                                                 |
| Color Bulb                   | command     | setBrightness       | `{1-100}`                                                    | set brightness                                               |
| Color Bulb                   | command     | setColor            | `"{0-255}:{0-255}:{0-255}"`                                  | set RGB color value                                          |
| Color Bulb                   | command     | setColorTemperature | `{2700-6500}`                                                | set color temperature                                        |

##### Strip Light
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Strip Light                  | command     | turnOn              | default                                                      | set to ON state                                              |
| Strip Light                  | command     | turnOff             | default                                                      | set to OFF state                                             |
| Strip Light                  | command     | toggle              | default                                                      | toggle state                                                 |
| Strip Light                  | command     | setBrightness       | `{1-100}`                                                    | set brightness                                               |
| Strip Light                  | command     | setColor            | `"{0-255}:{0-255}:{0-255}"`                                  | set RGB color value                                          |

##### Robot Vacuum Cleaner S1
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Robot Vacuum Cleaner S1      | command     | start               | default                                                      | start vacuuming                                              |
| Robot Vacuum Cleaner S1      | command     | stop                | default                                                      | stop vacuuming                                               |
| Robot Vacuum Cleaner S1      | command     | dock                | default                                                      | return to charging dock                                      |
| Robot Vacuum Cleaner S1      | command     | PowLevel            | `{0-3}`                                                      | set suction power level: 0 (Quiet), 1 (Standard), 2 (Strong), 3 (MAX) |

##### Robot Vacuum Cleaner S1 Plus
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Robot Vacuum Cleaner S1 Plus | command     | start               | default                                                      | start vacuuming                                              |
| Robot Vacuum Cleaner S1 Plus | command     | stop                | default                                                      | stop vacuuming                                               |
| Robot Vacuum Cleaner S1 Plus | command     | dock                | default                                                      | return to charging dock                                      |
| Robot Vacuum Cleaner S1 Plus | command     | PowLevel            | `{0-3}`                                                      | set suction power level: 0 (Quiet), 1 (Standard), 2 (Strong), 3 (MAX) |

##### Ceiling Light
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Ceiling Light | command     | turnOn              | default                                                      | set to ON state                                              |
| Ceiling Light | command     | turnOff             | default                                                      | set to OFF state                                             |
| Ceiling Light | command     | toggle              | default                                                      | toggle state                                                 |
| Ceiling Light | command     | setBrightness       | `{1-100}`                                                    | set brightness                                               |
| Ceiling Light | command     | setColorTemperature | `{2700-6500}`                                  | set the color temperature |

##### Ceiling Light Pro
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Ceiling Light Pro | command     | turnOn              | default                                                      | set to ON state                                              |
| Ceiling Light Pro | command     | turnOff             | default                                                      | set to OFF state                                             |
| Ceiling Light Pro | command     | toggle              | default                                                      | toggle state                                                 |
| Ceiling Light Pro | command     | setBrightness       | `{1-100}`                                                    | set brightness                                               |
| Ceiling Light Pro | command     | setColorTemperature | `{2700-6500}`                                  | set the color temperature |

##### Keypad

The control commands for this product work differently than the other products. Due to security concerns, the passcodes are stored locally. This mechanism dramatically prolongs the time needed to successfully create a passcode and get the correct result through the Web API. Hence, the actual results of the following commands are returned from the SwitchBot server asynchronously and are delivered through a webhook. 

You need to configure a webhook to receive the correct result. Refer to this product's webhook definition.

| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Keypad | command     | createKey | { "name": passcode _name_str, "type": passcode_type_str, "password": passcode_str, "startTime": valid_from_long, "endTime": valid_to_long } | create a new passcode |
| Keypad | command     | deleteKey | { "id": passcode_id_int }  | delete an existing passcode |

The following table describes the parameter object for `createKey`,
| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| name | String | a unique name for the passcode. duplicates under the same device are not allowed. |
| type |String | type of the passcode. *permanent*, a permanent passcode. *timeLimit*, a temporary passcode. *disposable*, a one-time passcode. *urgent*, an emergency passcode. |
| password | String | a 6 to 12-digit passcode in plain text                       |
| startTime | Long |set the time the passcode becomes valid from, mandatory for one-time passcode and temporary passcode. a 10-digit timestamp.|
| endTime | Long |set the time the passcode becomes expired, mandatory for one-time passcode and temporary passcode. a 10-digit timestamp.|

The following table describes the parameter object for `deleteKey`,
| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| id | String | the id of the passcode |

##### Keypad Touch

The control commands for this product work differently than the other products. Due to security concerns, the passcodes are stored locally. This mechanism dramatically prolongs the time needed to successfully create a passcode and get the correct result through the Web API. Hence, the actual results of the following commands are returned from the SwitchBot server asynchronously and are delivered through a webhook. 

You need to configure a webhook to receive the correct result. Refer to this product's webhook definition.

| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Keypad Touch | command     | createKey | { "name": passcode _name_str, "type": passcode_type_str, "password": passcode_str, "startTime": valid_from_long, "endTime": valid_to_long } | create a new passcode |
| Keypad Touch | command     | deleteKey | { "id": passcode_id_int }  | delete an existing passcode |

The following table describes the parameter object for `createKey`,
| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| name | String | a unique name for the passcode. duplicates under the same device are not allowed. |
| type |String | type of the passcode. *permanent*, a permanent passcode. *timeLimit*, a temporary passcode. *disposable*, a one-time passcode. *urgent*, an emergency passcode. |
| password | String | a 6 to 12-digit passcode in plain text                       |
| startTime | Long |set the time the passcode becomes valid from, mandatory for one-time passcode and temporary passcode. a 10-digit timestamp.|
| endTime | Long |set the time the passcode becomes expired, mandatory for one-time passcode and temporary passcode. a 10-digit timestamp.|

The following table describes the parameter object for `deleteKey`,
| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| id | String | the id of the passcode |


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

##### Keypad example

Create a temporary passcode

Request

```http
POST https://api.switch-bot.com/v1.1/devices/F7538E1ABCEB/commands
```

```js
{
    "commandType": "command",
    "command": "createKey",
    "parameter": {
        "name": "Guest Code",
        "type": "timeLimit",
        "password": "12345678",
        "startTime": 1664640056,
        "endTime": 1665331432
    }
}
```

Response

```js
{
    "statusCode": 100,
    "body": {
        "commandId": "CMD166444044923602"
    },
    "message": "success"
}
```




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

| Device Type   | **Product**     |
| ------------- | --------------- |
| WoPresence    | Motion Sensor   |
| WoContact     | Contact Sensor  |
| WoLock        | Lock            |
| WoCamera      | Indoor Cam      |
| WoPanTiltCam  | Pan/Tilt Cam    |
| WoBulb        | Color Bulb      |
| WoStrip       | LED Strip Light |
| WoPlugUS      | Plug Mini (US)  |
| WoPlugJP      | Plug Mini (JP)  |
| WoMeter       | Meter           |
| WoMeterPlus   | Meter Plus      |
| WoSweeper | Robot Vacuum Cleaner S1 |
| WoSweeperPlus | Robot Vacuum Cleaner S1 Plus |
| WoCeiling | Ceiling Light |
| WoCeilingPro | Ceiling Light Pro |
| WoKeypad      | Keypad |
| WoKeypadTouch | Keypad Touch |

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

#### Robot Vacuum Cleaner S1
| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| eventType    | String     | the type of events                                   |
| eventVersion | String     | the current event version                            |
| context      | Object     | the detail info of the event                         |
| deviceType   | String     | attributes of the context object. the type of the device |
| deviceMac    | String     | attributes of the context object. the MAC address of the device |
| workingStatus    | String     | attributes of the context object. the working status of the device. *StandBy*, *Clearing*, *Paused*, *GotoChargeBase*, *Charging*, *ChargeDone*, *Dormant*, *InTrouble*, *InRemoteControl*, or *InDustCollecting* |
| onlineStatus    | String     | attributes of the context object. the connection status of the device. *online* or *offline* |
| battery | Integer | attributes of the context object. the battery level, range from 0 to 100 |
| timeOfSample    | Long | attributes of the context object. the time stamp when the event is sent |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoSweeper",
        "deviceMac": DEVICE_MAC_ADDR,
        "workingStatus"："StandBy",
        "onlineStatus": "online",
        "battery": 100,
        "timeOfSample": 123456789
    }
}
```

#### Robot Vacuum Cleaner S1 Plus
| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| eventType    | String     | the type of events                                   |
| eventVersion | String     | the current event version                            |
| context      | Object     | the detail info of the event                         |
| deviceType   | String     | attributes of the context object. the type of the device |
| deviceMac    | String     | attributes of the context object. the MAC address of the device |
| workingStatus    | String     | attributes of the context object. the working status of the device. *StandBy*, *Clearing*, *Paused*, *GotoChargeBase*, *Charging*, *ChargeDone*, *Dormant*, *InTrouble*, *InRemoteControl*, or *InDustCollecting* |
| onlineStatus    | String     | attributes of the context object. the connection status of the device. *online* or *offline* |
| battery | Integer | attributes of the context object. the battery level, range from 0 to 100 |
| timeOfSample    | Long | attributes of the context object. the time stamp when the event is sent |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoSweeperPlus",
        "deviceMac": DEVICE_MAC_ADDR,
        "workingStatus"："StandBy",
        "onlineStatus": "online",
        "battery": 100,
        "timeOfSample": 123456789
    }
}
```

#### Ceiling Light
| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| eventType    | String     | the type of events                                   |
| eventVersion | String     | the current event version                            |
| context      | Object     | the detail info of the event                         |
| deviceType   | String     | attributes of the context object. the type of the device |
| deviceMac    | String     | attributes of the context object. the MAC address of the device |
| powerState | String | attributes of the context object. ON/OFF state |
| brightness | Integer | attributes of the context object. the brightness value, range from 1 to 100 |
| colorTemperature | Integer | attributes of the context object. the color temperature value, range from 2700 to 6500 |
| timeOfSample    | Long | attributes of the context object. the time stamp when the event is sent |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoCeiling",
        "deviceMac": DEVICE_MAC_ADDR,
        "powerState": "ON",
        "brightness": 10,
        "colorTemperature": 3500,
        "timeOfSample": 123456789
    }
}
```

#### Ceiling Light Pro
| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| eventType    | String     | the type of events                                   |
| eventVersion | String     | the current event version                            |
| context      | Object     | the detail info of the event                         |
| deviceType   | String     | attributes of the context object. the type of the device |
| deviceMac    | String     | attributes of the context object. the MAC address of the device |
| powerState | String | attributes of the context object. ON/OFF state |
| brightness | Integer | attributes of the context object. the brightness value, range from 1 to 100 |
| colorTemperature | Integer | attributes of the context object. the color temperature value, range from 2700 to 6500 |
| timeOfSample    | Long | attributes of the context object. the time stamp when the event is sent |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoCeilingPro",
        "deviceMac": DEVICE_MAC_ADDR,
        "powerState": "ON",
        "brightness": 10,
        "colorTemperature": 3500,
        "timeOfSample": 123456789
    }
}
```

#### Keypad
| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| eventType    | String     | the type of events                                   |
| eventVersion | String     | the current event version                            |
| context      | Object     | the detail info of the event                         |
| deviceType   | String     | attributes of the context object. the type of the device |
| deviceMac    | String     | attributes of the context object. the MAC address of the device |
| eventName    | String     | attributes of the context object. the name of the command being sent |
| commandId    | String     | attributes of the context object. the command id |
| result    | String     | attributes of the context object. the result of the command. *success*, *failed*, or *timeout*. timeout duration is 1 minute |
| timeOfSample    | Long     | attributes of the context object. the time stamp when the event is sent |


##### Create a passcode
```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoKeypad",
        "deviceMac": DEVICE_MAC_ADDR,
        "eventName": "createKey",
        "commandId": "CMD-1663558451952-01",
        "result": "success",
        "timeOfSample": 123456789
    }
}
```

##### Delete a passcode
```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoKeypad",
        "deviceMac": DEVICE_MAC_ADDR,
        "eventName": "deleteKey ",
        "commandId": "CMD-1663558451952-01",
        "result": "success",
        "timeOfSample": 123456789
    }
}
```

#### Keypad Touch
| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| eventType    | String     | the type of events                                   |
| eventVersion | String     | the current event version                            |
| context      | Object     | the detail info of the event                         |
| deviceType   | String     | attributes of the context object. the type of the device |
| deviceMac    | String     | attributes of the context object. the MAC address of the device |
| eventName    | String     | attributes of the context object. the name of the command being sent |
| commandId    | String     | attributes of the context object. the command id |
| result    | String     | attributes of the context object. the result of the command. *success*, *failed*, or *timeout*. timeout duration is 1 minute |
| timeOfSample    | Long     | attributes of the context object. the time stamp when the event is sent |

##### Create a passcode
```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoKeypadTouch",
        "deviceMac": DEVICE_MAC_ADDR,
        "eventName": "createKey",
        "commandId": "CMD-1663558451952-01",
        "result": "success",
        "timeOfSample": 123456789
    }
}
```

##### Delete a passcode
```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoKeypadTouch",
        "deviceMac": DEVICE_MAC_ADDR,
        "eventName": "deleteKey ",
        "commandId": "CMD-1663558451952-01",
        "result": "success",
        "timeOfSample": 123456789
    }
}
```

----

* [SwitchBot (Official website)](https://www.switch-bot.com/)
* [Facebook @SwitchBotRobot](https://www.facebook.com/SwitchBotRobot/) 
* [Twitter @SwitchBot](https://twitter.com/switchbot) 
