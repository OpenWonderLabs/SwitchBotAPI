# SwitchBotAPI

- [SwitchBotAPI](#switchbotapi)
  - [Introduction](#introduction)
  - [Getting Started](#getting-started)
  - [Authentication](#authentication)
    - [Open Token](#open-token)
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
      - [Description](#description-1)
      - [Path parameters](#path-parameters)
      - [Responses](#responses-1)
      - [Sample](#sample-1)
        - [SwitchBot Meter example](#switchbot-meter-example)
        - [SwitchBot Curtain example](#switchbot-curtain-example)
    - [Send device control commands](#send-device-control-commands)
      - [Description](#description-2)
      - [Command set for physical devices](#command-set-for-physical-devices)
      - [Command set for virtual infrared remote devices](#command-set-for-virtual-infrared-remote-devices)
      - [Path parameters](#path-parameters-1)
      - [Request body parameters](#request-body-parameters)
      - [Response](#response)
      - [Errors](#errors)
      - [Sample](#sample-2)
        - [Bot example](#bot-example)
        - [Infrared remote device example](#infrared-remote-device-example)
  - [Scenes](#scenes)
    - [Get scene list](#get-scene-list)
      - [Description](#description-3)
      - [Response](#response-1)
      - [Errors](#errors-1)
      - [Sample](#sample-3)
        - [Get all scenes](#get-all-scenes)
    - [Execute manual scenes](#execute-manual-scenes)
      - [Description](#description-4)
      - [Path parameters](#path-parameters-2)
      - [Errors](#errors-2)
      - [Sample](#sample-4)
        - [Execute a scene](#execute-a-scene)

## Introduction
This document describes a collection of SwitchBot API methods, examples, and best practices for, but not limited to, IoT hobbyists, developers, and gurus to make their own smart home programs or applications. 

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
### Open Token
The token returned from the SwitchBot Cloud is an encrypted open token that grants the user developer-level permissions. The user will be able to add, delete, edit, and look up his or her user data including profile data and data associated with the devices that have been added to the user's account.



## Glossary

The following table provides definitions to the terms to be frequently mentioned in the subsequent sections.

| Term          | Description                                                  |
| ------------- | ------------------------------------------------------------ |
| Hub           | Generally referred to these devices, SwitchBot Hub Model No. SwitchBot Hub S1/SwitchBot Hub Mini Model No. W0202200/SwitchBot Hub Plus Model No. SwitchBot Hub S1 |
| Hub Mini      | Short for SwitchBot Hub Mini Model No. W0202200              |
| Hub Plus      | Short for SwitchBot Hub Plus Model No. SwitchBot Hub S1      |
| Bot           | Short for SwitchBot Bot Model No. SwitchBot S1               |
| Curtain       | Short for SwitchBot Curtain Model No. W0701600               |
| Plug          | Short for SwitchBot Plug Model No. SP11                      |
| Meter         | Short for SwitchBot Thermometer and Hygrometer Model No. SwitchBot MeterTH S1 |
| Motion Sensor | Short for SwitchBot Motion Sensor Model No. W1101500 |
| Contact Sensor | Short for SwitchBot Contact Sensor Model No. W1201500 |
| Color Bulb | Short for SwitchBot Color Bulb Model No. W1401400 |
| Smart Fan     | Short for SwitchBot Smart Fan Model No. W0601100             |
| Cloud Service | An SwitchBot app feature that 1. enables SwitchBot products to be discovered and communicated with third-party services voice control services, 2. allows users to create customized smart scenes and Android widgets. For BLE-based devices such as Bot and Curtain, you MUST first add a Hub/Hub Mini/Hub Plus and then enable Cloud Service on the Settings page in order to make use of the web API! |



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
The amount of API calls per day is limited to 1000 times. Going over that limit will return "Unauthorized."

### Request Header

The following parameters need to be included into the header,

| Parameter | Type | Location | Required | Description     |
| ------------- | -------- | ------------ | ------------ | ------------------- |
| Authorization | String   | header       | Yes          | Open Token acquired |

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
GET /v1.0/devices
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
 - `new` Motion Sensor (MUST enable Cloud Service first)
 - `new` Contact Sensor (MUST enable Cloud Service first)
 - `new` Color Bulb
 -  Humidifier
 -  Smart Fan

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
| calibrate          | Boolean         | only available for Curtain devices. determines if the open position and the close position of a Curtain have been properly calibrated or not |
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

| Status Code | Body Content       | Message      | Description |
| ----------- | ------------ | ----------- | ----------- |
| 100         | Device list object | success      | Returns an object that contains two device lists |
| n/a       | n/a | Unauthorized | Http 401 Error. User permission is denied due to invalid token. |
| 190         | n/a | System error | Device internal error due to device states not synchronized with server |

#### Sample

##### Get all devices

Request

```http
GET https://api.switch-bot.com/v1.0/devices
```

Response

```js
{
    "statusCode": 100,
    "body": {
        "deviceList": [
            {
                "deviceId": "500291B269BE",
                "deviceName": "Living Room Humidifier",
                "deviceType": "Humidifier",
                "enableCloudService": true,
                "hubDeviceId": "000000000000"
            }
        ],
        "infraredRemoteList": [
            {
                "deviceId": "02-202008110034-13",
                "deviceName": "Living Room TV",
                "remoteType": "TV",
                "hubDeviceId": "FA7310762361"
            }
        ]
    },
    "message": "success"
}
```




### Get device status
```http
GET /v1.0/devices/{deviceId}/status
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
| Key                    | Value Type | Description                                                  |
| ---------------------- | ---------- | ------------------------------------------------------------ |
| deviceId               | String     | device ID                                                    |
| deviceType             | String     | device type                                                  |
| hubDeviceId            | String     | device's parent Hub ID                                       |
| power                  | String     | only available for Bot/Plug/Humidifier/Color Bulb devices. ON/OFF state |
| humidity               | Integer    | only available for Meter/Humidifier devices. humidity percentage |
| temperature            | Float      | only available for Meter/Humidifier devices. temperature in celsius |
| nebulizationEfficiency | Integer    | only available for Humidifier devices. atomization efficiency % |
| auto                   | Boolean    | only available for Humidifier devices. determines if a Humidifier is in Auto Mode or not |
| childLock              | Boolean    | only available for Humidifier devices. determines if a Humidifier's safety lock is on or not |
| sound                  | Boolean    | only available for Humidifier devices. determines if a Humidifier is muted or not |
| calibrate              | Boolean    | only available for Curtain devices. determines if a Curtain has been calibrated or not |
| group                  | Boolean    | only available for Curtain devices. determines if a Curtain is paired with or grouped with another Curtain or not |
| moving                 | Boolean    | only available for Curtain devices. determines if a Curtain is moving or not |
| slidePosition          | Integer    | only available for Curtain devices. the percentage of the distance between the calibrated open position and close position that a Curtain has moved to |
| mode                   | Integer    | only available for Smart Fan devices. the fan mode           |
| speed                  | Integer    | only available for Smart Fan devices. the fan speed          |
| shaking                | Boolean    | only available for Smart Fan devices. determines if the fan is swinging or not |
| shakeCenter            | Integer    | only available for Smart Fan devices. the fan's swing direciton |
| shakeRange             | Integer    | only available for Smart Fan devices. the fan's swing range, 0~120° |
| moveDetected  | Boolean | only available for Motion Sensor, Contact Sensor devices. determines if motion is detected |
| brightness  | String | only available for Motion Sensor, Contact Sensor devices. tell the ambient environment is bright or dim |
| openState | String | only available for Contact Sensor devices. open/close/timeOutNotClose |
| brightness | Integer | only available for Color Bulb devices. the brightness value, range from 1 to 100 |
| color | String | only available for Color Bulb devices. the color value, RGB "255:255:255" |
| colorTemperature | Integer | only available for Color Bulb devices. the color temperature value, range from 2700 to 6500 |
| lackWater | Boolean | only available for Humidifier devices. determines if the water tank empty or not |

The reponses may contain the following codes and message,

| Status Code | Body Content       | Message      | Description |
| ----------- | ------------------ | ------------ | ----------- |
| 100         | Device list object | success      | Returns an object that contains two device lists |
| n/a       | n/a | Unauthorized | Http 401 Error. User permission is denied due to invalid token. |
| 190         | n/a | System error | Device internal error due to device states not synchronized with server |

#### Sample

##### SwitchBot Meter example

Request the status of a SwitchBot Thermometer and Hygrometer

Request

```http
GET https://api.switch-bot.com/v1.0/devices/C271111EC0AB/status
```

Response


```js
{
    "statusCode": 100,
    "body": {
        "deviceId": "C271111EC0AB",
        "deviceType": "Meter",
        "hubDeviceId": "FA7310762361",
        "humidity": 52,
        "temperature": 26.1
    },
    "message": "success"
}
```

##### SwitchBot Curtain example

Request the status of a SwitchBot Curtain

Request

```http
GET https://api.switch-bot.com/v1.0/devices/E2F6032048AB/status
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
POST /v1.0/devices/{deviceId}/commands
```

#### Description

Send control commands to physical devices and virtual infrared remote devices.

#### Command set for physical devices

The table below describes all the available commands for physical devices,

| deviceType     | commandType     | Command     |  command parameter    |  Description    |
| ---- | ---- | ---- | ---- | ---- |
|  Bot    |  command    | turnOff     | default     | set to OFF state |
| Bot | command | turnOn | default | set to ON state |
| Bot | command | press | default | trigger press |
| Plug     | command | turnOn | default | set to ON state |
| Plug | command | turnOff | default | set to OFF state |
| Curtain     | command |  setPosition    | index0,mode0,position0<br />e.g. `0,ff,80` |  mode: 0 (Performance Mode), 1 (Silent Mode), ff (default mode) <br />position: 0~100 (0 means opened, 100 means closed)  |
| Curtain | command |  turnOff    | default | equivalent to set position to 100 |
| Curtain | command |  turnOn    | default | equivalent to set position to 0 |
| Humidifier | command | turnOff | default | set to OFF state                                             |
| Humidifier | command | turnOn | default | set to ON state                                              |
| Humidifier | command |setMode  | `auto` or `101` or<br />  `102` or `103` or `{0~100}` | auto, set to Auto Mode,<br />101, set atomization efficiency to 34%,<br />102, set atomization efficiency to 67%,<br />103, set atomization efficiency to 100% |
| Smart Fan | command |turnOn | default | set to ON state |
| Smart Fan | command |turnOff | default | set to OFF state |
| Smart Fan | command | setAllStatus | power,fanMode,<br />fanSpeed,shakeRange<br/>e.g. `on,1,1,60` | power: off/on,<br />fanMode: 1/2,<br />fanSpeed: 1/2/3/4,<br />shakeRange: 0~120<br/>fanMode: 1 (Standard), 2 (Natural) |
| Color Bulb | command |turnOn | default | set to ON state |
| Color Bulb | command |turnOff | default | set to OFF state |
| Color Bulb | command |toggle | default | toggle state |
| Color Bulb | command |setBrightness | `{1-100}` | set brightness |
| Color Bulb | command |setColor | "{0-255}:{0-255}:{0-255}" | set RGB color value |
| Color Bulb | command |setColorTemperature | `{2000-6500}` | set color temperature |

#### Command set for virtual infrared remote devices

The table below describes all the available commands for virtual infrared remote devices,

| deviceType                             | commandType | Command                    | command parameter                                            | Description                                                  |
| -------------------------------------- | ----------- | -------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| All home appliance types except Others | ""          | turnOn                     | default                                                      | every home appliance can be turned on by default             |
| All home appliance types except Others | command     | turnOff                    | default                                                      | every home appliance can be turned off by default            |
| Others                                 | `customize` | {user-defined button name} | default                                                      | all user-defined buttons must be configured with commandType=customize |
| Air Conditioner                        | command     | setAll                     | {temperature},{mode},{fan speed},{power state}<br />e.g. `26,1,3,on` | the unit of temperature is in celsius; <br />modes include 1 (auto), 2 (cool), 3 (dry), 4 (fan), 5 (heat); <br />fan speed includes 1 (auto), 2 (low), 3 (medium), 4 (high); <br />power state includes on and off |
|                                        |             |                            |                                                              |                                                              |
| TV, IPTV/Streamer,  Set Top Box         | command     | SetChannel                 | {channel number}, e.g. 15                                | set the TV channel to switch to                              ||                                        | command     | setMute                    | default                                                      | mute/unmute                                                  |
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
POST https://api.switch-bot.com/v1.0/devices/210/commands
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
POST https://api.switch-bot.com/v1.0/devices/84F70353A411/commands
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
POST https://api.switch-bot.com/v1.0/devices/02-202007201626-70/commands
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
POST https://api.switch-bot.com/v1.0/devices/02-202007201626-10/commands
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
GET /v1.0/scenes
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
GET https://api.switch-bot.com/v1.0/scenes
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
POST /v1.0/scenes/{sceneId}/execute
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
POST https://api.switch-bot.com/v1.0/scenes/T02-202009221414-48924101/execute
```

Response

```js
{
    "statusCode": 100,
    "body": {},
    "message": "success"
}
```


----

* [SwitchBot (Official website)](https://www.switch-bot.com/)
* [Facebook @SwitchBotRobot](https://www.facebook.com/SwitchBotRobot/) 
* [Twitter @SwitchBot](https://twitter.com/switchbot) 
