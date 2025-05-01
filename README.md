# SwitchBot API v1.1

- [Introduction](#introduction)
- [About the New Version](#about-the-new-version)
- [Getting Started](#getting-started)
- [Authentication](#authentication)
  * [Open Token and Secret Key](#open-token-and-secret-key)
  * [How to Sign?](#how-to-sign)
    + [Python 2 example code](#python-2-example-code)
    + [Python 3 example code](#python-3-example-code)
    + [JavaScript example code](#javascript-example-code)
    + [C# example code](#c-example-code)
    + [Java 11+ example code](#java-11-example-code)
    + [PHP example code](#php-example-code)
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
      - [Curtain 3](#curtain-3)
      - [Hub/Hub Plus/Hub Mini/Hub 2/Hub 3](#hubhub-plushub-minihub-2hub-3)
      - [Meter](#meter)
      - [Meter Plus](#meter-plus)
      - [Outdoor Meter](#outdoor-meter)
      - [Meter Pro](#meter-pro)
      - [Meter Pro CO2](#meter-pro-co2)
      - [Lock](#lock)
      - [Lock Pro](#lock-pro)
      - [Lock Ultra](#lock-ultra)
      - [Keypad](#keypad)
      - [Keypad Touch](#keypad-touch)
      - [Remote](#remote)
      - [Motion Sensor](#motion-sensor)
      - [Contact Sensor](#contact-sensor)
      - [Water Leak Detector](#water-leak-detector)
      - [Ceiling Light](#ceiling-light)
      - [Ceiling Light Pro](#ceiling-light-pro)
      - [Plug Mini (US)](#plug-mini-us)
      - [Plug Mini (JP)](#plug-mini-jp)
      - [Plug](#plug)
      - [Strip Light](#strip-light)
      - [Color Bulb](#color-bulb)
      - [Robot Vacuum Cleaner S1](#robot-vacuum-cleaner-s1)
      - [Robot Vacuum Cleaner S1 Plus](#robot-vacuum-cleaner-s1-plus)
      - [Mini Robot Vacuum K10+](#mini-robot-vacuum-k10+)
      - [Mini Robot Vacuum K10+ Pro](#mini-robot-vacuum-k10+-pro)
      - [K10+ Pro Combo](#k10+-pro-combo)
      - [Floor Cleaning Robot S10](#floor-cleaning-robot-s10)
      - [Floor Cleaning Robot S20](#floor-cleaning-robot-s20)
      - [Multitasking Household Robot K20+ Pro](#multitasking-household-robot-k20-pro)
      - [Humidifier](#humidifier)
      - [Evaporative Humidifier](#evaporative-humidifier)
      - [Evaporative Humidifier (Auto-refill)](#evaporative-humidifier-auto-refill)
      - [Air Purifier VOC](#air-purifier-voc)
      - [Air Purifier Table VOC](#air-purifier-table-voc)
      - [Air Purifier PM2.5](#air-purifier-pm2.5)
      - [Air Purifier Table PM2.5](#air-purifier-table-pm2.5)
      - [Indoor Cam](#indoor-cam)
      - [Pan/Tilt Cam](#pantilt-cam)
      - [Pan/Tilt Cam 2K](#pantilt-cam-2k)
      - [Blind Tilt](#blind-tilt)
      - [Battery Circulator Fan](#battery-circulator-fan)
      - [Circulator Fan](#circulator-fan)
      - [Roller Shade](#roller-shade)
      - [Relay Switch 1PM](#relay-switch-1pm)
      - [Relay Switch 1](#relay-switch-1)
      - [Relay Switch 2PM](#relay-switch-2pm)
      - [Garage Door Opener](#Garage-Door-Opener)
      - [Floor Lamp](#Floor-Lamp)
      - [LED Strip Light 3](#LED-Strip-Light-3)
      - [Lock Lite](#Lock-Lite)
      - [Video Doorbell](#Video-Doorbell)
      - [Keypad Vision](#Keypad-Vision)
      - [Virtual infrared remote devices](#virtual-infrared-remote-devices)
    + [Sample](#sample)
      - [Get all devices](#get-all-devices)
  * [Get device status](#get-device-status)
    + [Description](#description-1)
    + [Path parameters](#path-parameters)
    + [Responses](#responses-1)
      - [Bot](#bot-1)
      - [Curtain](#curtain-1)
      - [Curtain 3](#curtain-3-1)
      - [Meter](#meter-1)
      - [Meter Plus](#meter-plus-1)
      - [Outdoor Meter](#outdoor-meter-1)
      - [Meter Pro](#meter-pro-1)
      - [Meter Pro CO2 Monitor](#meter-pro-co2-monitor-1)
      - [Lock](#lock-1)
      - [Lock Pro](#lock-pro-1)
      - [Keypad](#keypad-1)
      - [Keypad Touch](#keypad-touch-1)
      - [Motion Sensor](#motion-sensor-1)
      - [Contact Sensor](#contact-sensor-1)
      - [Water Leak Detector](#water-leak-detector-1)
      - [Ceiling Light](#ceiling-light-1)
      - [Ceiling Light Pro](#ceiling-light-pro-1)
      - [Plug Mini (US)](#plug-mini-us-1)
      - [Plug Mini (JP)](#plug-mini-jp-1)
      - [Plug](#plug-1)
      - [Strip Light](#strip-light-1)
      - [Color Bulb](#color-bulb-1)
      - [Robot Vacuum Cleaner S1](#robot-vacuum-cleaner-s1-1)
      - [Robot Vacuum Cleaner S1 Plus](#robot-vacuum-cleaner-s1-plus-1)
      - [Mini Robot Vacuum K10+](#mini-robot-vacuum-k10+-1)
      - [Mini Robot Vacuum K10+ Pro](#mini-robot-vacuum-k10+-pro-1)
      - [K10+ Pro Combo](#k10+-pro-combo-1)
      - [Multitasking Household Robot K20+ Pro](#multitasking-household-robot-k20-pro-1)
      - [Floor Cleaning Robot S10](#floor-cleaning-robot-s10-1)
      - [Floor Cleaning Robot S20](#floor-cleaning-robot-s20-1)
      - [Humidifier](#humidifier-1)
      - [Evaporative Humidifier](#evaporative-humidifier-1)
      - [Evaporative Humidifier (Auto-refill)](#evaporative-humidifier-auto-refill-1)
      - [Air Purifier VOC](#air-purifier-voc-1)
      - [Air Purifier Table VOC](#air-purifier-table-voc-1)
      - [Air Purifier PM2.5](#air-purifier-pm2.5-1)
      - [Air Purifier Table PM2.5](#air-purifier-table-pm2.5-1)
      - [Blind Tilt](#blind-tilt-1)
      - [Hub 2](#hub-2)
      - [Hub 3](#hub-3)
      - [Battery Circulator Fan](#battery-circulator-fan-1)
      - [Circulator Fan](#circulator-fan-1)
      - [Roller Shade](#roller-shade-1)
      - [Relay Switch 1PM](#relay-switch-1pm-1)
      - [Relay Switch 1](#relay-switch-1-1)
      - [Relay Switch 2PM](#relay-switch-2PM-1)
      - [Garage Door Opener](#Garage-Door-Opener-1)
      - [Floor Lamp](#Floor-Lamp-1)
      - [LED Strip Light 3](#LED-Strip-Light-3-1)
      - [Lock Lite](#Lock-Lite-1)
      - [Lock Ultra](#Lock-ultra-1)
      - [Video Doorbell](#Video-Doorbell-1)
      - [Keypad Vision](#Keypad-Vision-1)
    + [Sample](#sample-1)
      - [SwitchBot Meter example](#switchbot-meter-example)
      - [SwitchBot Curtain example](#switchbot-curtain-example)
  * [Send device control commands](#send-device-control-commands)
    + [Description](#description-2)
    + [Command set for physical devices](#command-set-for-physical-devices)
      - [Bot](#bot-2)
      - [Curtain](#curtain-2)
      - [Curtain 3](#curtain-3-2)
      - [Lock](#lock-2)
      - [Lock Pro](#lock-pro-2)
      - [Lock Ultra](#lock-ultra-2)
      - [Humidifier](#humidifier-2)
      - [Evaporative Humidifier](#evaporative-humidifier-2)
      - [Evaporative Humidifier (Auto-refill)](#evaporative-humidifier-auto-refill-2)
      - [Air Purifier VOC](#air-purifier-voc-2)
      - [Air Purifier Table VOC](#air-purifier-table-voc-2)
      - [Air Purifier PM2.5](#air-purifier-pm2.5-2)
      - [Air Purifier Table PM2.5](#air-purifier-table-pm2.5-2)
      - [Plug](#plug-2)
      - [Plug Mini (US)](#plug-mini-us-2)
      - [Plug Mini (JP)](#plug-mini-jp-2)
      - [Color Bulb](#color-bulb-2)
      - [Strip Light](#strip-light-2)
      - [Robot Vacuum Cleaner S1](#robot-vacuum-cleaner-s1-2)
      - [Robot Vacuum Cleaner S1 Plus](#robot-vacuum-cleaner-s1-plus-2)
      - [Mini Robot Vacuum K10+](#mini-robot-vacuum-k10+-2)
      - [Mini Robot Vacuum K10+ Pro](#mini-robot-vacuum-k10+-pro-2)
      - [K10+ Pro Combo](#k10+-pro-combo-2)
      - [Multitasking Household Robot K20+ Pro](#multitasking-household-robot-k20-pro-2)
      - [Floor Cleaning Robot S10](#floor-cleaning-robot-s10-2)
      - [Floor Cleaning Robot S20](#floor-cleaning-robot-s20-2)
      - [Ceiling Light](#ceiling-light-2)
      - [Ceiling Light Pro](#ceiling-light-pro-2)
      - [Keypad](#keypad-2)
      - [Keypad Touch](#keypad-touch-2)
      - [Blind Tilt](#blind-tilt-2)
      - [Battery Circulator Fan](#battery-circulator-fan-2)
      - [Circulator Fan](#circulator-fan-2)
      - [Roller Shade](#roller-shade-2)
      - [Relay Switch 1PM](#relay-switch-1pm-2)
      - [Relay Switch 1](#relay-switch-1-2)
      - [Relay Switch 2PM](#relay-switch-2pm-2)
      - [Garage Door Opener](#Garage-Door-Opener-2)
      - [Floor Lamp](#Floor-Lamp-2)
      - [LED Strip Light 3](#LED-Strip-Light-3-2)
      - [Video Doorbell](#Video-Doorbell-2)
      - [Keypad Vision](#Keypad-Vision-2)
    + [Command set for virtual infrared remote devices](#command-set-for-virtual-infrared-remote-devices)
    + [Path parameters](#path-parameters-1)
    + [Request body parameters](#request-body-parameters)
    + [Response](#response)
    + [Errors](#errors)
    + [Sample](#sample-2)
      - [Floor Cleaning Robot S10 example](#floor-cleaning-robot-s10-example)
      - [Floor Cleaning Robot S20 example](#floor-cleaning-robot-s20-example)
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
    + [Bot](#bot-3)
    + [Curtain](#curtain-3)
    + [Curtain 3](#curtain-3-3)
    + [Motion Sensor](#motion-sensor-2)
    + [Contact Sensor](#contact-sensor-2)
    + [Water Leak Detector](#water-leak-detector-2)
    + [Meter](#meter-2)
    + [Meter Plus](#meter-plus-2)
    + [Outdoor Meter](#outdoor-meter-2)
    + [Meter Pro](#meter-pro-2)
    + [Meter Pro CO2 Monitor](#meter-pro-co2-monitor-2)
    + [Lock](#lock-3)
    + [Lock Pro](#lock-pro-3)
    + [Indoor Cam](#indoor-cam-1)
    + [Pan/Tilt Cam](#pantilt-cam-1)
    + [Color Bulb](#color-bulb-3)
    + [LED Strip Light](#led-strip-light)
    + [Plug Mini (US)](#plug-mini-us-3)
    + [Plug Mini (JP)](#plug-mini-jp-3)
    + [Robot Vacuum Cleaner S1](#robot-vacuum-cleaner-s1-3)
    + [Robot Vacuum Cleaner S1 Plus](#robot-vacuum-cleaner-s1-plus-3)
    + [Mini Robot Vacuum K10+](#mini-robot-vacuum-k10+-3)
    + [Mini Robot Vacuum K10+ Pro](#mini-robot-vacuum-k10+-pro-3)
    + [K10+ Pro Combo](#k10+-pro-combo-3)
    + [Multitasking Household Robot K20+ Pro](#multitasking-household-robot-k20-pro-3)
    + [Floor Cleaning Robot S10](#floor-cleaning-robot-s10-3)
    + [Floor Cleaning Robot S20](#floor-cleaning-robot-s20-3)
    + [Ceiling Light](#ceiling-light-3)
    + [Ceiling Light Pro](#ceiling-light-pro-3)
    + [Keypad](#keypad-3)
      - [Create a passcode](#create-a-passcode)
      - [Delete a passcode](#delete-a-passcode)
    + [Keypad Touch](#keypad-touch-3)
      - [Create a passcode](#create-a-passcode-1)
      - [Delete a passcode](#delete-a-passcode-1)
    + [Hub 2](#hub-2-1)
    + [Hub 3](#hub-3-1)
    + [Battery Circulator Fan](#battery-circulator-fan-3)
    + [Circulator Fan](#circulator-fan-3)
    + [Roller Shade](#roller-shade-3)
    + [Relay Switch 1PM](#relay-switch-1pm-3)
    + [Relay Switch 1](#relay-switch-1-3)
    + [Relay Switch 2PM](#relay-switch-2pm-3)
    + [Evaporative Humidifier](#evaporative-humidifier-3)
    + [Evaporative Humidifier (Auto-refill)](#evaporative-humidifier-auto-refill-3)
    + [Air Purifier VOC](#air-purifier-voc-3)
    + [Air Purifier Table VOC](#air-purifier-table-voc-3)
    + [Air Purifier PM2.5](#air-purifier-pm2.5-3)
    + [Air Purifier Table PM2.5](#air-purifier-table-pm2.5-3)
    + [Garage Door Opener](#Garage-Door-Opener-3)
    + [Floor Lamp](#Floor-Lamp-3)
    + [LED Strip Light 3](#LED-Strip-Light-3-3)
    + [Lock Lite](#Lock-Lite-3)
    + [Video Doorbell](#Video-Doorbell-3)
    + [Keypad Vision](#Keypad-Vision-3)
    + [Lock Ultra](#lock-ultra-3)

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
    For app version ≥ V9.0,
    a) Go to Profile > Preferences > About
    b) Tap App Version 10 times. Developer Options will show up
    c) Tap Developer Options
    d) Tap Get Token

  For app version < V9.0,
  a) Go to Profile > Preferences
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

We have attached some scripts for you to quickly generate a sign. If you prefer to write your own script or routine, here is the procedure.

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

#### Python 2 example code

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

#### Python 3 example code

```python
import json
import time
import hashlib
import hmac
import base64
import uuid

# Declare empty header dictionary
apiHeader = {}
# open token
token = '' # copy and paste from the SwitchBot app V6.14 or later
# secret key
secret = '' # copy and paste from the SwitchBot app V6.14 or later
nonce = uuid.uuid4()
t = int(round(time.time() * 1000))
string_to_sign = '{}{}{}'.format(token, t, nonce)

string_to_sign = bytes(string_to_sign, 'utf-8')
secret = bytes(secret, 'utf-8')

sign = base64.b64encode(hmac.new(secret, msg=string_to_sign, digestmod=hashlib.sha256).digest())
print ('Authorization: {}'.format(token))
print ('t: {}'.format(t))
print ('sign: {}'.format(str(sign, 'utf-8')))
print ('nonce: {}'.format(nonce))

#Build api header JSON
apiHeader['Authorization']=token
apiHeader['Content-Type']='application/json'
apiHeader['charset']='utf8'
apiHeader['t']=str(t)
apiHeader['sign']=str(sign, 'utf-8')
apiHeader['nonce']=str(nonce)

```

#### JavaScript example code

```javascript
const crypto = require('crypto');
const https = require('https');

const token = "yourToken";
const secret = "yourSecret";
const t = Date.now();
const nonce = "requestID";
const data = token + t + nonce;
const sign = crypto
    .createHmac('sha256', secret)
    .update(data)
    .digest('base64');
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

#### C# example code

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

#### Java 11+ example code

```java
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;
import java.net.http.HttpResponse.BodyHandlers;
import java.time.Instant;
import java.util.Base64;
import java.util.UUID;

import javax.crypto.Mac;
import javax.crypto.spec.SecretKeySpec;

public class Main {
    public static void main(String[] args) throws Exception {
    	
      String token = args[0];
      String secret = args[1];
      String nonce = UUID.randomUUID().toString();
      String time= "" + Instant.now().toEpochMilli();
      String data = token + time + nonce;
      
      SecretKeySpec secretKeySpec = new SecretKeySpec(secret.getBytes("UTF-8"), "HmacSHA256");
      Mac mac = Mac.getInstance("HmacSHA256");
      mac.init(secretKeySpec);
      String signature = new String(Base64.getEncoder().encode(mac.doFinal(data.getBytes("UTF-8"))));      
      
      HttpRequest getDevices = HttpRequest.newBuilder()
      .uri(new URI("https://api.switch-bot.com/v1.1/devices"))
      .header("Authorization", token)
      .header("sign", signature)
      .header("nonce", nonce)
      .header("t", time)
      .GET()
      .build();
      
      HttpResponse<String> response = HttpClient.newBuilder().build().send(getDevices, BodyHandlers.ofString());
      
      System.out.println(response.body());
    }
}
```

#### PHP example code 

```php
<?php
$token = 'XXXXXXXXXXXXXXXXXXX';
$secret = 'YYYYYYYYYYY';
$nonce = guidv4();
$t = time() * 1000;
$data = utf8_encode($token . $t . $nonce);
$sign = hash_hmac('sha256', $data, $secret,true);
$sign = strtoupper(base64_encode($sign));

$url = "https://api.switch-bot.com/v1.1/devices";

$curl = curl_init($url);
curl_setopt($curl, CURLOPT_URL, $url);
curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);

$headers = array(
    "Content-Type:application/json",
    "Authorization:" . $token,
    "sign:" . $sign,
    "nonce:" . $nonce,
    "t:" . $t
);

curl_setopt($curl, CURLOPT_HTTPHEADER, $headers);
$response = curl_exec($curl);
curl_close($curl);

function guidv4($data = null) {
    // Generate 16 bytes (128 bits) of random data or use the data passed into the function.
    $data = $data ?? random_bytes(16);
    assert(strlen($data) == 16);
    $data[6] = chr(ord($data[6]) & 0x0f | 0x40);
    $data[8] = chr(ord($data[8]) & 0x3f | 0x80);

    // Output the 36 character UUID.
    return vsprintf('%s%s-%s-%s-%s-%s%s%s', str_split(bin2hex($data), 4));
}

```

#### Swift example code

```swift
import CryptoKit 

let token = 'TTTTTTT'
let secret = 'SSSS'

func getDevices() async throws -> Any {
    let hostname = "https://api.switch-bot.com"
    
    var components = URLComponents(string: hostname)!
    components.path = "/v1.1/devices"
    components.port = 443
    
    var request = URLRequest(url: components.url!)
    
    request.setValue("application/json", forHTTPHeaderField: "Content-Type")
    request.setValue("utf-8", forHTTPHeaderField: "charset")
    let timestamp = Int(Date().timeIntervalSince1970.rounded() * 1000) // Date().timeInterval returns seconds, not milliseconds, since1970
    let nonce =  UUID().uuidString
    
    let timeAdjustedToken = token + "\(timestamp)" + nonce
    let key = SymmetricKey(data: Data(secret.utf8))
    let authenticationCode = HMAC<SHA256>.authenticationCode(for: Data(timeAdjustedToken.utf8), using: key)
    let signatureToken = Data(authenticationCode).base64EncodedString()

    request.setValue(token, forHTTPHeaderField: "Authorization")
    request.setValue(signatureToken, forHTTPHeaderField: "sign")
    request.setValue(nonce, forHTTPHeaderField: "nonce")
    request.setValue("\(timestamp)", forHTTPHeaderField: "t")
    
    let (data, response) = try await URLSession.shared.data(for: request)
    return try JSONSerialization.jsonObject(with: data)
}
```

## Glossary

The following table provides definitions to the terms to be frequently mentioned in the subsequent sections.

| Term                         | Description                                                  | Model No.             | Availability                      |
| ---------------------------- | ------------------------------------------------------------ | --------------------- | --------------------------------- |
| Hub Mini                     | Short for SwitchBot Hub Mini                                 | W0202200              |                                   |
| Hub Plus                     | Short for SwitchBot Hub Plus                                 | SwitchBot Hub S1      |                                   |
| Hub 2                        | Short for SwitchBot Hub 2                                    | W3202100              |                                   |
| Hub 3                        | Short for SwitchBot Hub 3                                    | W7202100              ||
| Bot                          | Short for SwitchBot Bot                                      | SwitchBot S1          |                                   |
| Curtain                      | Short for SwitchBot Curtain                                  | W0701600              |                                   |
| Curtain 3                    | Short for SwitchBot Curtain 3                                | W2400000              |                                   |
| Plug                         | Short for SwitchBot Plug                                     | SP11                  | Currently only available in Japan |
| Meter                        | Short for SwitchBot Thermometer and Hygrometer               | SwitchBot MeterTH S1  |                                   |
| Meter Plus (JP)              | Short for SwitchBot Thermometer and Hygrometer Plus (JP).    | W2201500              | Only available in Japan |
| Meter Plus (US)              | Short for SwitchBot Thermometer and Hygrometer Plus (US)     | W2301500              | Only available in US |
| Outdoor Meter                | Short for Indoor/Outdoor Thermo-Hygrometer                   | W3400010              |                                   |
| Meter Pro | Short for SwitchBot Meter Pro | W4900000 | |
| Meter Pro (CO2 Monitor) | Short for SwitchBot Meter Pro (CO2 Monitor) | W4900010 | |
| Motion Sensor                | Short for SwitchBot Motion Sensor                            | W1101500              |                                   |
| Contact Sensor               | Short for SwitchBot Contact Sensor                           | W1201500              |                                   |
| Water Leak Detector | Short for SwitchBot Water Leak Detector                               | W4402000              |                                   |
| Color Bulb                   | Short for SwitchBot Color Bulb                               | W1401400              |                                   |
| Strip Light                  | Short for SwitchBot LED Strip Light                          | W1701100              |                                   |
| Plug Mini (US)               | Short for SwitchBot Plug Mini (US)                           | W1901400 and W1901401 | Only available in US |
| Plug Mini (JP)               | Short for SwitchBot Plug Mini (JP)                           | W2001400 and W2001401 | Only available in Japan |
| Lock                         | Short for SwitchBot Lock                                     | W1601700              |                                   |
| Lock Pro                     | Short for SwitchBot Lock Pro                                 | W3500000              |                                   |
| Keypad                       | Short for SwitchBot Lock                                     | W2500010              |                                   |
| Keypad Touch                 | Short for SwitchBot Lock                                     | W2500020              |                                   |
| S1      | Short for SwitchBot Robot Vacuum Cleaner S1                  | W3011000              |                                   |
| S1 Plus | Short for SwitchBot Robot Vacuum Cleaner S1 Plus             | W3011010              |                                   |
| K10+ | Short for SwitchBot Mini Robot Vacuum K10+ | W3011020 | |
| K10+ Pro | Short for SwitchBot Mini Robot Vacuum K10+ Pro | W3011026 | |
| S10   | Short for SwitchBot Floor Cleaning Robot S10                 | W3211800              |                                   |
| S20   | Short for SwitchBot Floor Cleaning Robot S10                 | W6602310            |                                   |
| K10+ Pro Combo | Short for SwitchBot Robot Vacuum K10+ Pro Combo | W3002500 | |
| K20+ Pro | Short for SwitchBot Multitasking Household Robot K20+ Pro | W3002520 | |
| Ceiling Light                | Short for SwitchBot Ceiling Light                            | W2612230 and W2612240 | Currently only available in Japan |
| Ceiling Light Pro            | Short for SwitchBot Ceiling Light Pro                        | W2612210 and W2612220 | Currently only available in Japan |
| Indoor Cam                   | Short for SwitchBot Indoor Cam                               | W1301200              |                                   |
| Pan/Tilt Cam                 | Short for SwitchBot Pan/Tilt Cam                             | W1801200              |                                   |
| Pan/Tilt Cam 2K              | Short for SwitchBot Pan/Tilt Cam 2K                          | W3101100              |                                   |
| Blind Tilt                   | Short for SwitchBot Blind Tilt                               | W2701600              |                                   |
| Battery Circulator Fan       | Short for SwitchBot Battery Circulator Fan                   | W3800510              |                                   |
| Circulator Fan | Short for SwitchBot Circulator Fan | W3800511 | |
| Evaporative Humidifier | Short for SwitchBot Evaporative Humidifier | W3902300 | |
| Evaporative Humidifier (Auto-refill) | Short for SwitchBot Evaporative Humidifier (Auto-refill) | W3902310 | |
| Air Purifier PM2.5 | Short for SwitchBot Air Purifier | W5302300 | |
| Air Purifier Table PM2.5 | Short for SwitchBot Air Purifier Table | W5302310 | |
| Air Purifier VOC | Short for SwitchBot Air Purifier | W5302300 | Currently only available in Japan |
| Air Purifier Table VOC | Short for SwitchBot Air Purifier Table | W5302310 | Currently only available in Japan |
| Roller Shade | Short for SwitchBot Roller Shade | W5000000 |  |
| Relay Switch 1PM | Short for SwitchBot Relay Switch 1PM | W5502310 |  |
| Relay Switch 1 | Short for SwitchBot Relay Switch 1 | W5502300 |  |
| Relay Switch 2PM | Short for SwitchBot Relay Switch 2PM | W5502320 |  |
| Garage Door Opener | Short for SwitchBot Garage Door Opener | W5502330 |  |
| Floor Lamp | Short for SwitchBot RGBWW Floor Lamp | W1702100 |  |
| Strip Light 3 | Short for SwitchBot RGBWW Strip Light 3 | W1702110 |  |
| Lock Lite | Short for SwitchBot Lock Lite | W5110000 |  |
| Video Doorbell | Short for SwitchBot Video Doorbell | W6702000 |  |
| Keypad Vision | Short for SwitchBot Keypad Vision | W5600003 |  |
| Lock Ultra | Short for SwitchBot Lock Ultra | W5600000 |  |
### `Legacy` Cloud Services

> Important note: Beyond V9.0, there will NOT be a Cloud Services option in the app. You will see Third-party Services instead. Please read this article for more information, https://support.switch-bot.com/hc/en-us/articles/7257579858455

A SwitchBot app feature, which appears in the app <V9.0 that

 1. Enables SwitchBot products to be discovered and communicated with third-party services such as Home Assistant, Alexa, Google Home, IFTTT, SmartThings, and so forth
 2. Allows users to create customized smart scenes and  widgets. For BLE-based devices such as Bot and Curtain
 3. You MUST first add a SwitchBot Hub such as Hub 2, Hub Mini with Matter Enabled, or Hub Mini
 4. Then enable Cloud Services on the Settings page in order to make use of the web API!



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

> Note: For devices that communicate via BLE, please enable Cloud Services on SwitchBot app first.

Physical devices refer to the following SwitchBot products,
 -  Hub
 -  Hub Plus
 -  Hub Mini
 -  Bot
 -  Curtain
 -  Plug
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
 -  Robot Vacuum Cleaner S1
 -  Robot Vacuum Cleaner S1 Plus
 -  Keypad
 -  Keypad Touch
 -  Ceiling Light
 -  Ceiling Light Pro
 -  Blind Tilt
 -  Hub 2
 -  Hub 3
 -  Outdoor Meter
 -  Battery Circulator Fan
 -  Curtain 3
 -  Lock Pro
 -  Floor Cleaning Robot S10
 -   Water Leak Detector
 -  Mini Robot Vacuum K10+
 -  Mini Robot Vacuum K10+ Pro
 -  Meter Pro
 -  Meter Pro CO2
 -  Circulator Fan
 -  Evaporative Humidifier
 -  Evaporative Humidifier (Auto-refill)
 -  K10+ Pro Combo
 -  Air Purifier VOC
 -  Air Purifier Table VOC
 -  Air Purifier PM2.5
 -  Air Purifier Table PM2.5
 -  Roller Shade
 -  Relay Switch 1PM
 -  Relay Switch 1
 -  `new` Hub 3
 -  `new` Relay Switch 2PM
 -  `new` S20
 -  `new` Floor Lamp 
 -  `new` Strip Light 3
 -  `new` Garage Door Opener
 -  `new` Lock Lite
 -  `new` Video Doorbell
 -  `new` Keypad Vision
 -  `new` Lock Ultra
 -  `new` K20+ Pro

Virtual infrared remote devices refer to virtual devices that are used to simulate infrared signals of a home appliance remote control. A SwitchBot Hub Plus, Hub Mini, Hub 2, or Ceiling Light is required in order to be able to create these virtual devices within the app. The types of appliances supported include,
 -  Air Conditioner
 -  TV
 -  Light
 -  Streamer
 -  Set Top Box
 -  DVD Player
 -  Fan
 -  Projector
 -  Camera
 -  Air Purifier
 -  Speaker
 -  Water Heater
 -  Robot Vacuum Cleaner
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

##### Curtain 3

| Key                | Value Type      | Description                                                  |
| ------------------ | --------------- | ------------------------------------------------------------ |
| deviceId           | String          | device ID                                                    |
| deviceName         | String          | device name                                                  |
| deviceType         | String          | device type. *Curtain3*                                      |
| enableCloudService | Boolean         | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String          | device's parent Hub ID                                       |
| curtainDevicesIds  | Array<deviceId> | a list of Curtain device IDs such that the Curtain devices are being paired or grouped |
| calibrate          | Boolean         | determines if the open position and the close position of a device have been properly calibrated or not |
| group              | Boolean         | determines if a Curtain is paired with or grouped with another Curtain or not |
| master             | Boolean         | determines if a Curtain is the master device or not when paired with or grouped with another Curtain |
| openDirection      | String          | the opening direction of a Curtain                           |

##### Hub/Hub Plus/Hub Mini/Hub 2/Hub 3

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Hub*, *Hub Plus*, *Hub Mini*, *Hub 2* or *Hub 3*. |
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

##### Outdoor Meter

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *WoIOSensor*                                    |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                       |

##### Meter Pro

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *MeterPro*                                     |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                       |

##### Meter Pro CO2

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *MeterPro(CO2)*                                 |
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
| groupName              | String         | the name of the Lock group |
| lockDevicesIds              | Array<deviceId>         | a list of Lock device IDs such that the Lock devices are being grouped in Dual Lock mode |

##### Lock Pro

| Key                | Value Type      | Description                                                  |
| ------------------ | --------------- | ------------------------------------------------------------ |
| deviceId           | String          | device ID                                                    |
| deviceName         | String          | device name                                                  |
| deviceType         | String          | device type. *Smart Lock Pro*                |
| enableCloudService | Boolean         | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String          | device's parent Hub ID                                       |
| group              | Boolean         | determines if a Lock is grouped with another Lock or not |
| master             | Boolean         | determines if a Lock is the master device or not when grouped with another Lock in Dual Lock mode |
| groupName              | String         | the name of the Lock group |
| lockDevicesIds              | Array<deviceId>         | a list of Lock device IDs such that the Lock devices are being grouped in Dual Lock mode |

##### Lock Ultra

| Key                | Value Type      | Description                                                  |
| ------------------ | --------------- | ------------------------------------------------------------ |
| deviceId           | String          | device ID                                                    |
| deviceName         | String          | device name                                                  |
| deviceType         | String          | device type. *Smart Lock Ultra*                |
| enableCloudService | Boolean         | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String          | device's parent Hub ID                                       |
| group              | Boolean         | determines if a Lock is grouped with another Lock or not |
| master             | Boolean         | determines if a Lock is the master device or not when grouped with another Lock in Dual Lock mode |
| groupName              | String         | the name of the Lock group |
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

##### Water Leak Detector
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Water Detector*                                |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

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

##### Mini Robot Vacuum K10+

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *K10+*                                          |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Mini Robot Vacuum K10+ Pro

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *K10+ Pro*                                      |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### K10+ Pro Combo

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Robot Vacuum Cleaner K10+ Pro Combo*           |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | returns `null` if not a bluetooth device                     |

##### Floor Cleaning Robot S10

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Robot Vacuum Cleaner S10*                      |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### S20

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Robot Vacuum Cleaner S20*                      |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### K20+ Pro

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Robot Vacuum Cleaner K20 Plus Pro*                      |
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

##### Evaporative Humidifier
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Humidifier2*                                   |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | returns `null` if not a bluetooth device                     |

##### Evaporative Humidifier (Auto-refill)
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Humidifier2*                                   |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | returns `null` if not a bluetooth device                     |

##### Air Purifier VOC

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Air Purifier VOC*                              |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | returns `null` if not a bluetooth device                     |

##### Air Purifier Table VOC

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Air Purifier Table VOC*                        |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | returns `null` if not a bluetooth device                     |

##### Air Purifier PM2.5

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Air Purifier PM2.5*                            |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | returns `null` if not a bluetooth device                     |

##### Air Purifier Table PM2.5

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Air Purifier Table PM2.5*                      |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | returns `null` if not a bluetooth device                     |

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
| deviceType         | String     | device type. *Pan/Tilt Cam 2K*                                    |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Blind Tilt
| Key                 | Value Type      | Description                                                  |
| ------------------- | --------------- | ------------------------------------------------------------ |
| deviceId            | String          | device ID                                                    |
| deviceName          | String          | device name                                                  |
| deviceType          | String          | device type. *Blind Tilt*                                    |
| version             | Integer         | the version of the device                                    |
| enableCloudService  | Boolean         | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId         | String          | device's parent Hub ID                                       |
| blindTiltDevicesIds | Array<deviceId> | a list of Blind Tilt device IDs such that the Blind Tilt devices are being paired or grouped |
| calibrate           | Boolean         | determines if the open and the closed positions have been properly calibrated or not |
| group               | Boolean         | determines if a Blind Tilt device is paired with or grouped with one or more devices of the same type or not |
| master              | Boolean         | determines if a Blind Tilt device is the master device or not when paired with or grouped with one or more devices of the same type |
| direction           | String          | the opening direction of a Blind Tilt device                 |
| slidePosition       | Integer         | the current position, 0-100                                  |

##### Battery Circulator Fan
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Battery Circulator Fan*                        |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                       |

##### Circulator Fan

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Circulator Fan*                        |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                       |

##### Roller Shade

| Key                | Value Type      | Description                                                  |
| ------------------ | --------------- | ------------------------------------------------------------ |
| deviceId           | String          | device ID                                                    |
| deviceName         | String          | device name                                                  |
| deviceType         | String          | device type. *Roller Shade*                                  |
| bleVersion         | Integer         | firmware version                                             |
| enableCloudService | Boolean         | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String          | device's parent Hub ID                                       |
| groupingDevicesIds | Array<deviceId> | a list of device IDs such that the Roller Shade devices are being paired or grouped |
| group              | Boolean         | determines if a device is paired with or grouped with one or more devices of the same type or not |
| master             | Boolean         | determines if a device is the master device or not when paired with or grouped with one or more devices of the same type |
| groupName          | String          | the name of the device group                                 |

##### Relay Switch 1PM
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Relay Switch 1PM*                              |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Relay Switch 1
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Relay Switch 1*                                |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Relay Switch 2PM
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Relay Switch 2PM*                              |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Garage Door Opener
| Key         | Value Type | Description                   |
| ----------- | ---------- | ----------------------------- |
| deviceId    | String     | device ID                     |
| deviceName  | String     | device name                   |
| deviceType  | String     | device type. *Garage Door Opener*     |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                       |

##### Floor Lamp
| Key         | Value Type | Description                   |
| ----------- | ---------- | ----------------------------- |
| deviceId    | String     | device ID                     |
| deviceName  | String     | device name                   |
| deviceType  | String     | device type. *Floor Lamp*     |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                       |

##### Strip Light 3
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *LED Strip Light 3*                                   |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |                          |

##### Lock Lite
| Key                | Value Type      | Description                                                  |
| ------------------ | --------------- | ------------------------------------------------------------ |
| deviceId           | String          | device ID                                                    |
| deviceName         | String          | device name                                                  |
| deviceType         | String          | device type. *Lock Lite*                                  |
| enableCloudService | Boolean         | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String          | device's parent Hub ID                                       |
| group              | Boolean         | determines if a Lock is grouped with another Lock or not |
| master             | Boolean         | determines if a Lock is the master device or not when grouped with another Lock in Dual Lock mode |
| groupName              | String         | the name of the Lock group |
| lockDevicesIds              | Array<deviceId>         | a list of Lock device IDs such that the Lock devices are being grouped in Dual Lock mode |

##### Video Doorbell
| Key         | Value Type | Description                   |
| ----------- | ---------- | ----------------------------- |
| deviceId    | String     | device ID                     |
| deviceName  | String     | device name                   |
| deviceType  | String     | device type. *Video Doorbell*       |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                       |

##### Keypad Vision
| Key         | Value Type | Description                   |
| ----------- | ---------- | ----------------------------- |
| deviceId    | String     | device ID                     |
| deviceName  | String     | device name                   |
| deviceType  | String     | device type. *Keypad Vision*    |
| enableCloudService | Boolean    | determines if Cloud Service is enabled or not for the current device |
| hubDeviceId        | String     | device's parent Hub ID                                       |
| lockDeviceId       | String     | MAC address of the Lock that the current device is paired with |
| keyList            | Object     | a list of passcodes                                          |

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
 -  Robot Vacuum Cleaner S1
 -  Robot Vacuum Cleaner S1 Plus
 -  Keypad
 -  Keypad Touch
 -  Ceiling Light
 -  Ceiling Light Pro
 -  Hub 2
 -  Outdoor Meter
 -  Battery Circulator Fan
 -  Lock Pro
 -  Floor Cleaning Robot S10
 -  Water Leak Detector
 -  Mini Robot Vacuum K10+
 -  Mini Robot Vacuum K10+ Pro
 -  Meter Pro
 -  Meter Pro CO2
 -  Circulator Fan
 -  Evaporative Humidifier
 -  Evaporative Humidifier (Auto-refill)
 -  K10+ Pro Combo
 -  Air Purifier VOC
 -  Air Purifier Table VOC
 -  Air Purifier PM2.5
 -  Air Purifier Table PM2.5
 -  Roller Shade
 -  Relay Switch 1PM
 -  Relay Switch 1
 -  `new` Hub 3
 -  `new` Relay Switch 2PM
 -  `new` Garage Door Opener
 -  `new` S20
 -  `new` Floor Lamp 
 -  `new` Strip Light 3
 -  `new` Lock Lite
 -  `new` Lock Ultra
 -  `new` Video Doorbell
 -  `new` Keypad Vision
 -  `new` K20+ Pro
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
| battery              | Integer | the current battery level, 0-100 |
| version              | String     | the current firmware version, e.g. V6.3 |
| deviceMode              | String     | *pressMode*, *switchMode*, or *customizeMode*                                                 |
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
| battery              | Integer | the current battery level, 0-100 |
| version              | String     | the current firmware version, e.g. V4.2 |
| slidePosition      | String          | the percentage of the distance between the calibrated open position and closed position that Curtain has traversed |

##### Curtain 3
| Key                | Value Type      | Description                                                  |
| ------------------ | --------------- | ------------------------------------------------------------ |
| deviceId           | String          | device ID                                                    |
| deviceType         | String          | device type. *Curtain3*                           |
| hubDeviceId        | String          | device's parent Hub ID                                       |
| calibrate          | Boolean         | determines if the open position and the close position of a device have been properly calibrated or not |
| group              | Boolean         | determines if a Curtain is paired with or grouped with another Curtain or not |
| moving             | Boolean         | determines if a Curtain is moving or not |
| battery              | Integer | the current battery level, 0-100 |
| version              | String     | the current firmware version, e.g. V4.2 |
| slidePosition      | String          | the percentage of the distance between the calibrated open position and closed position that Curtain has traversed |

##### Meter
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Meter*                                         |
| hubDeviceId        | String     | device's parent Hub ID                                       |
| temperature            | Float      |  temperature in celsius                                       |
| version              | String     | the current firmware version, e.g. V4.2 |
| battery              | Integer | the current battery level, 0-100 |
| humidity               | Integer    | humidity percentage |


##### Meter Plus
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *MeterPlus*                                         |
| hubDeviceId        | String     | device's parent Hub ID                                       |
| battery              | Integer | the current battery level, 0-100 |
| version              | String     | the current firmware version, e.g. V4.2 |
| temperature            | Float      |  temperature in celsius                                       |
| humidity               | Integer    | humidity percentage |

##### Outdoor Meter
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *WoIOSensor*                                         |
| hubDeviceId        | String     | device's parent Hub ID                                       |
| battery              | Integer | the current battery level, 0-100 |
| version              | String     | the current firmware version, e.g. V4.2 |
| temperature            | Float      |  temperature in celsius                                       |
| humidity               | Integer    | humidity percentage |

##### Meter Pro

| Key         | Value Type | Description                             |
| ----------- | ---------- | --------------------------------------- |
| deviceId    | String     | device ID                               |
| deviceType  | String     | device type. *MeterPro*                |
| hubDeviceId | String     | device's parent Hub ID                  |
| battery     | Integer    | the current battery level, 0-100        |
| version     | String     | the current firmware version, e.g. V4.2 |
| temperature | Float      | temperature in celsius                  |
| humidity    | Integer    | humidity percentage                     |

##### Meter Pro CO2

| Key         | Value Type | Description                             |
| ----------- | ---------- | --------------------------------------- |
| deviceId    | String     | device ID                               |
| deviceType  | String     | device type. *MeterPro(CO2)*   |
| hubDeviceId | String     | device's parent Hub ID                  |
| battery     | Integer    | the current battery level, 0-100        |
| version     | String     | the current firmware version, e.g. V4.2 |
| temperature | Float      | temperature in celsius                  |
| humidity    | Integer    | humidity percentage                     |
| CO2    | Integer    | CO2 ppm value, 0-9999 |

##### Lock

| Key                | Value Type      | Description                                                  |
| ------------------ | --------------- | ------------------------------------------------------------ |
| deviceId           | String          | device ID                                                    |
| deviceType         | String          | device type. *Smart Lock*                                    |
| hubDeviceId        | String          | device's parent Hub ID                                       |
| battery              | Integer | the current battery level, 0-100 |
| version              | String     | the current firmware version, e.g. V4.2 |
| lockState              | String     | determines if locked or not |
| doorState              | String     | determines if the door is closed or not  |
| calibrate          | Boolean         | determines if Lock has been calibrated or not |

##### Lock Pro
| Key                | Value Type      | Description                                                  |
| ------------------ | --------------- | ------------------------------------------------------------ |
| deviceId           | String          | device ID                                                    |
| deviceType         | String          | device type. *Smart Lock Pro*                                |
| hubDeviceId        | String          | device's parent Hub ID                                       |
| battery              | Integer | the current battery level, 0-100 |
| version              | String     | the current firmware version, e.g. V4.2 |
| lockState              | String     | determines if locked or not, *jammed*, *unlock* or *lock* |
| doorState              | String     | determines if the door is closed or not, *open* or *close* |
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
| battery              | Integer | the current battery level, 0-100 |
| version              | String     | the current firmware version, e.g. V4.2 |
| moveDetected           | Boolean    | determines if motion is detected |
| brightness             | String     | the ambient brightness picked up by the sensor. *bright*  or *dim* |

##### Contact Sensor

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Contact Sensor*                                |
| hubDeviceId        | String     | device's parent Hub ID                                       |
| battery              | Integer | the current battery level, 0-100 |
| version              | String     | the current firmware version, e.g. V4.2 |
| moveDetected           | Boolean    | determines if motion is detected |
| openState  | String | the open state of the sensor. *open*, *close*, or *timeOutNotClose* |
| brightness             | String     | the ambient brightness picked up by the sensor. *bright*  or *dim* |

##### Water Leak Detector

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Water Detector*                  |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| battery              | Integer | the current battery level, `0-100` |
| version              | String     | the current firmware version, e.g. V4.2 |
| status | Integer | `0`, dry. `1`, leak detected |

##### Ceiling Light

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Ceiling Light*                                 |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| power | String | ON/OFF state |
| version              | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |
| brightness | Integer | the brightness value, range from 1 to 100 |
| colorTemperature | Integer | the color temperature value, range from 2700 to 6500 |

##### Ceiling Light Pro

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Ceiling Light Pro*                             |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| version              | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |
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
| version              | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |
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
| version              | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |
| weight                 | Float      | the power consumed in a day, measured in Watts |
| electricityOfDay       | Integer    | the duration that the device has been used during a day, measured in minutes  |
| electricCurrent        | Float      | the current of the device at the moment, measured in Amp |

##### Plug
| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Plug*                        |
| power | String | ON/OFF state |
| version              | String     | the current Wi-Fi firmware version, e.g. V4.2 |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |

##### Strip Light

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Strip Light*                                   |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| power                  | String     | ON/OFF state                                                 |
| version              | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |
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
| version              | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |
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

##### Mini Robot Vacuum K10+

| Key           | Value Type | Description                                                  |
| ------------- | ---------- | ------------------------------------------------------------ |
| deviceId      | String     | device ID                                                    |
| deviceName    | String     | device name                                                  |
| deviceType    | String     | device type. *K10+*                                          |
| hubDeviceId   | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| workingStatus | String     | the working status of the device. *StandBy*, *Clearing*, *Paused*, *GotoChargeBase*, *Charging*, *ChargeDone*, *Dormant*, *InTrouble*, *InRemoteControl*, or *InDustCollecting* |
| onlineStatus  | String     | the connection status of the device. *online* or *offline*   |
| battery       | Integer    | the current battery level `0-100`                            |

##### Mini Robot Vacuum K10+ Pro

| Key           | Value Type | Description                                                  |
| ------------- | ---------- | ------------------------------------------------------------ |
| deviceId      | String     | device ID                                                    |
| deviceName    | String     | device name                                                  |
| deviceType    | String     | device type. *K10+ Pro*                                      |
| hubDeviceId   | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| workingStatus | String     | the working status of the device. *StandBy*, *Clearing*, *Paused*, *GotoChargeBase*, *Charging*, *ChargeDone*, *Dormant*, *InTrouble*, *InRemoteControl*, or *InDustCollecting* |
| onlineStatus  | String     | the connection status of the device. *online* or *offline*   |
| battery       | Integer    | the current battery level `0-100`                            |

##### K10+ Pro Combo
| Key           | Value Type | Description                                                  |
| ------------- | ---------- | ------------------------------------------------------------ |
| deviceId      | String     | device ID                                                    |
| deviceName    | String     | device name                                                  |
| deviceType    | String     | device type. *Robot Vacuum Cleaner K10+ Pro Combo*           |
| hubDeviceId   | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| workingStatus | String     | the working status of the device. *StandBy*, *Clearing*, *Paused*, *GotoChargeBase*, *Charging*, *ChargeDone*, *Dormant*, *InTrouble*, *InRemoteControl*, or *InDustCollecting* |
| onlineStatus  | String     | the connection status of the device. *online* or *offline*   |
| battery       | Integer    | the current battery level `0-100`                            |
| taskType      | String     | the current task in progress. *standBy*, *explore*, *cleanAll*, *cleanArea*, *cleanRoom*, *backToCharge*, *collectDust*, *remoteControl*, *cleanWithExplorer* |


##### Floor Cleaning Robot S10

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Robot Vacuum Cleaner S10*                  |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| workingStatus    | String     | the working status of the device. *StandBy*, *Clearing*, *Paused*, *GotoChargeBase*, *Charging*, *ChargeDone*, *Dormant*, *InTrouble*, *InRemoteControl*, or *InDustCollecting* |
| onlineStatus    | String     | the connection status of the device. *online* or *offline* |
| battery                | Integer    |  the current battery level `0-100` |
| waterBaseBattery | Integer | the current battery level `0-100` |
| taskType | String | the current task in progress. *standBy*, *explore*, *cleanAll*, *cleanArea*, *cleanRoom*, *fillWater*, *deepWashing*, *backToCharge*, *markingWaterBase*, *drying*, *collectDust*, *remoteControl*, *cleanWithExplorer*, *fillWaterForHumi*, *markingHumi* |

##### Floor Cleaning Robot S20

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceName         | String     | device name                                                  |
| deviceType         | String     | device type. *Robot Vacuum Cleaner S20*                  |
| hubDeviceId        | String     | device's parent Hub ID. *000000000000* when the device itself is a Hub or it is connected through Wi-Fi. |
| workingStatus    | String     | the working status of the device. *StandBy*, *Clearing*, *Paused*, *GotoChargeBase*, *Charging*, *ChargeDone*, *Dormant*, *InTrouble*, *InRemoteControl*, or *InDustCollecting* |
| onlineStatus    | String     | the connection status of the device. *online* or *offline* |
| battery                | Integer    |  the current battery level `0-100` |
| waterBaseBattery | Integer | the current battery level `0-100` |
| taskType | String | the current task in progress. *standBy*, *explore*, *cleanAll*, *cleanArea*, *cleanRoom*, *fillWater*, *deepWashing*, *backToCharge*, *markingWaterBase*, *drying*, *collectDust*, *remoteControl*, *cleanWithExplorer*, *fillWaterForHumi*, *markingHumi* |

##### Humidifier

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Humidifier*                                    |
| power                  | String     | ON/OFF state                                                 |
| humidity               | Integer    | humidity percentage                                          |
| temperature            | Float      | temperature in celsius                                       |
| nebulizationEfficiency | Integer    | atomization efficiency percentage |
| auto                   | Boolean    | determines if a Humidifier is in Auto Mode or not            |
| childLock              | Boolean    | determines if a Humidifier's safety lock is on or not        |
| sound                  | Boolean    | determines if a Humidifier is muted or not                   |
| lackWater | Boolean | determines if the water tank is empty or not |

##### Evaporative Humidifier

| Key           | Value Type | Description                                                  |
| ------------- | ---------- | ------------------------------------------------------------ |
| deviceId      | String     | device ID                                                    |
| deviceType    | String     | device type. *Humidifier2*                                   |
| power         | String     | ON/OFF state                                                 |
| humidity      | Integer    | humidity percentage                                          |
| mode          | Integer    | the current mode. `1`, level 4; `2`, level 3; `3`, level 2; `4`, level 1; `5`, humidity mode; `6`, sleep mode; `7`, auto mode; `8`, drying mode |
| drying        | Boolean    | determines if the device is drying its filter or not         |
| childLock     | Boolean    | determines if the safety lock is on or not                   |
| filterElement | Object     | contains status info of the filter. e.g. {"effectiveUsageHours": 240, "usedHours": 20}. `effectiveUsageHours`, the effective duration of the filter in hours; `usedHours`, the number of hours the filter has been used. |
| version       | Integer    | firmware version                                             |

##### Evaporative Humidifier (Auto-refill)

| Key           | Value Type | Description                                                  |
| ------------- | ---------- | ------------------------------------------------------------ |
| deviceId      | String     | device ID                                                    |
| deviceType    | String     | device type. *Humidifier2*                                   |
| power         | String     | ON/OFF state                                                 |
| humidity      | Integer    | humidity percentage                                          |
| mode          | Integer    | the current mode. `1`, level 4; `2`, level 3; `3`, level 2; `4`, level 1; `5`, humidity mode; `6`, sleep mode; `7`, auto mode; `8`, drying mode |
| drying        | Boolean    | determines if the device is drying its filter or not         |
| childLock     | Boolean    | determines if the safety lock is on or not                   |
| filterElement | Object     | contains status info of the filter. e.g. {"effectiveUsageHours": 240, "usedHours": 20}. `effectiveUsageHours`, the effective duration of the filter in hours; `usedHours`, the number of hours the filter has been used. |
| version       | Integer    | firmware version                                             |

##### Air Purifier VOC
| Key         | Value Type | Description                                                  |
| ----------- | ---------- | ------------------------------------------------------------ |
| deviceId    | String     | device ID                                                    |
| deviceType  | String     | device type. *Air Purifier VOC*                              |
| power       | String     | current state; `ON`, on; `OFF`, off                          |
| version     | String     | the current firmware version, e.g. V4.2                      |
| hubDeviceId | String     | returns `null` if not a bluetooth device                     |
| mode        | Integter   | the current mode. `1`, normal or fan mode; `2`, auto mode; `3`, sleep mode; `4`, pet mode |
| childLock   | Integter   | child lock. `0`, disabled; `1`, enabled                      |

##### Air Purifier Table VOC

| Key         | Value Type | Description                                                  |
| ----------- | ---------- | ------------------------------------------------------------ |
| deviceId    | String     | device ID                                                    |
| deviceType  | String     | device type. *Air Purifier Table VOC*                        |
| power       | String     | current state; `ON`, on; `OFF`, off                          |
| version     | String     | the current firmware version, e.g. V4.2                      |
| hubDeviceId | String     | returns `null` if not a bluetooth device                     |
| mode        | Integter   | the current mode. `1`, normal or fan mode; `2`, auto mode; `3`, sleep mode; `4`, pet mode |
| childLock   | Integter   | child lock. `0`, disabled; `1`, enabled                      |

##### Air Purifier PM2.5

| Key         | Value Type | Description                                                  |
| ----------- | ---------- | ------------------------------------------------------------ |
| deviceId    | String     | device ID                                                    |
| deviceType  | String     | device type. *Air Purifier PM2.5*                            |
| power       | String     | current state; `ON`, on; `OFF`, off                          |
| version     | String     | the current firmware version, e.g. V4.2                      |
| hubDeviceId | String     | returns `null` if not a bluetooth device                     |
| mode        | Integter   | the current mode. `1`, normal or fan mode; `2`, auto mode; `3`, sleep mode; `4`, pet mode |
| childLock   | Integter   | child lock. `0`, disabled; `1`, enabled                      |

##### Air Purifier Table PM2.5

| Key         | Value Type | Description                                                  |
| ----------- | ---------- | ------------------------------------------------------------ |
| deviceId    | String     | device ID                                                    |
| deviceType  | String     | device type. *Air Purifier Table PM2.5*                      |
| power       | String     | current state; `ON`, on; `OFF`, off                          |
| version     | String     | the current firmware version, e.g. V4.2                      |
| hubDeviceId | String     | returns `null` if not a bluetooth device                     |
| mode        | Integter   | the current mode. `1`, normal or fan mode; `2`, auto mode; `3`, sleep mode; `4`, pet mode |
| childLock   | Integter   | child lock. `0`, disabled; `1`, enabled                      |

##### Blind Tilt

| Key           | Value Type | Description                                                  |
| ------------- | ---------- | ------------------------------------------------------------ |
| deviceId      | String     | device ID                                                    |
| deviceType    | String     | device type. *Blind Tilt*                                    |
| hubDeviceId   | String     | device's parent Hub ID                                       |
| version       | Integer    | the firmware version of the device                                    |
| calibrate     | Boolean    | determines if the open and the closed positions have been properly calibrated or not |
| group         | Boolean    | determines if a Blind Tilt device is paired with or grouped with one or more devices of the same type or not |
| moving        | Boolean    | determines if the device is moving or not                    |
| direction     | String     | the opening direction of a Blind Tilt device                 |
| slidePosition | Integer    | the current position, 0-100                                  |

##### Roller Shade
| Key           | Value Type | Description                                                  |
| ------------- | ---------- | ------------------------------------------------------------ |
| deviceId      | String     | device ID                                                    |
| deviceType    | String     | device type. *Roller Shade*                                  |
| hubDeviceId   | String     | device's parent Hub ID                                       |
| version       | String     | the current firmware version, e.g. V4.2                      |
| calibrate     | Boolean    | determines if the open and the closed positions have been properly calibrated or not |
| battery       | Integer    | the current battery level `0-100`                            |
| moving        | Boolean    | determines if the device is moving or not                    |
| slidePosition | Integer    | the current position, `0-100`                                |

##### Hub 2

| Key         | Value Type | Description                             |
| ----------- | ---------- | --------------------------------------- |
| deviceId    | String     | device ID                               |
| deviceType  | String     | device type. *Hub 2*                    |
| hubDeviceId | String     | Hub ID, equivalent to device ID |
| temperature | Float      | temperature in celsius                  |
| lightLevel | Integer      | the level of illuminance of the ambience light, 1~20 |
| version     | String     | the current firmware version, e.g. V4.2 |
| humidity    | Integer    | humidity percentage                     |

##### Hub 3

| Key         | Value Type | Description                             |
| ----------- | ---------- | --------------------------------------- |
| deviceId    | String     | device ID                               |
| deviceType  | String     | device type. *Hub 3*                    |
| hubDeviceId | String     | Hub ID, equivalent to device ID |
| version     | String     | the current firmware version, e.g. V4.2 |
| temperature | Float      | temperature in celsius                  |
| lightLevel | Integer      | the level of illuminance of the ambience light, 1~10 |
| humidity    | Integer    | humidity percentage                     |
| moveDetected           | Boolean    | determines if motion is detected |
| online  | String     | the connection status of the device. *online* or *offline* |

##### Battery Circulator Fan
| Key                 | Value Type      | Description                                                  |
| ------------------- | --------------- | ------------------------------------------------------------ |
| deviceId            | String          | device ID                                                    |
| deviceName          | String          | device name                                                  |
| deviceType          | String          | device type. *Battery Circulator Fan*                                    |
| mode     | String     |fan mode. direct mode: *direct*; natural mode: "natural"; sleep mode: "sleep"; ultra quiet mode: "baby" |
| version     | String     | the current firmware version, e.g. V4.2 |
| battery                | Integer    |  the current battery level                                            |
| power                  | String     | ON/OFF state                                                 |
| nightStatus                | String    |  set nightlight status. turn off: *off*; mode 1: *1*; mode 2: *2*  |
| oscillation | String | set horizontal oscillation. turn on: *on*; turn off: *off* |
| verticalOscillation | String | set vertical oscillation. turn on: *on*; turn off: *off* |
| chargingStatus | String | battery charge status. *charging* or *uncharged* |
| fanSpeed | Integer | fan speed. 1~100 |

##### Circulator Fan
| Key                 | Value Type      | Description                                                  |
| ------------------- | --------------- | ------------------------------------------------------------ |
| deviceId            | String          | device ID                                                    |
| deviceName          | String          | device name                                                  |
| deviceType          | String          | device type. *Circulator Fan*                                    |
| mode     | String     |fan mode. direct mode: *direct*; natural mode: "natural"; sleep mode: "sleep"; ultra quiet mode: "baby" |
| version     | String     | the current firmware version, e.g. V4.2 |
| power                  | String     | ON/OFF state                                                 |
| nightStatus                | String    |  set nightlight status. turn off: *off*; mode 1: *1*; mode 2: *2*  |
| oscillation | String | set horizontal oscillation. turn on: *on*; turn off: *off* |
| verticalOscillation | String | set vertical oscillation. turn on: *on*; turn off: *off* |
| fanSpeed | Integer | fan speed. 1~100 |

##### Relay Switch 1PM

| Key             | Value Type | Description                                               |
| --------------- | ---------- | --------------------------------------------------------- |
| deviceId        | String     | device ID                                                 |
| deviceType      | String     | device type. *Relay Switch 1PM*                           |
| switchStatus    | Integer    | the current switch state. `0`, off; `1`, on               |
| voltage         | Float      | the current voltage, measured in Volt                     |
| version         | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |
| power           | Float      | the current power, measured in Watts                      |
| usedElectricity | Integer    | daily power consumption, measured in watt-minutes         |
| electricCurrent | Integer    | the electrical current measured in mA                     |

##### Relay Switch 1

| Key             | Value Type | Description                                               |
| --------------- | ---------- | --------------------------------------------------------- |
| deviceId        | String     | device ID                                                 |
| deviceType      | String     | device type. *Relay Switch 1*                             |
| switchStatus    | Integer    | the current switch state. `0`, off; `1`, on               |
| version         | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |

##### Relay Switch 2PM

| Key             | Value Type | Description                                               |
| --------------- | ---------- | --------------------------------------------------------- |
| deviceId        | String     | device ID                                                 |
| deviceType      | String     | device type. *Relay Switch 2PM*                           |
| online    | Boolean     | the connection status of the device. *true* or *false* |
| switch1Status    | Integer    | the current switch1 state. `0`, off; `1`, on               |
| switch2Status    | Integer    | the current switch2 state. `0`, off; `1`, on               |
| switch1voltage         | Integer    | the switch1 current voltage, measured in Volt                     |
| switch2voltage         | Integer    | the switch2 current voltage, measured in Volt                     |
| version         | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |
| switch1power           | Integer    | the switch1 current power, measured in Watts                      |
| switch2power           | Integer    | the switch2 current power, measured in Watts                      |
| switch1usedElectricity | Integer    | switch1 daily power consumption, measured in watt-minutes         |
| switch2usedElectricity | Integer    | switch2 daily power consumption, measured in watt-minutes         |
| switch1electricCurrent | Integer    | the switch1 electrical current measured in mA                     |
| switch2electricCurrent | Integer    | the switch2 electrical current measured in mA                     |
| calibrate     | Boolean      | determines if the open and the closed positions have been properly calibrated or not |
| position      | Integer     | the current position, 0-100                               |
| isStuck       | String       | determine if the roller blind is stuck                               |


##### Garage Door Opener

| Key             | Value Type | Description                                               |
| --------------- | ---------- | --------------------------------------------------------- |
| deviceId        | String     | device ID                                                 |
| deviceType      | String     | device type. *Garage Door Opener*                         |
| doorStatus      | Integer    | the current switch state. `0`, on; `1`, off                          |
| online    | Boolean     | the connection status of the device. *true* or *false* |
| version         | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |

##### Floor Lamp

| Key             | Value Type | Description                                               |
| --------------- | ---------- | --------------------------------------------------------- |
| deviceId        | String     | device ID                                                 |
| deviceType      | String     | device type. *Floor Lamp*                           |
| online    | Boolean     | the connection status of the device. *true* or *false* |
| hubDeviceId        | String     | device's parent Hub ID                                       |
| version         | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |
| power                  | String     | ON/OFF state                                                 |
| brightness             | Integer    | the brightness value, range from 1 to 100                    |
| color                  | String     |  the color value, RGB "255:255:255"                           |
| colorTemperature | Integer | the color temperature value, range from 2700 to 6500 |

##### Strip Light 3

| Key             | Value Type | Description                                               |
| --------------- | ---------- | --------------------------------------------------------- |
| deviceId        | String     | device ID                                                 |
| online    | Boolean     | the connection status of the device. *true* or *false* |
| deviceType      | String     | device type. *LED Strip Light 3*                           |
| hubDeviceId        | String     | device's parent Hub ID                                       |
| version         | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |
| power                  | String     | ON/OFF state                                                 |
| brightness             | Integer    | the brightness value, range from 1 to 100                    |
| color                  | String     |  the color value, RGB "255:255:255"                           |
| colorTemperature | Integer | the color temperature value, range from 2700 to 6500 |

##### Lock Lite

| Key             | Value Type | Description                                               |
| --------------- | ---------- | --------------------------------------------------------- |
| deviceId        | String     | device ID                                                 |
| deviceType      | String     | device type. *Lock Lite*                           |
| hubDeviceId        | String     | device's parent Hub ID                                       |
| battery                | Integer    |  the current battery level                                            |
| version         | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |
| lockState              | String     | determines if locked or not, *jammed*, *unlock* or *lock* |
| calibrate     | Boolean      | determines if the open and the closed positions have been properly calibrated or not |

##### Lock Ultra
| Key                | Value Type      | Description                                                  |
| ------------------ | --------------- | ------------------------------------------------------------ |
| deviceId           | String          | device ID                                                    |
| deviceType         | String          | device type. *Lock Ultra*                                |
| hubDeviceId        | String          | device's parent Hub ID                                       |
| battery              | Integer | the current battery level, 0-100 |
| version              | String     | the current firmware version, e.g. V4.2 |
| lockState              | String     | determines if locked or not, *jammed*, *unlock* or *lock* |
| doorState              | String     | determines if the door is closed or not, *open* or *close* |
| calibrate          | Boolean         | determines if Lock has been calibrated or not |

##### Video Doorbell

| Key             | Value Type | Description                                               |
| --------------- | ---------- | --------------------------------------------------------- |
| deviceId        | String     | device ID                                                 |
| deviceType      | String     | device type. *Video Doorbell*                           |
| hubDeviceId        | String     | device's parent Hub ID                                       |
| version         | String     | the current BLE and Wi-Fi firmware version, e.g. V3.1-6.3 |
| battery                | Integer    |  the current battery level                                            |
| online     | Boolean     | the connection status of the device. *true* or *false* |

##### K20+ Pro

| Key             | Value Type | Description                                               |
| --------------- | ---------- | --------------------------------------------------------- |
| deviceId        | String     | device ID                                                 |
| deviceType      | String     | device type. *Robot Vacuum Cleaner K20 Plus Pro*                           |
| hubDeviceId        | String     | device's parent Hub ID                                       |
| workingStatus    | String     | the working status of the device. *StandBy*, *Clearing*, *Paused*, *GotoChargeBase*, *Charging*, *ChargeDone*, *Dormant*, *InTrouble*, *InRemoteControl*, or *InDustCollecting* |
| onlineStatus    | String     | the connection status of the device. *online* or *offline* |
| battery                | Integer    |  the current battery level `0-100` |
| taskType | String | the current task in progress. *standBy*, *explore*, *cleanAll*, *cleanArea*, *cleanRoom*, *backToCharge*, *collectDust*, *remoteControl*, *cleanWithExplorer*|

##### Keypad Vision

| Key                | Value Type | Description                                                  |
| ------------------ | ---------- | ------------------------------------------------------------ |
| deviceId           | String     | device ID                                                    |
| deviceType         | String     | device type. *Keypad Vision*                                        |
| hubDeviceId        | String     | device's parent Hub ID                                       |

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
| deviceType | commandType | Command     | command parameter                          | Description                                                  |
| ---------- | ----------- | ----------- | ------------------------------------------ | ------------------------------------------------------------ |
| Curtain    | command     | setPosition | index0,mode0,position0<br />e.g. `0,ff,80` | mode: 0 (Performance Mode), 1 (Silent Mode), ff (default mode) <br />position: 0~100 (0 means open, 100 means closed) |
| Curtain    | command     | turnOff     | default                                    | equivalent to set position to 100                            |
| Curtain    | command     | turnOn      | default                                    | equivalent to set position to 0                              |
| Curtain    | command     | pause       | default                                    | set to PAUSE state                                           |

##### Curtain 3
| deviceType | commandType | Command     | command parameter                          | Description                                                  |
| ---------- | ----------- | ----------- | ------------------------------------------ | ------------------------------------------------------------ |
| Curtain 3  | command     | setPosition | index0,mode0,position0<br />e.g. `0,ff,80` | mode: 0 (Performance Mode), 1 (Silent Mode), ff (default mode) <br />position: 0~100 (0 means open, 100 means closed) |
| Curtain 3  | command     | turnOff     | default                                    | equivalent to set position to 100                            |
| Curtain 3  | command     | turnOn      | default                                    | equivalent to set position to 0                              |
| Curtain 3  | command     | pause       | default                                    | set to PAUSE state                                           |

##### Lock
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Lock                         | command     | lock                | default                                                      | rotate to locked position                                    |
| Lock                         | command     | unlock              | default                                                      | rotate to unlocked position                                  |

##### Lock Pro
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

##### Evaporative Humidifier
| deviceType  | commandType | Command      | command parameter                                  | Description                                                  |
| ----------- | ----------- | ------------ | -------------------------------------------------- | ------------------------------------------------------------ |
| Humidifier2 | command     | turnOff      | default                                            | set to OFF state                                             |
| Humidifier2 | command     | turnOn       | default                                            | set to ON state                                              |
| Humidifier2 | command     | setMode      | {"mode": mode_int, "targetHumidify": humidity_int} | set the mode. `mode_int`, `1`, level 4; `2`, level 3; `3`, level 2; `4`, level 1; `5`, humidity mode; `6`, sleep mode; `7`, auto mode; `8`, drying mode; `targetHumidify`, the target humidity level in percentage, `0~100`. |
| Humidifier2 | command     | setChildLock | `true` or `false`                                  | enable or disable child lock. `true`, enable; `false`, disable |

##### Evaporative Humidifier (Auto-refill)
| deviceType  | commandType | Command      | command parameter                                  | Description                                                  |
| ----------- | ----------- | ------------ | -------------------------------------------------- | ------------------------------------------------------------ |
| Humidifier2 | command     | turnOff      | default                                            | set to OFF state                                             |
| Humidifier2 | command     | turnOn       | default                                            | set to ON state                                              |
| Humidifier2 | command     | setMode      | {"mode": mode_int, "targetHumidify": humidity_int} | set the mode. `mode_int`, `1`, level 4; `2`, level 3; `3`, level 2; `4`, level 1; `5`, humidity mode; `6`, sleep mode; `7`, auto mode; `8`, drying mode; `targetHumidify`, the target humidity level in percentage, `0~100`. |
| Humidifier2 | command     | setChildLock | `true` or `false`                                  | enable or disable child lock. `true`, enable; `false`, disable |

##### Air Purifier VOC
| deviceType       | commandType | Command      | command parameter                            | Description                                                  |
| ---------------- | ----------- | ------------ | -------------------------------------------- | ------------------------------------------------------------ |
| Air Purifier VOC | command     | turnOff      | default                                      | set to OFF state                                             |
| Air Purifier VOC | command     | turnOn       | default                                      | set to ON state                                              |
| Air Purifier VOC | command     | setMode      | {"mode": mode_int, "fanGear": fan_level_int} | set the mode. `mode_int`,  `1`, normal or fan mode; `2`, auto mode; `3`, sleep mode; `4`, pet mode; `fan_level_int`, the fan level can only be set if `mode_int` is set to `1`, `1~3` |
| Air Purifier VOC | command     | setChildLock | `0` or `1`                                   | enable or disable child lock. `1`, enable; `0`, disable      |

##### Air Purifier Table VOC
| deviceType             | commandType | Command      | command parameter                            | Description                                                  |
| ---------------------- | ----------- | ------------ | -------------------------------------------- | ------------------------------------------------------------ |
| Air Purifier Table VOC | command     | turnOff      | default                                      | set to OFF state                                             |
| Air Purifier Table VOC | command     | turnOn       | default                                      | set to ON state                                              |
| Air Purifier Table VOC | command     | setMode      | {"mode": mode_int, "fanGear": fan_level_int} | set the mode. `mode_int`,  `1`, normal or fan mode; `2`, auto mode; `3`, sleep mode; `4`, pet mode; `fan_level_int`, the fan level can only be set if `mode_int` is set to `1`, `1~3` |
| Air Purifier Table VOC | command     | setChildLock | `0` or `1`                                   | enable or disable child lock. `1`, enable; `0`, disable      |

##### Air Purifier PM2.5
| deviceType         | commandType | Command      | command parameter                            | Description                                                  |
| ------------------ | ----------- | ------------ | -------------------------------------------- | ------------------------------------------------------------ |
| Air Purifier PM2.5 | command     | turnOff      | default                                      | set to OFF state                                             |
| Air Purifier PM2.5 | command     | turnOn       | default                                      | set to ON state                                              |
| Air Purifier PM2.5 | command     | setMode      | {"mode": mode_int, "fanGear": fan_level_int} | set the mode. `mode_int`,  `1`, normal or fan mode; `2`, auto mode; `3`, sleep mode; `4`, pet mode; `fan_level_int`, the fan level can only be set if `mode_int` is set to `1`, `1~3` |
| Air Purifier PM2.5 | command     | setChildLock | `0` or `1`                                   | enable or disable child lock. `1`, enable; `0`, disable      |

##### Air Purifier Table PM2.5
| deviceType               | commandType | Command      | command parameter                            | Description                                                  |
| ------------------------ | ----------- | ------------ | -------------------------------------------- | ------------------------------------------------------------ |
| Air Purifier Table PM2.5 | command     | turnOff      | default                                      | set to OFF state                                             |
| Air Purifier Table PM2.5 | command     | turnOn       | default                                      | set to ON state                                              |
| Air Purifier Table PM2.5 | command     | setMode      | {"mode": mode_int, "fanGear": fan_level_int} | set the mode. `mode_int`,  `1`, normal or fan mode; `2`, auto mode; `3`, sleep mode; `4`, pet mode; `fan_level_int`, the fan level can only be set if `mode_int` is set to `1`, `1~3` |
| Air Purifier Table PM2.5 | command     | setChildLock | `0` or `1`                                   | enable or disable child lock. `1`, enable; `0`, disable      |

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

##### Relay Switch 1PM
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Relay Switch 1PM | command     | turnOn              | default                                                      | set to ON state                                              |
| Relay Switch 1PM | command     | turnOff             | default                                                      | set to OFF state                                             |
| Relay Switch 1PM | command     | toggle              | default                                                      | toggle state                                                 |
| Relay Switch 1PM | command | setMode | `0~3` | set the switch mode. `0`, toggle mode; `1`, edge switch mode; `2`, detached switch mode; `3`, momentary switch mode |

##### Relay Switch 1
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Relay Switch 1 | command     | turnOn              | default                                                      | set to ON state                                              |
| Relay Switch 1 | command     | turnOff             | default                                                      | set to OFF state                                             |
| Relay Switch 1 | command     | toggle              | default                                                      | toggle state                                                 |
| Relay Switch 1 | command | setMode | `0~3` | set the switch mode. `0`, toggle mode; `1`, edge switch mode; `2`, detached switch mode; `3`, momentary switch mode |

##### Relay Switch 2PM
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Relay Switch 2PM | command     | turnOn              | “1”or"2"                                                      | set to ON state 1 represents channel 1 2 represents channel 2                                             |
| Relay Switch 2PM | command     | turnOff             | default                                                      | set to OFF state                                             |
| Relay Switch 2PM | command     | toggle              | “1”or"2"                                                    | toggle 1 represents channel 1 2 represents channel 2state                                                 |
| Relay Switch 2PM | command | setMode | “1”/“2”，`0~3` | The first item represents the switching of channel number, 1 represents channel number 1 and 2 represents channel number 2. The second item represents set the switch mode. `0`, toggle mode; `1`, edge switch mode; `2`, detached switch mode; `3`, momentary switch mode |
| Relay Switch 2PM | command | setPosition | `0~100` | Set roller blind opening and closing percentage. `0`, Open All; `100`, Close All  |

##### Garage Door Opener
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Garage Door Opener | command     | turnOn              | default                                                      | set to ON state                                              |
| Garage Door Opener | command     | turnOff             | default                                                      | set to OFF state                                             |

##### Floor Lamp
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Floor Lamp | command     | turnOn              | default                                                      | set to ON state                                              |
| Floor Lamp | command     | turnOff             | default                                                      | set to OFF state                                             |
| Floor Lamp | command     | toggle              | default                                                      | toggle state                                                 |
| Floor Lamp               | command     | setBrightness       | `{0-100}`                                                    | set brightness                                               |
| Floor Lamp | command     | setColor            | `"{0-255}:{0-255}:{0-255}"`                                  | set RGB color value  
| Floor Lamp | command     | setColorTemperature | `{2700-6500}`                                                | set color temperature   

##### Strip Light 3
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Strip Light 3 | command     | turnOn              | default                                                      | set to ON state                                              |
| Strip Light 3 | command     | turnOff             | default                                                      | set to OFF state                                             |
| Strip Light 3 | command     | toggle              | default                                                      | toggle state                                                 |
| Strip Light 3  | command     | setBrightness       | `{1-100}`                                                    | set brightness                                               |
| Strip Light 3  | command     | setColor            | `"{0-255}:{0-255}:{0-255}"`                                  | set RGB color value  |
| Strip Light 3  | command     | setColorTemperature | `{2700-6500}`                                                | set color temperature                                        |

##### Lock Lite
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Lock Lite                       | command     | lock                | default                                                      | rotate to locked position                                    |
| Lock Lite                     | command     | unlock              | default                                                      | rotate to unlocked position   

##### Lock Ultra
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Lock Ultra                     | command     | lock                | default                                                      | rotate to locked position                                    |
| Lock Ultra                    | command      | unlock              | default                                                      | rotate to unlocked position   

##### Video Doorbell
| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Video Doorbell | command     | enableMotionDetection              | default                                                      | Set to enabled state                                              |
| Video Doorbell | command     | disableMotionDetection              | default                                                     | Set to disabled state                                                 |

##### Keypad Vision

The control commands for this product work differently than the other products. Due to security concerns, the passcodes are stored locally. This mechanism dramatically prolongs the time needed to successfully create a passcode and get the correct result through the Web API. Hence, the actual results of the following commands are returned from the SwitchBot server asynchronously and are delivered through a webhook. 

You need to configure a webhook to receive the correct result. Refer to this product's webhook definition.

| deviceType                   | commandType | Command             | command parameter                                            | Description                                                  |
| ---------------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Keypad Vision | command     | createKey | { "name": passcode _name_str, "type": passcode_type_str, "password": passcode_str, "startTime": valid_from_long, "endTime": valid_to_long } | create a new passcode |
| Keypad Vision | command     | deleteKey | { "id": passcode_id_int }  | delete an existing passcode |

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

##### Mini Robot Vacuum K10+

| deviceType | commandType | Command  | command parameter | Description                                                  |
| ---------- | ----------- | -------- | ----------------- | ------------------------------------------------------------ |
| K10+       | command     | start    | default           | start vacuuming                                              |
| K10+       | command     | stop     | default           | stop vacuuming                                               |
| K10+       | command     | dock     | default           | return to charging dock                                      |
| K10+       | command     | PowLevel | `{0-3}`           | set suction power level: 0 (Quiet), 1 (Standard), 2 (Strong), 3 (MAX) |

##### Mini Robot Vacuum K10+ Pro

| deviceType | commandType | Command  | command parameter | Description                                                  |
| ---------- | ----------- | -------- | ----------------- | ------------------------------------------------------------ |
| K10+ Pro   | command     | start    | default           | start vacuuming                                              |
| K10+ Pro   | command     | stop     | default           | stop vacuuming                                               |
| K10+ Pro   | command     | dock     | default           | return to charging dock                                      |
| K10+ Pro   | command     | PowLevel | `{0-3}`           | set suction power level: 0 (Quiet), 1 (Standard), 2 (Strong), 3 (MAX) |

##### K20+ Pro

| deviceType | commandType | Command  | command parameter | Description                                                  |
| ---------- | ----------- | -------- | ----------------- | ------------------------------------------------------------ |
| K20+ Pro | command     | startClean  | {"action": action_str, "param": {"fanLevel": fan_level_int, "times": clean_cycle_int}} | start cleaning. <br />`action_str`, the cleaning mode, *sweep* or *mop*.<br />`fanLevel`, the vacuum level, `1-4`.<br />`times`, the number of cycles, `1-2639999`, in theory. |
| K20+ Pro | command     | pause       | default                                                      | pause cleaning                                               |
| K20+ Pro | command     | dock        | default                                                      | return to charging dock                                      |
| K20+ Pro | command     | setVolume   | `{0-100}`                                                    | set the robot volume                                         |
| K20+ Pro | command     | changeParam | {"fanLevel": fan_level_int, "waterLevel": water_level_int, "times": clean_cycle_int} | change clean parameters. `fan_level_int`, the vacuum level, `1-4`; `water_level_int`, the mop moisture level, `1-2`; `times`, the number of cycles, `1-2639999`, in theory. |

##### K10+ Pro Combo

| deviceType                          | commandType | Command     | command parameter                                            | Description                                                  |
| ----------------------------------- | ----------- | ----------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Robot Vacuum Cleaner K10+ Pro Combo | command     | startClean  | {"action": action_str, "param": {"fanLevel": fan_level_int, "times": clean_cycle_int}} | start cleaning. <br />`action_str`, the cleaning mode, *sweep* or *mop*.<br />`fanLevel`, the vacuum level, `1-4`.<br />`times`, the number of cycles, `1-2639999`, in theory. |
| Robot Vacuum Cleaner K10+ Pro Combo | command     | pause       | default                                                      | pause cleaning                                               |
| Robot Vacuum Cleaner K10+ Pro Combo | command     | dock        | default                                                      | return to charging dock                                      |
| Robot Vacuum Cleaner K10+ Pro Combo | command     | setVolume   | `{0-100}`                                                    | set the robot volume                                         |
| Robot Vacuum Cleaner K10+ Pro Combo | command     | changeParam | {"fanLevel": fan_level_int, "times": clean_cycle_int} | change clean parameters. `fan_level_int`, the vacuum level, `1-4`; `times`, the number of cycles, `1-2639999`, in theory. |


##### Floor Cleaning Robot S10

| deviceType               | commandType | Command         | command parameter                                            | Description                                                  |
| ------------------------ | ----------- | --------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Floor Cleaning Robot S10 | command     | startClean      | {"action": clean_mode_str, "param": {"fanLevel": fan_level_int, "waterLevel": water_level_int, "times": clean_cycle_int}} | start cleaning.<br />`action`, the cleaning mode, *sweep* or *sweep_mop*.<br />`fanLevel`, the vacuum level, `1-4`.<br />`waterLevel`, the mop moisture level, `1-2`.<br />`times`, the number of cycles, `1-2639999`, in theory. |
| Floor Cleaning Robot S10 | command     | addWaterForHumi | default                                                      | refill the mind blowing Evaporative Humidifier (Auto-refill). |
| Floor Cleaning Robot S10 | command     | pause           | default                                                      | pause.                                                       |
| Floor Cleaning Robot S10 | command     | dock            | default                                                      | return to Auto-empty Station and charge.                     |
| Floor Cleaning Robot S10 | command     | setVolume       | `0-100`                                                      | set volume, `1-100`                                          |
| Floor Cleaning Robot S10 | command     | selfClean       | `1` or `2` or `3`                                            | mode `1`, wash the mop.<br />mode `2`, dry itself.<br /> mode `3`, terminate. |
| Floor Cleaning Robot S10 | command     | changeParam     | {"fanLevel": fan_level_int, "waterLevel": water_level_int, "times": clean_cycle_int} | `fanLevel`, the vacuum level, `1-4`.<br />`waterLevel`, the mop moisture level, `1-2`.<br />`times`, the number of cycles, `1-2639999`, in theory. |

##### S20

| deviceType | commandType | Command         | command parameter                                            | Description                                                  |
| ---------- | ----------- | --------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| S20        | command     | startClean      | {"action": clean_mode_str, "param": {"fanLevel": fan_level_int, "waterLevel": water_level_int, "times": clean_cycle_int}} | start cleaning.<br />`action`, the cleaning mode, *sweep* or *sweep_mop*.<br />`fanLevel`, the vacuum level, `1-4`.<br />`waterLevel`, the mop moisture level, `1-2`.<br />`times`, the number of cycles, `1-2639999`, in theory. |
| S20        | command     | addWaterForHumi | default                                                      | refill the mind blowing Evaporative Humidifier (Auto-refill). |
| S20        | command     | pause           | default                                                      | pause.                                                       |
| S20        | command     | dock            | default                                                      | return to Auto-empty Station and charge.                     |
| S20        | command     | setVolume       | `0-100`                                                      | set volume, `1-100`                                          |
| S20        | command     | selfClean       | `1` or `2` or `3`                                            | mode `1`, wash the mop.<br />mode `2`, dry itself.<br /> mode `3`, terminate. |
| S20        | command     | changeParam     | {"fanLevel": fan_level_int, "waterLevel": water_level_int, "times": clean_cycle_int} | `fanLevel`, the vacuum level, `1-4`.<br />`waterLevel`, the mop moisture level, `1-2`.<br />`times`, the number of cycles, `1-2639999`, in theory. |

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

##### Blind Tilt

| deviceType | commandType | Command     | command parameter                    | Description                                                  |
| ---------- | ----------- | ----------- | ------------------------------------ | ------------------------------------------------------------ |
| Blind Tilt | command     | setPosition | direction;position<br />e.g. `up;60` | direction: up/down<br />position: 0~100 (0 means closed, 100 means open, it MUST be set to a multiple of 2. e.g. `up;48` or `up; 36`) |
| Blind Tilt | command     | fullyOpen   | default                              | Set the position of Blind Tilt to open, equivalent to setting the position to `up;100` or `down;100` |
| Blind Tilt | command     | closeUp     | default                              | Set the position of Blind Tilt to closed up, equivalent to setting the position to `up;0` |
| Blind Tilt | command     | closeDown   | default                              | Set the position of Blind Tilt to closed down, equivalent to setting the position to `down;0` |

##### Roller Shade

| deviceType   | commandType | Command     | command parameter | Description                                                  |
| ------------ | ----------- | ----------- | ----------------- | ------------------------------------------------------------ |
| Roller Shade | command     | setPosition | `0~100`           | `0`, open; `100`, closed                                     |

##### Battery Circulator Fan

| deviceType             | commandType | Command           | command parameter                       | Description                                                  |
| ---------------------- | ----------- | ----------------- | --------------------------------------- | ------------------------------------------------------------ |
| Battery Circulator Fan | command     | turnOff           | default                                 | Set to OFF state                                             |
| Battery Circulator Fan | command     | turnOn            | default                                 | Set to ON state                                              |
| Battery Circulator Fan | command     | setNightLightMode | `off`, `1`, or `2`                      | `off`, turn off nightlight,<br />`1`, bright <br />`2`, dim  |
| Battery Circulator Fan | command     | setWindMode       | `direct`, `natural`, `sleep`, or `baby` | Set fan mode. `direct`: direct mode. `natural`:  natural mode. `sleep`: sleep mode. `baby`: ultra quiet mode |
| Battery Circulator Fan | command     | setWindSpeed      | `{1-100}` e.g. `10`                     | Set fan speed.1~100                                          |

##### Circulator Fan

| deviceType     | commandType | Command           | command parameter                       | Description                                                  |
| -------------- | ----------- | ----------------- | --------------------------------------- | ------------------------------------------------------------ |
| Circulator Fan | command     | turnOff           | default                                 | Set to OFF state                                             |
| Circulator Fan | command     | turnOn            | default                                 | Set to ON state                                              |
| Circulator Fan | command     | setNightLightMode | `off`, `1`, or `2`                      | `off`, turn off nightlight,<br />`1`, bright <br />`2`, dim  |
| Circulator Fan | command     | setWindMode       | `direct`, `natural`, `sleep`, or `baby` | Set fan mode. `direct`: direct mode. `natural`:  natural mode. `sleep`: sleep mode. `baby`: ultra quiet mode |
| Circulator Fan | command     | setWindSpeed      | `{1-100}` e.g. `10`                     | Set fan speed.1~100                                          |

#### Command set for virtual infrared remote devices

The table below describes all the available commands for virtual infrared remote devices,

| deviceType                             | commandType | Command                    | command parameter                                            | Description                                                  |
| -------------------------------------- | ----------- | -------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| All home appliance types except Others | command     | turnOn                     | default                                                      | every home appliance can be turned on by default             |
| All home appliance types except Others | command     | turnOff                    | default                                                      | every home appliance can be turned off by default            |
| Others                                 | `customize` | {user-defined button name} | default                                                      | all user-defined buttons must be configured with commandType=customize |
| Air Conditioner                        | command     | setAll                     | {temperature},{mode},{fan speed},{power state}<br />e.g. `26,1,3,on` | the unit of temperature is in celsius; <br />modes include 0/1 (auto), 2 (cool), 3 (dry), 4 (fan), 5 (heat); <br />fan speed includes 1 (auto), 2 (low), 3 (medium), 4 (high); <br />power state includes on and off |
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
lig
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

##### Floor Cleaning Robot S10 example
Clean with vacuum mode

Request

```http
POST https://api.switch-bot.com/v1.1/devices/F7538E1ABC23/commands
```

```js
{
    "commandType": "command",
    "command": "startClean", // start cleaning
    "parameter": {
        "action": "sweep", // clean with vacuum mode
        "param": {
            "fanLevel": 1, // vacuum level set to 1
            "waterLevel": 1, // mop moisture level set to 1
            "times": 1 // number of cyclyes to clean set to 1
        }
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

Change the cleaning settings

Request

```http
POST https://api.switch-bot.com/v1.1/devices/F7538E1ABC23/commands
```

```js
{
    "commandType": "command",
    "command": "changeParam",
    "parameter": {
      	"fanLevel": 2, // vacuum level set to 1
        "waterLevel": 1, // mop moisture level set to 1
        "times": 1 // number of times to clean set to 2
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
POST https://api.switch-bot.com/v1.1/webhook/updateWebhook
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
| WoHand    | Bot   |
| WoCurtain | Curtain |
| WoPresence    | Motion Sensor   |
| WoContact     | Contact Sensor  |
| WoLock        | Lock            |
| WoLockPro | Lock Pro |
| WoCamera      | Indoor Cam      |
| WoPanTiltCam  | Pan/Tilt Cam    |
| WoBulb        | Color Bulb      |
| WoStrip       | LED Strip Light |
| WoPlugUS      | Plug Mini (US)  |
| WoPlugJP      | Plug Mini (JP)  |
| WoMeter       | Meter           |
| WoMeterPlus   | Meter Plus      |
| WoIOSensor | Outdoor Meter |
| WoSweeper | Robot Vacuum Cleaner S1 |
| WoSweeperPlus | Robot Vacuum Cleaner S1 Plus |
| WoCeiling | Ceiling Light |
| WoCeilingPro | Ceiling Light Pro |
| WoKeypad      | Keypad |
| WoKeypadTouch | Keypad Touch |
| WoHub2 | Hub 2 |
| WoHub3 | Hub 3 |
| Robot Vacuum Cleaner S10 | Floor Cleaning Robot S10 |
| Water Detector | Water Leak Detector |
| MeterPro | Meter Pro |
| MeterPro(CO2) | Meter Pro CO2 Monitor |
| WoFan2 | Battery Circulator Fan or Circulator Fan |
| Humidifier2 | Evaporative Humidifier or Evaporative Humidifier (Auto-refill) |
| Robot Vacuum Cleaner K10+ Pro Combo | K10+ Pro Combo |
| Air Purifier VOC | Air Purifier VOC |
| Air Purifier Table VOC | Air Purifier Table VOC |
| Air Purifier PM2.5 | Air Purifier PM2.5 |
| Air Purifier Table PM2.5 | Air Purifier Table PM2.5 |
| WoRollerShade | Roller Shade |
| Relay Switch 1PM | Relay Switch 1PM |
| Relay Switch 1 | Relay Switch 1 |
| Relay Switch 2PM | Relay Switch 2PM |
| Garage Door Opener | Garage Door Opener |
| Floor Lamp | Floor Lamp |
| Lock Lite | Lock Lite |
| Video Doorbell | Video Doorbell |
| Keypad Vision | Keypad Vision |
| Lock Ultra | Lock Ultra |
| Strip Light 3 | Strip Light 3 |
| K20+ Pro | K20+ Pro |

#### Bot
| Key Name       | Value Type | Description                                                  |
| -------------- | ---------- | ------------------------------------------------------------ |
| eventType      | String     | the type of events                                           |
| eventVersion   | String     | the current event version                                    |
| context        | Object     | the detail info of the event                                 |
| deviceType     | String     | the type of the device                                       |
| deviceMac      | String     | the MAC address of the device                                |
| power | String     | the current state of the device. This state is only valid for Switch Mode, where "on" stands for on and "off" stands for off. It will return "on" or "off" in Press Mode or Customize Mode, but the returned value can be neglected. |
| timeOfSample   | Long       | the time stamp when the event is sent                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoHand",
        "deviceMac": DEVICE_MAC_ADDR,
        "power": "on",//"on"or"off"
        "battery": 10,
        "deviceMode": "pressMode",//pressMode,switchMode,customizeMode
        "timeOfSample": 123456789
    }
}
```

#### Curtain
| Key Name       | Value Type | Description                                                  |
| -------------- | ---------- | ------------------------------------------------------------ |
| eventType      | String     | the type of events                                           |
| eventVersion   | String     | the current event version                                    |
| context        | Object     | the detail info of the event                                 |
| deviceType     | String     | the type of the device                                       |
| deviceMac      | String     | the MAC address of the device                                |
| calibrate          | Boolean         | determines if the open position and the close position of a device have been properly calibrated or not |
| group              | Boolean         | determines if a Curtain is paired with or grouped with another Curtain or not |
| slidePosition             | Integer         | the percentage of the distance between the calibrated open position and closed position that Curtain has traversed |
| battery      | Integer          | the battery level of a Curtain                           |
| timeOfSample   | Long       | the time stamp when the event is sent                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoCurtain",
        "deviceMac": DEVICE_MAC_ADDR,
        "calibrate":false,
        "group":false,
        "slidePosition":50, //0~100
        "battery":100,
        "timeOfSample": 123456789
    }
}
```

#### Curtain 3
| Key Name       | Value Type | Description                                                  |
| -------------- | ---------- | ------------------------------------------------------------ |
| eventType      | String     | the type of events                                           |
| eventVersion   | String     | the current event version                                    |
| context        | Object     | the detail info of the event                                 |
| deviceType     | String     | the type of the device                                       |
| deviceMac      | String     | the MAC address of the device                                |
| calibrate          | Boolean         | determines if the open position and the close position of a device have been properly calibrated or not |
| group              | Boolean         | determines if a Curtain is paired with or grouped with another Curtain or not |
| slidePosition             | Integer         | the percentage of the distance between the calibrated open position and closed position that Curtain has traversed |
| battery      | Integer          | the battery level of a Curtain                           |
| timeOfSample   | Long       | the time stamp when the event is sent                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoCurtain3",
        "deviceMac": DEVICE_MAC_ADDR,
        "calibrate":false,
        "group":false,
        "slidePosition":50, //0~100
        "battery":100,
        "timeOfSample": 123456789
    }
}
```

#### Motion Sensor

| Key Name       | Value Type | Description                                                  |
| -------------- | ---------- | ------------------------------------------------------------ |
| eventType      | String     | the type of events                                           |
| eventVersion   | String     | the current event version                                    |
| context        | Object     | the detail info of the event                                 |
| deviceType     | String     | the type of the device                                       |
| deviceMac      | String     | the MAC address of the device                                |
| detectionState | String     | the motion state of the device, "DETECTED" stands for motion is detected; "NOT_DETECTED" stands for motion has not been detected for some time |
| battery        | Integer    | the current battery level, `0-100`                           |
| timeOfSample   | Long       | the time stamp when the event is sent                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoPresence",
        "deviceMac": DEVICE_MAC_ADDR,
        "detectionState": "NOT_DETECTED",
        "battery":100,
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
| battery        | Integer    | the current battery level, `0-100`                           |
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
        "battery":100,
        "timeOfSample": 123456789
    }
}
```

#### Water Leak Detector

| Key Name     | Value Type | Description                                |
| ------------ | ---------- | ------------------------------------------ |
| eventType    | String     | the type of events                         |
| eventVersion | String     | the current event version                  |
| context      | Object     | the detail info of the event               |
| deviceType   | String     | the type of the device                     |
| deviceMac    | String     | the MAC address of the device |
| detectionState | Integer | `0`, dry. `1`, leak detected |
| battery              | Integer | the current battery level, `0-100` |
| timeOfSample | Long       | the time stamp when the event is sent      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Water Detector",
        "deviceMac": DEVICE_MAC_ADDR,
        "detectionState": 0,
        "battery":100,
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
| battery      | Integer    | the current battery level, `0-100`         |
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
        "battery":100,
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
| battery      | Integer    | the current battery level, `0-100`         |
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
        "battery":100,
        "timeOfSample": 123456789
    }
}
```

#### Outdoor Meter

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
| battery      | Integer    | the current battery level, `0-100`         |
| timeOfSample | Long       | the time stamp when the event is sent      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoIOSensor",
        "deviceMac": DEVICE_MAC_ADDR,
        "temperature": 22.5,
        "scale": "CELSIUS",
        "humidity": 31,
        "battery":100,
        "timeOfSample": 123456789
    }
}
```

#### Meter Pro

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
| battery      | Integer    | the current battery level, `0-100`         |
| timeOfSample | Long       | the time stamp when the event is sent      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "MeterPro",
        "deviceMac": DEVICE_MAC_ADDR,
        "temperature": 22.5,
        "scale": "CELSIUS",
        "humidity": 31,
        "battery":100,
        "timeOfSample": 123456789
    }
}
```

#### Meter Pro CO2

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
| CO2          | Integer    | CO2 ppm value, 0-9999                      |
| battery      | Integer    | the current battery level, `0-100`         |
| timeOfSample | Long       | the time stamp when the event is sent      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "MeterPro(CO2)",
        "deviceMac": DEVICE_MAC_ADDR,
        "temperature": 22.5,
        "scale": "CELSIUS",
        "humidity": 31,
        "CO2": 1203,
        "battery":100,
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
| battery      | Integer    | the current battery level, `0-100`                           |
| timeOfSample | Long       | the time stamp when the event is sent                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoLock",
        "deviceMac": DEVICE_MAC_ADDR,
        "lockState": "LOCKED",
        "battery":100,
        "timeOfSample": 123456789
    }
}
```

#### Lock Pro

| Key Name     | Value Type | Description                                                  |
| ------------ | ---------- | ------------------------------------------------------------ |
| eventType    | String     | the type of events                                           |
| eventVersion | String     | the current event version                                    |
| context      | Object     | the detail info of the event                                 |
| deviceType   | String     | the type of the device                                       |
| deviceMac    | String     | the MAC address of the device                                |
| lockState    | String     | the state of the device, "LOCKED" stands for the motor is rotated to locking position; "UNLOCKED" stands for the motor is rotated to unlocking position; "JAMMED" stands for the motor is jammed while rotating |
| battery      | Integer    | the current battery level, `0-100`                           |
| timeOfSample | Long       | the time stamp when the event is sent                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoLockPro",
        "deviceMac": DEVICE_MAC_ADDR,
        "lockState": "LOCKED",
        "battery":100,
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

#### Mini Robot Vacuum K10+
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
        "deviceType": "WoSweeperMini",
        "deviceMac": DEVICE_MAC_ADDR,
        "workingStatus"："StandBy",
        "onlineStatus": "online",
        "battery": 100,
        "timeOfSample": 123456789
    }
}
```

#### Mini Robot Vacuum K10+ Pro
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
        "deviceType": "WoSweeperMiniPro",
        "deviceMac": DEVICE_MAC_ADDR,
        "workingStatus"："StandBy",
        "onlineStatus": "online",
        "battery": 100,
        "timeOfSample": 123456789
    }
}
```

#### K10+ Pro Combo
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
| taskType | String | attributes of the context object. the current task in progress. *standBy*, *explore*, *cleanAll*, *cleanArea*, *cleanRoom*, *backToCharge*, *collectDust*, *remoteControl*, *cleanWithExplorer* |
| timeOfSample    | Long | attributes of the context object. the time stamp when the event is sent |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Robot Vacuum Cleaner K10+ Pro Combo",
        "deviceMac": DEVICE_MAC_ADDR,
        "workingStatus"："StandBy",
        "onlineStatus": "online",
        "battery": 100,
        "taskType": "explore",
        "timeOfSample": 123456789
    }
}
```

#### Floor Cleaning Robot S10
| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| eventType    | String     | the type of events                                   |
| eventVersion | String     | the current event version                            |
| context      | Object     | the detail info of the event                         |
| deviceType   | String     | attributes of the context object. the type of the device |
| deviceMac    | String     | attributes of the context object. the MAC address of the device |
| workingStatus    | String     | attributes of the context object. the working status of the device. *StandBy*, *Clearing*, *Paused*, *GotoChargeBase*, *Charging*, *ChargeDone*, *Dormant*, *InTrouble*, *InRemoteControl*, or *InDustCollecting* |
| onlineStatus    | String     | attributes of the context object. the connection status of the device. *online* or *offline* |
| battery | Integer | attributes of the context object. the battery level, `0-100` |
| waterBaseBattery | Integer | the current battery level `0-100` |
| taskType | String | the current task in progress. *standBy*, *explore*, *cleanAll*, *cleanArea*, *cleanRoom*, *fillWater*, *deepWashing*, *backToCharge*, *markingWaterBase*, *drying*, *collectDust*, *remoteControl*, *cleanWithExplorer*, *fillWaterForHumi*, *markingHumi* |
| timeOfSample    | Long | attributes of the context object. the time stamp when the event is sent |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Robot Vacuum Cleaner S10",
        "deviceMac": DEVICE_MAC_ADDR,
        "workingStatus"："StandBy",
        "onlineStatus": "online",
        "battery": 100,// 0-100
        "waterBaseBattery": 100,
        "taskType": "explore",
        "timeOfSample": 123456789
    }
}
```

#### S20
| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| eventType    | String     | the type of events                                   |
| eventVersion | String     | the current event version                            |
| context      | Object     | the detail info of the event                         |
| deviceType   | String     | attributes of the context object. the type of the device |
| deviceMac    | String     | attributes of the context object. the MAC address of the device |
| workingStatus    | String     | attributes of the context object. the working status of the device. *StandBy*, *Clearing*, *Paused*, *GotoChargeBase*, *Charging*, *ChargeDone*, *Dormant*, *InTrouble*, *InRemoteControl*, or *InDustCollecting* |
| onlineStatus    | String     | attributes of the context object. the connection status of the device. *online* or *offline* |
| battery | Integer | attributes of the context object. the battery level, `0-100` |
| waterBaseBattery | Integer | the current battery level `0-100` |
| taskType | String | the current task in progress. *standBy*, *explore*, *cleanAll*, *cleanArea*, *cleanRoom*, *fillWater*, *deepWashing*, *backToCharge*, *markingWaterBase*, *drying*, *collectDust*, *remoteControl*, *cleanWithExplorer*, *fillWaterForHumi*, *markingHumi* |
| timeOfSample    | Long | attributes of the context object. the time stamp when the event is sent |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Robot Vacuum Cleaner s20",
        "deviceMac": DEVICE_MAC_ADDR,
        "workingStatus"："StandBy",
        "onlineStatus": "online",
        "battery": 100,// 0-100
        "waterBaseBattery": 100,
        "taskType": "explore",
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

#### Hub 2
| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| eventType    | String     | the type of events                                   |
| eventVersion | String     | the current event version                            |
| context      | Object     | the detail info of the event                         |
| deviceType   | String     | attributes of the context object. the type of the device |
| deviceMac    | String     | attributes of the context object. the MAC address of the device |
| temperature  | Float      | the current temperature reading            |
| humidity     | Integer    | the current humidity reading in percentage |
| lightLevel  | Integer      | the level of illuminance of the ambience light, 1~20            |
| scale        | String     | the current temperature unit being used    |
| timeOfSample    | Long | attributes of the context object. the time stamp when the event is sent |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoHub2",
        "deviceMac": DEVICE_MAC_ADDR,
        "temperature":13,
        "humidity":18,
        "lightLevel": 19,
        "scale": "CELSIUS",
        "timeOfSample": 123456789
    }
}
```

#### Hub 3
| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| eventType    | String     | the type of events                                   |
| eventVersion | String     | the current event version                            |
| context      | Object     | the detail info of the event                         |
| detectionState | String     | the motion state of the device, "DETECTED" stands for motion is detected; "NOT_DETECTED" stands for motion has not been detected for some time |
| deviceMac    | String     | attributes of the context object. the MAC address of the device |
| deviceType   | String     | attributes of the context object. the type of the device |
| humidity     | Integer    | the current humidity reading in percentage |
| lightLevel  | Integer      | the level of illuminance of the ambience light, 1~10            |
| scale        | String     | the current temperature unit being used    |
| temperature  | Float      | the current temperature reading            |
| timeOfSample    | Long | attributes of the context object. the time stamp when the event is sent |

```js
{
  "eventType": "changeReport",
  "eventVersion": "1",
  "context": {
    "detectionState": "DETECTED",
    "deviceMac": "B0E9FE582974",
    "deviceType": "Hub 3",
    "humidity": 45,
    "lightLevel": 10,
    "scale": "CELSIUS",
    "temperature": 30.3,
    "timeOfSample": 1742807095763
  }
}
```

#### Battery Circulator Fan

| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| eventType    | String     | the type of events                                   |
| eventVersion | String     | the current event version                            |
| context      | Object     | the detail info of the event                         |
| deviceType   | String     | the type of the device                               |
| deviceMac    | String     | the MAC address of the device                        |
| mode                | String  | fan mode. direct mode: *direct*; natural mode: "natural"; sleep mode: "sleep"; ultra quiet mode: "baby" |
| version             | String  | the current firmware version, e.g. V4.2                      |
| battery             | Integer | the current battery level                                    |
| powerState     | String  | ON/OFF state                                                 |
| nightStatus         | Integer | set nightlight status. turn off: *off*; mode 1: *1*; mode 2: *2* |
| oscillation         | String  | set horizontal oscillation. turn on: *on*; turn off: *off*   |
| verticalOscillation | String  | set vertical oscillation. turn on: *on*; turn off: *off*     |
| chargingStatus      | String  | battery charge status. *charging* or *uncharged*             |
| fanSpeed            | Integer | fan speed. 1~100                                             |
| timeOfSample | Long       | the time stamp when the event is sent                |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoFan2",
        "deviceMac": DEVICE_MAC_ADDR,
        "mode": "direct",
        "version": "V3.1",
        "battery": 22,
        "powerState": "ON",
        "nightStatus": "off",
        "oscillation": "on",
        "verticalOscillation": "on",
        "chargingStatus": "charging",
        "fanSpeed": 3,
        "timeOfSample": 123456789
    }
}
```

#### Circulator Fan

| Key Name     | Value Type | Description                                          |
| ------------ | ---------- | ---------------------------------------------------- |
| eventType    | String     | the type of events                                   |
| eventVersion | String     | the current event version                            |
| context      | Object     | the detail info of the event                         |
| deviceType   | String     | the type of the device                               |
| deviceMac    | String     | the MAC address of the device                        |
| mode                | String  | fan mode. direct mode: *direct*; natural mode: "natural"; sleep mode: "sleep"; ultra quiet mode: "baby" |
| version             | String  | the current firmware version, e.g. V4.2                      |
| powerState     | String  | ON/OFF state                                                 |
| nightStatus         | Integer | set nightlight status. turn off: *off*; mode 1: *1*; mode 2: *2* |
| oscillation         | String  | set horizontal oscillation. turn on: *on*; turn off: *off*   |
| verticalOscillation | String  | set vertical oscillation. turn on: *on*; turn off: *off*     |
| fanSpeed            | Integer | fan speed. 1~100                                             |
| timeOfSample | Long       | the time stamp when the event is sent                |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoFan2",
        "deviceMac": DEVICE_MAC_ADDR,
        "mode": "direct",
        "version": "V3.1",
        "powerState": "ON",
        "nightStatus": "off",
        "oscillation": "on",
        "verticalOscillation": "on",
        "fanSpeed": 3,
        "timeOfSample": 123456789
    }
}
```

#### Evaporative Humidifier

| Key Name     | Value Type | Description                                |
| ------------ | ---------- | ------------------------------------------ |
| eventType    | String     | the type of events                         |
| eventVersion | String     | the current event version                  |
| context      | Object     | the detail info of the event               |
| deviceType   | String     | the type of the device                     |
| deviceMac    | String     | the MAC address of the device |
| power | String | the power state of the device |
| mode | Integer | the current mode. `1`, level 4; `2`, level 3; `3`, level 2; `4`, level 1; `5`, humidity mode; `6`, sleep mode; `7`, auto mode; `8`, drying mode |
| drying  | Boolean | determines if the device is drying its filter or not |
| timeOfSample | Long       | the time stamp when the event is sent      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Humidifier2",
        "deviceMac": DEVICE_MAC_ADDR,
        "power": "on",
        "mode": 1,
        "drying": false,
        "timeOfSample": 123456789
    }
}
```

#### Evaporative Humidifier (Auto-refill)

| Key Name     | Value Type | Description                                |
| ------------ | ---------- | ------------------------------------------ |
| eventType    | String     | the type of events                         |
| eventVersion | String     | the current event version                  |
| context      | Object     | the detail info of the event               |
| deviceType   | String     | the type of the device                     |
| deviceMac    | String     | the MAC address of the device |
| power | String | the power state of the device |
| mode | Integer | the current mode. `1`, level 4; `2`, level 3; `3`, level 2; `4`, level 1; `5`, humidity mode; `6`, sleep mode; `7`, auto mode; `8`, drying mode |
| drying  | Boolean | determines if the device is drying its filter or not |
| timeOfSample | Long       | the time stamp when the event is sent      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Humidifier2",
        "deviceMac": DEVICE_MAC_ADDR,
        "power": "on",
        "mode": 1,
        "drying": false,
        "timeOfSample": 123456789
    }
}
```

#### Air Purifier VOC

| Key Name     | Value Type | Description                                |
| ------------ | ---------- | ------------------------------------------ |
| eventType    | String     | the type of events                         |
| eventVersion | String     | the current event version                  |
| context      | Object     | the detail info of the event               |
| deviceType   | String     | the type of the device                     |
| deviceMac    | String     | the MAC address of the device |
| power | String | the power state of the device |
| mode | Integer | the current mode. `1`, normal or fan mode; `2`, auto mode; `3`, sleep mode; `4`, pet mode |
| childLock | Integer | child lock. `0`, disabled; `1`, enabled |
| timeOfSample | Long       | the time stamp when the event is sent      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Air Purifier VOC",
        "deviceMac": DEVICE_MAC_ADDR,
        "power": "ON",
        "mode": 4,
        "childLock": 0,
        "timeOfSample": 123456789
    }
}
```

#### Air Purifier Table VOC

| Key Name     | Value Type | Description                                |
| ------------ | ---------- | ------------------------------------------ |
| eventType    | String     | the type of events                         |
| eventVersion | String     | the current event version                  |
| context      | Object     | the detail info of the event               |
| deviceType   | String     | the type of the device                     |
| deviceMac    | String     | the MAC address of the device |
| power | String | the power state of the device |
| mode | Integer | the current mode. `1`, normal or fan mode; `2`, auto mode; `3`, sleep mode; `4`, pet mode |
| childLock | Integer | child lock. `0`, disabled; `1`, enabled |
| timeOfSample | Long       | the time stamp when the event is sent      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Air Purifier Table VOC",
        "deviceMac": DEVICE_MAC_ADDR,
        "power": "ON",
        "mode": 4,
        "childLock": 0,
        "timeOfSample": 123456789
    }
}
```

#### Air Purifier PM2.5

| Key Name     | Value Type | Description                                |
| ------------ | ---------- | ------------------------------------------ |
| eventType    | String     | the type of events                         |
| eventVersion | String     | the current event version                  |
| context      | Object     | the detail info of the event               |
| deviceType   | String     | the type of the device                     |
| deviceMac    | String     | the MAC address of the device |
| power | String | the power state of the device |
| mode | Integer | the current mode. `1`, normal or fan mode; `2`, auto mode; `3`, sleep mode; `4`, pet mode |
| childLock | Integer | child lock. `0`, disabled; `1`, enabled |
| timeOfSample | Long       | the time stamp when the event is sent      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Air Purifier PM2.5",
        "deviceMac": DEVICE_MAC_ADDR,
        "power": "ON",
        "mode": 4,
        "childLock": 0,
        "timeOfSample": 123456789
    }
}
```

#### Air Purifier Table PM2.5

| Key Name     | Value Type | Description                                |
| ------------ | ---------- | ------------------------------------------ |
| eventType    | String     | the type of events                         |
| eventVersion | String     | the current event version                  |
| context      | Object     | the detail info of the event               |
| deviceType   | String     | the type of the device                     |
| deviceMac    | String     | the MAC address of the device |
| power | String | the power state of the device |
| mode | Integer | the current mode. `1`, normal or fan mode; `2`, auto mode; `3`, sleep mode; `4`, pet mode |
| childLock | Integer | child lock. `0`, disabled; `1`, enabled |
| timeOfSample | Long       | the time stamp when the event is sent      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Air Purifier Table PM2.5",
        "deviceMac": DEVICE_MAC_ADDR,
        "power": "ON",
        "mode": 4,
        "childLock": 0,
        "timeOfSample": 123456789
    }
}
```

#### Roller Shade
| Key Name       | Value Type | Description                                                  |
| -------------- | ---------- | ------------------------------------------------------------ |
| eventType      | String     | the type of events                                           |
| eventVersion   | String     | the current event version                                    |
| context        | Object     | the detail info of the event                                 |
| deviceType     | String     | the type of the device                                       |
| deviceMac      | String     | the MAC address of the device                                |
| calibrate          | Boolean         | determines if the open position and the close position of a device have been properly calibrated or not |
| slidePosition             | Integer         | the percentage of the distance between the calibrated open position and closed position that the device has traversed |
| battery      | Integer          | the battery level                           |
| timeOfSample   | Long       | the time stamp when the event is sent                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoRollerShade",
        "deviceMac": DEVICE_MAC_ADDR,
        "calibrate":false,
        "slidePosition":50, //0~100
        "battery":100,
        "timeOfSample": 123456789
    }
}
```

#### Relay Switch 1PM

| Key Name        | Value Type | Description                                                  |
| --------------- | ---------- | ------------------------------------------------------------ |
| eventType       | String     | the type of events                                           |
| eventVersion    | String     | the current event version                                    |
| context         | Object     | the detail info of the event                                 |
| deviceType      | String     | the type of the device                                       |
| deviceMac       | String     | the MAC address of the device                                |
| online          | Boolean    | determines if the device is connected to the internet or disconnected |
| switchStatus    | Integer    | the switch state of the device. `1`, on; `0`, off            |
| overload        | Boolean    | determines if the device is power overloaded or not          |
| overTemperature | Boolean    | determines if the working temperature is over 100 degree celcius or not |
| timeOfSample    | Long       | the time stamp when the event is sent                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Relay Switch 1PM",
        "deviceMac": DEVICE_MAC_ADDR,
        "online": false,
        "overTemperature": true,
        "overload": true,
        "switchStatus": 1,
        "timeOfSample": 123456789
    }
}
```

#### Relay Switch 1

| Key Name        | Value Type | Description                                                  |
| --------------- | ---------- | ------------------------------------------------------------ |
| eventType       | String     | the type of events                                           |
| eventVersion    | String     | the current event version                                    |
| context         | Object     | the detail info of the event                                 |
| deviceType      | String     | the type of the device                                       |
| deviceMac       | String     | the MAC address of the device                                |
| online          | Boolean    | determines if the device is connected to the internet or disconnected |
| switchStatus    | Integer    | the switch state of the device. `1`, on; `0`, off            |
| overTemperature | Boolean    | determines if the working temperature is over 100 degree celcius or not |
| timeOfSample    | Long       | the time stamp when the event is sent                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Relay Switch 1",
        "deviceMac": DEVICE_MAC_ADDR,
        "online": false,
        "overTemperature": true,
        "switchStatus": 1,
        "timeOfSample": 123456789
    }
}
```

#### Relay Switch 2PM

| Key Name        | Value Type | Description                                                  |
| --------------- | ---------- | ------------------------------------------------------------ |
| eventType       | String     | the type of events                                           |
| eventVersion    | String     | the current event version                                    |
| context         | Object     | the detail info of the event                                 |
| deviceType      | String     | the type of the device                                       |
| deviceMac       | String     | the MAC address of the device                                |
| online          | Boolean    | determines if the device is connected to the internet or disconnected |
| switchStatus    | Integer    | the switch state of the device. `1`, on; `0`, off            |
| overload        | Boolean    | determines if the device is power overloaded or not          |
| calibrate          | Boolean         | determines if the open position and the close position of a device have been properly calibrated or not |
| position          | Integer          | determine the percentage of the device that is open or closed |
| isStuck          | Boolean           | determine if the device is stuck |



```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Relay Switch 2PM",
        "deviceMac": "FFFFFFFFFFF",
        "online": false,
        "overTemperature": true,
        "switch1Status": 1,
        "switch2Status": 1,
        "switch1Overload": true,
        "switch2Overload": true,
        "calibrate": true,
        "position": 0,
        "isStuck": true
    }
}
```

#### Garage Door Opener

| Key Name        | Value Type | Description                                                  |
| --------------- | ---------- | ------------------------------------------------------------ |
| eventType       | String     | the type of events                                           |
| eventVersion    | String     | the current event version                                    |
| context         | Object     | the detail info of the event                                 |
| deviceType      | String     | the type of the device                                       |
| deviceMac       | String     | the MAC address of the device                                |
| doorStatus      | Integer     | he switch state of the device. `0`, on; `1`, off                               |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Garage Door Opener",
        "deviceMac": "FFFFFFFFFFF",
        "doorStatus": 1, 
    }
}
```

#### Floor Lamp

| Key Name        | Value Type | Description                                                  |
| --------------- | ---------- | ------------------------------------------------------------ |
| eventType       | String     | the type of events                                           |
| eventVersion    | String     | the current event version                                    |
| context         | Object     | the detail info of the event                                 |
| deviceType      | String     | the type of the device                                       |
| deviceMac       | String     | the MAC address of the device                                |
| powerState     | String  | ON/OFF state                                                 |
| brightness | Integer | attributes of the context object. the brightness value, range from 1 to 100 |
| colorTemperature | Integer | attributes of the context object. the color temperature value, range from 2700 to 6500 |
| color            | String     | the color value, in the format of RGB value, "255:255:255" |
| timeOfSample | Long       | the time stamp when the event is sent                |

```js
{
   "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Floor Lamp",
        "deviceMac": DEVICE_MAC_ADDR,
        "powerState": "ON",
        "brightness": 10,
        "color": "255:255:0",
        "colorTemperature": 3500,
        "timeOfSample": 123456789
    }
}
```

#### Lock Lite

| Key Name        | Value Type | Description                                                  |
| --------------- | ---------- | ------------------------------------------------------------ |
| eventType       | String     | the type of events                                           |
| eventVersion    | String     | the current event version                                    |
| context         | Object     | the detail info of the event                                 |
| deviceType      | String     | the type of the device                                       |
| deviceMac       | String     | the MAC address of the device                                |
| lockState       | String     | determines if locked or not |
| battery      | Integer          | the battery level                           |
| timeOfSample   | Long       | the time stamp when the event is sent                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoLockLite",
        "deviceMac": DEVICE_MAC_ADDR,
        "lockState": "LOCKED",
        "battery": 90,
        "timeOfSample": 123456789
    }
}
```

#### Video Doorbell

| Key Name        | Value Type | Description                                                  |
| --------------- | ---------- | ------------------------------------------------------------ |
| eventType       | String     | the type of events                                           |
| eventVersion    | String     | the current event version                                    |
| context         | Object     | the detail info of the event                                 |
| deviceType      | String     | the type of the device                                       |
| deviceMac       | String     | the MAC address of the device                                |
| battery      | Integer          | the battery level                           |
| detectionState | String     | the motion state of the device, "DETECTED" stands for motion is detected; "NOT_DETECTED" stands for motion has not been detected for some time |
| timeOfSample   | Long       | the time stamp when the event is sent                        |
| press   | Boolean      |the Doorbell button was pressed                      |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Video Doorbell",
        "deviceMac": DEVICE_MAC_ADDR,
        "battery": 80,
        "detectionState": "DETECTED",
        "press": true,
        "timeOfSample": 123456789
    }
}
```

#### Keypad Vision

| Key Name        | Value Type | Description                                                  |
| --------------- | ---------- | ------------------------------------------------------------ |
| eventType       | String     | the type of events                                           |
| eventVersion    | String     | the current event version                                    |
| context         | Object     | the detail info of the event                                 |
| deviceType      | String     | the type of the device                                       |
| deviceMac       | String     | the MAC address of the device                                |
| eventName    | String     | attributes of the context object. the name of the command being sent |
| commandId    | String     | attributes of the context object. the command id |
| result    | String     | attributes of the context object. the result of the command. *success*, *failed*, or *timeout*. timeout duration is 1 minute |
| timeOfSample   | Long       | the time stamp when the event is sent                        |

##### Create a passcode
```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "WoKeypadVision",
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
        "deviceType": "WoKeypadVision",
        "deviceMac": DEVICE_MAC_ADDR,
        "eventName": "deleteKey ",
        "commandId": "CMD-1663558451952-01",
        "result": "success",
        "timeOfSample": 123456789
    }
}
```

#### Lock Ultra

| Key Name        | Value Type | Description                                                  |
| --------------- | ---------- | ------------------------------------------------------------ |
| eventType       | String     | the type of events                                           |
| eventVersion    | String     | the current event version                                    |
| context         | Object     | the detail info of the event                                 |
| deviceType      | String     | the type of the device                                       |
| deviceMac       | String     | the MAC address of the device                                |
| lockState    | String     | the state of the device, "LOCKED" stands for the motor is rotated to locking position; "UNLOCKED" stands for the motor is rotated to unlocking position; "JAMMED" stands for the motor is jammed while rotating |
| battery      | Integer          | the battery level                           |
| timeOfSample   | Long       | the time stamp when the event is sent                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Smart Lock Ultra",
        "deviceMac": DEVICE_MAC_ADDR,
        "lockState": "LOCKED",
        "battery": 90,
        "timeOfSample": 123456789
    }
}
```

#### Strip Light 3

| Key Name        | Value Type | Description                                                  |
| --------------- | ---------- | ------------------------------------------------------------ |
| eventType       | String     | the type of events                                           |
| eventVersion    | String     | the current event version                                    |
| context         | Object     | the detail info of the event                                 |
| deviceType      | String     | the type of the device                                       |
| deviceMac       | String     | the MAC address of the device                                |
| powerState     | String  | ON/OFF state                                                 |
| colorTemperature | Integer | attributes of the context object. the color temperature value, range from 2700 to 6500 |
| color            | String     | the color value, in the format of RGB value, "255:255:255" |
| timeOfSample   | Long       | the time stamp when the event is sent                        |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Strip Light 3",
        "deviceMac": DEVICE_MAC_ADDR,
        "powerState": "ON",//"ON"or"OFF"
        "brightness": 10,
        "color": "255:255:0",
        "colorTemperature": 3500,
        "timeOfSample": 123456789
    }
}

```

#### K20+ Pro

| Key Name        | Value Type | Description                                                  |
| --------------- | ---------- | ------------------------------------------------------------ |
| eventType    | String     | the type of events                                   |
| eventVersion | String     | the current event version                            |
| context      | Object     | the detail info of the event                         |
| deviceType   | String     | attributes of the context object. the type of the device |
| deviceMac    | String     | attributes of the context object. the MAC address of the device |
| workingStatus    | String     | attributes of the context object. the working status of the device. *StandBy*, *Clearing*, *Paused*, *GotoChargeBase*, *Charging*, *ChargeDone*, *Dormant*, *InTrouble*, *InRemoteControl*, or *InDustCollecting* |
| onlineStatus    | String     | attributes of the context object. the connection status of the device. *online* or *offline* |
| battery | Integer | attributes of the context object. the battery level, range from 0 to 100 |
| taskType | String | attributes of the context object. the current task in progress. *standBy*, *explore*, *cleanAll*, *cleanArea*, *cleanRoom*, *backToCharge*, *collectDust*, *remoteControl*, *cleanWithExplorer* |
| timeOfSample    | Long | attributes of the context object. the time stamp when the event is sent |

```js
{
    "eventType": "changeReport",
    "eventVersion": "1",
    "context": {
        "deviceType": "Robot Vacuum Cleaner K20+ Pro",
        "deviceMac": DEVICE_MAC_ADDR,
        "workingStatus"："StandBy",
        //StandBy,Clearing,Paused,GotoChargeBase,Charging,ChargeDone,Dormant,InTrouble,InRemoteControl,InDustCollecting
        "onlineStatus": "online",//online,offline
        "battery": 100,// 0-100
        "taskType": "explore", // standBy,explore,cleanAll,cleanArea,cleanRoom,deepWashing,backToCharge,drying,collectDust,remoteControl,cleanWithExplorer
        "timeOfSample": 123456789
    }
}

```


----

* [SwitchBot (Official website)](https://www.switch-bot.com/)
* [Facebook @SwitchBotRobot](https://www.facebook.com/SwitchBotRobot/) 
* [Twitter @SwitchBot](https://twitter.com/switchbot) 
