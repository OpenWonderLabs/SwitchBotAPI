# SwitchBot API v1.1

- [SwitchBot API v1.1](#switchbot-api-v11)
  - [Introduction](#introduction)
  - [About the New Version](#about-the-new-version)
  - [Getting Started](#getting-started)
  - [Authentication](#authentication)
    - [Open Token and Secret Key](#open-token-and-secret-key)
    - [How to Sign?](#how-to-sign)
      - [Python 2 example code](#python-2-example-code)
      - [Python 3 example code](#python-3-example-code)
      - [JavaScript example code](#javascript-example-code)
      - [C# example code](#c-example-code)
      - [Java 11+ example code](#java-11-example-code)
      - [PHP example code](#php-example-code)
      - [Swift example code](#swift-example-code)
      - [Go example code](#go-example-code)
  - [Glossary](#glossary)
    - [`Legacy` Cloud Services](#legacy-cloud-services)
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
      - [Sample request](#sample-request)
    - [Get device status](#get-device-status)
      - [Description](#description-1)
      - [Path parameters](#path-parameters)
      - [Response structure](#response-structure)
      - [Response codes](#response-codes)
      - [Sample requests](#sample-requests)
        - [Get Meter status](#get-meter-status)
        - [Get Curtain status](#get-curtain-status)
    - [Send device control commands](#send-device-control-commands)
      - [Description](#description-2)
      - [Path parameters](#path-parameters-1)
      - [Request body parameters](#request-body-parameters)
      - [Response](#response)
      - [Error codes](#error-codes)
      - [Sample request](#sample-request-1)
        - [Control Floor Cleaning Robot S10](#control-floor-cleaning-robot-s10)
        - [Change the cleaning settings](#change-the-cleaning-settings)
        - [Keypad example](#keypad-example)
        - [Bot example](#bot-example)
        - [Infrared remote device example](#infrared-remote-device-example)
  - [Scenes](#scenes)
    - [Get scene list](#get-scene-list)
      - [Description](#description-3)
      - [Response structure](#response-structure-1)
      - [Response body schema](#response-body-schema)
      - [Error codes](#error-codes-1)
      - [Sample request](#sample-request-2)
    - [Execute manual scenes](#execute-manual-scenes)
      - [Description](#description-4)
      - [Path parameters](#path-parameters-2)
      - [Response structure](#response-structure-2)
      - [Error codes](#error-codes-2)
      - [Sample request](#sample-request-3)
  - [Webhook](#webhook)
    - [Configure webhook](#configure-webhook)
      - [Description](#description-5)
      - [Request body parameters](#request-body-parameters-1)
      - [Example request](#example-request)
      - [Response](#response-1)
    - [Query webhook configuration](#query-webhook-configuration)
      - [Description](#description-6)
      - [Request body parameters](#request-body-parameters-2)
      - [Request types](#request-types)
      - [Response examples](#response-examples)
    - [Update webhook configuration](#update-webhook-configuration)
      - [Description](#description-7)
      - [Request body parameters](#request-body-parameters-3)
      - [Example request](#example-request-1)
      - [Response](#response-2)
    - [Delete webhook](#delete-webhook)
      - [Description](#description-8)
      - [Request body parameters](#request-body-parameters-4)
      - [Example request](#example-request-2)
      - [Response](#response-3)
    - [Webhook event structure](#webhook-event-structure)
      - [Common webhook event properties](#common-webhook-event-properties)
      - [Bot event example](#bot-event-example)
      - [Curtain event example](#curtain-event-example)
  - [Device Specifications and Supported Features List](#device-specifications-and-supported-features-list)
    - [Hubs](#hubs)
    - [Locks \& Security](#locks--security)
    - [Curtains \& Blinds](#curtains--blinds)
    - [Sensors](#sensors)
    - [Lighting](#lighting)
    - [Robot Vacuum](#robot-vacuum)
    - [Climate Control](#climate-control)
    - [Plugs \& Switches](#plugs--switches)
    - [Cameras](#cameras)
    - [Others](#others)

## Introduction

This document describes a collection of SwitchBot API methods, examples, and best practices for, but not limited to, IoT hobbyists, developers, and gurus to make their own smart home programs or applications.

> Note: This API is limited to personal uses.
> It is prohibited for commercial uses or for large-scale applications. There is a daily call limit to all users to ensure resources are evenly distributed to each API user.
> For commercial uses, please do consult SwitchBot via this [form](https://share.hsforms.com/1aDMLLwl_QmSazZr8i3Gakgbx01q).

> 日本でご利用の皆さまへ:
> 弊社はAPIインターフェイスを通じて、より柔軟でパーソナルな利用体験を提供できることを願っております。
> すべてのユーザーの皆様の公平な利用とサービス品質を保証するため、APIの利用範囲についてご説明いたします。
> ①個人ユーザーの利用
> 弊社は、個人のプロジェクト、学習研究、および日常生活におけるクリエイティブなシーンでのAPI利用を歓迎し、奨励いたします。
> これらの目的で利用する場合は追加の申請なしにAPIを自由に呼び出すことができます。
> ➁商用利用
> SwitchBot APIを商業製品やサービスに統合する予定がある場合、または大規模な呼び出し（例：数千回以上のリクエスト）を行う場合は、まず弊社にご連絡ください、別途EnterpriseAPIをご用意しております。
> • 貴社の製品/サービスの動作がより安定します。
> • 専門的な技術サポートと割り当ての保証を提供できます。
> • 貴社の利用が弊社のサービス利用規約およびブランドガイドラインに準拠していることを確認できます。
> お問い合わせ方法
> 商用利用に関するご要望やご質問がございましたら、いつでもお気軽にお問い合わせください。 📧 メール：biz@switchbot.jp

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
const crypto = require("crypto");
const https = require("https");

const token = "yourToken";
const secret = "yourSecret";
const t = Date.now();
const nonce = "requestID";
const data = token + t + nonce;
const sign = crypto.createHmac("sha256", secret).update(data).digest("base64");
console.log(sign);

const body = JSON.stringify({
  command: "turnOn",
  parameter: "default",
  commandType: "command",
});
const deviceId = "MAC";
const options = {
  hostname: "api.switch-bot.com",
  port: 443,
  path: `/v1.1/devices/${deviceId}/commands`,
  method: "POST",
  headers: {
    Authorization: token,
    sign: sign,
    nonce: nonce,
    t: t,
    "Content-Type": "application/json",
    "Content-Length": body.length,
  },
};

const req = https.request(options, (res) => {
  console.log(`statusCode: ${res.statusCode}`);
  res.on("data", (d) => {
    process.stdout.write(d);
  });
});

req.on("error", (error) => {
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

#### Go example code

```go
package main

import (
    "crypto/hmac"
    "crypto/sha256"
    "encoding/base64"
    "fmt"
    "io"
    "log"
    "net/http"
    "strings"
    "time"
)

func main() {
    token := "XXXXXXXXXXXXXXXXXXX"      // copy and paste from the SwitchBot app V6.14 or later
    secret := "YYYYYYYYYYY"             // copy and paste from the SwitchBot app V6.14 or later
    nonce := UUID()                     // generate random UUID v4
    timestamp := time.Now().UnixMilli() // 13-digit milliseconds Unix timestamp

    data := fmt.Sprintf("%s%d%s", token, timestamp, nonce)

    mac := hmac.New(sha256.New, []byte(secret))
    if _, err := mac.Write([]byte(data)); err != nil {
        log.Fatalf("Error generating signature: %v", err)
    }

    signature := mac.Sum(nil)
    signatureB64 := strings.ToUpper(base64.StdEncoding.EncodeToString(signature))

    url := "https://api.switch-bot.com/v1.1/devices"
    req, err := http.NewRequest("GET", url, nil)
    if err != nil {
        log.Fatalf("Error creating request: %v", err)
    }

    req.Header.Set("Content-Type", "application/json")
    req.Header.Set("Authorization", token)
    req.Header.Set("sign", signatureB64)
    req.Header.Set("nonce", nonce)
    req.Header.Set("t", fmt.Sprintf("%d", timestamp))

    client := &http.Client{}
    resp, err := client.Do(req)
    if err != nil {
        log.Fatalf("Error sending request: %v", err)
    }
    defer resp.Body.Close()

    body, err := io.ReadAll(resp.Body)
    if err != nil {
        log.Fatalf("Error reading response: %v", err)
    }

    fmt.Println(string(body)) // Response in JSON format
}

// UUID returns an RFC 4122/9562–compliant random UUIDv4 string.
func UUID() string {
    var uuid [16]byte                 // 128-bit long array
    rand.Read(uuid[:])                // Use cryptographically secure random source
    uuid[6] = (uuid[6] & 0x0F) | 0x40 // Version (UUIDv4 = 0100)
    uuid[8] = (uuid[8] & 0x3F) | 0x80 // Variant (RFC9562 / RFC4122 = 10xxxxxx)

    return fmt.Sprintf("%08x-%04x-%04x-%04x-%012x",
        uuid[0:4],  // 4 bytes
        uuid[4:6],  // 2 bytes
        uuid[6:8],  // 2 bytes (version included)
        uuid[8:10], // 2 bytes (variant included)
        uuid[10:])  // 6 bytes
}
```

## Glossary

The following table provides definitions to the terms to be frequently mentioned in the subsequent sections.

| Term                                 | Description                                               | Model No.                          | Availability                      |
| ------------------------------------ | --------------------------------------------------------- | ---------------------------------- | --------------------------------- |
| Hub Mini                             | Short for SwitchBot Hub Mini                              | W0202200                           |                                   |
| Hub Plus                             | Short for SwitchBot Hub Plus                              | SwitchBot Hub S1                   |                                   |
| Hub 2                                | Short for SwitchBot Hub 2                                 | W3202100                           |                                   |
| Hub 3                                | Short for SwitchBot Hub 3                                 | W7202100                           |                                   |
| Bot                                  | Short for SwitchBot Bot                                   | SwitchBot S1                       |                                   |
| Curtain                              | Short for SwitchBot Curtain                               | W0701600                           |                                   |
| Curtain 3                            | Short for SwitchBot Curtain 3                             | W2400000                           |                                   |
| Plug                                 | Short for SwitchBot Plug                                  | SP11                               | Currently only available in Japan |
| Meter                                | Short for SwitchBot Thermometer and Hygrometer            | SwitchBot MeterTH S1               |                                   |
| Meter Plus (JP)                      | Short for SwitchBot Thermometer and Hygrometer Plus (JP). | W2201500                           | Only available in Japan           |
| Meter Plus (US)                      | Short for SwitchBot Thermometer and Hygrometer Plus (US)  | W2301500                           | Only available in US              |
| Outdoor Meter                        | Short for Indoor/Outdoor Thermo-Hygrometer                | W3400010                           |                                   |
| Weather Station                      | Short for SwitchBot Weather Station                       | W3400010                           |                                   |
| Meter Pro                            | Short for SwitchBot Meter Pro                             | W4900000                           |                                   |
| Meter Pro (CO2 Monitor)              | Short for SwitchBot Meter Pro (CO2 Monitor)               | W4900010                           |                                   |
| Motion Sensor                        | Short for SwitchBot Motion Sensor                         | W1101500                           |                                   |
| Contact Sensor                       | Short for SwitchBot Contact Sensor                        | W1201500                           |                                   |
| Prensence Sensor                     | Short for SwitchBot Prensence Sensor                      | W8200000                           |                                   |
| Water Leak Detector                  | Short for SwitchBot Water Leak Detector                   | W4402000                           |                                   |
| Color Bulb                           | Short for SwitchBot Color Bulb                            | W1401400                           |                                   |
| Strip Light                          | Short for SwitchBot LED Strip Light                       | W1701100                           |                                   |
| Plug Mini (US)                       | Short for SwitchBot Plug Mini (US)                        | W1901400 and W1901401              | Only available in US              |
| Plug Mini (JP)                       | Short for SwitchBot Plug Mini (JP)                        | W2001400 and W2001401              | Only available in Japan           |
| Plug Mini (EU)                       | Short for SwitchBot Plug Mini (EU)                        | W7732300                           | Only available in Europe          |
| Lock                                 | Short for SwitchBot Lock                                  | W1601700                           |                                   |
| Lock Pro                             | Short for SwitchBot Lock Pro                              | W3500000                           |                                   |
| Lock Pro Matter Enabled              | Short for SwitchBot Lock Pro Matter Enabled               | W8102000                           |                                   |
| Lock Vision                          | Short for SwitchBot Lock Vision                           | W1141000                           |                                   |
| Lock Vision Pro                      | Short for SwitchBot Lock Vision Pro                       | W1141001                           |                                   |
| Keypad                               | Short for SwitchBot Lock                                  | W2500010                           |                                   |
| Keypad Touch                         | Short for SwitchBot Lock                                  | W2500020                           |                                   |
| S1                                   | Short for SwitchBot Robot Vacuum Cleaner S1               | W3011000                           |                                   |
| S1 Plus                              | Short for SwitchBot Robot Vacuum Cleaner S1 Plus          | W3011010                           |                                   |
| K10+                                 | Short for SwitchBot Mini Robot Vacuum K10+                | W3011020                           |                                   |
| K10+ Pro                             | Short for SwitchBot Mini Robot Vacuum K10+ Pro            | W3011026                           |                                   |
| S10                                  | Short for SwitchBot Floor Cleaning Robot S10              | W3211800                           |                                   |
| S20                                  | Short for SwitchBot Floor Cleaning Robot S20              | W6602310                           |                                   |
| K10+ Pro Combo                       | Short for SwitchBot Robot Vacuum K10+ Pro Combo           | W3002500                           |                                   |
| K20+ Pro                             | Short for SwitchBot Multitasking Household Robot K20+ Pro | W3002520                           |                                   |
| K11+                                 | Short for Robot Vacuum K11+                               | W3003100                           |                                   |
| Ceiling Light                        | Short for SwitchBot Ceiling Light                         | W2612230 and W2612240              | Currently only available in Japan |
| Ceiling Light Pro                    | Short for SwitchBot Ceiling Light Pro                     | W2612210 and W2612220              | Currently only available in Japan |
| RGBICWW Strip Light                  | Short for SwitchBot RGBICWW Strip Light                   | W1702109                           |                                   |
| RGBICWW Floor Lamp                   | Short for SwitchBot RGBICWW Floor Lamp                    | W1702101                           |                                   |
| RGBIC Neon Rope Light                | Short for SwitchBot RGBIC Neon Rope Light                 | W1702107                           |                                   |
| RGBIC Neon Wire Rope Light           | Short for SwitchBot RGBIC Neon Wire Rope Light            | W1702108                           |                                   |
| Indoor Cam                           | Short for SwitchBot Indoor Cam                            | W1301200                           |                                   |
| Pan/Tilt Cam                         | Short for SwitchBot Pan/Tilt Cam                          | W1801200                           |                                   |
| Pan/Tilt Cam 2K                      | Short for SwitchBot Pan/Tilt Cam 2K                       | W3101100                           |                                   |
| Blind Tilt                           | Short for SwitchBot Blind Tilt                            | W2701600                           |                                   |
| Battery Circulator Fan               | Short for SwitchBot Battery Circulator Fan                | W3800510                           |                                   |
| Circulator Fan                       | Short for SwitchBot Circulator Fan                        | W3800511                           |                                   |
| Evaporative Humidifier               | Short for SwitchBot Evaporative Humidifier                | W3902300                           |                                   |
| Evaporative Humidifier (Auto-refill) | Short for SwitchBot Evaporative Humidifier (Auto-refill)  | W3902310                           |                                   |
| Air Purifier PM2.5                   | Short for SwitchBot Air Purifier                          | W5302300                           |                                   |
| Air Purifier Table PM2.5             | Short for SwitchBot Air Purifier Table                    | W5302310                           |                                   |
| Air Purifier VOC                     | Short for SwitchBot Air Purifier                          | W5302300                           | Currently only available in Japan |
| Air Purifier Table VOC               | Short for SwitchBot Air Purifier Table                    | W5302310                           | Currently only available in Japan |
| Roller Shade                         | Short for SwitchBot Roller Shade                          | W5000000                           |                                   |
| Relay Switch 1PM                     | Short for SwitchBot Relay Switch 1PM                      | W5502310                           |                                   |
| Relay Switch 1                       | Short for SwitchBot Relay Switch 1                        | W5502300                           |                                   |
| Relay Switch 2PM                     | Short for SwitchBot Relay Switch 2PM                      | W5502320                           |                                   |
| Garage Door Opener                   | Short for SwitchBot Garage Door Opener                    | W5502330                           |                                   |
| Floor Lamp                           | Short for SwitchBot RGBWW Floor Lamp                      | W1702100                           |                                   |
| Strip Light 3                        | Short for SwitchBot RGBWW Strip Light 3                   | W1702110                           |                                   |
| Lock Lite                            | Short for SwitchBot Lock Lite                             | W5110000                           |                                   |
| Video Doorbell                       | Short for SwitchBot Video Doorbell                        | W6702000                           |                                   |
| Keypad Vision                        | Short for SwitchBot Keypad Vision                         | W5600003                           |                                   |
| Keypad Vision Pro                    | Short for SwitchBot Keypad Vision Pro                     | W5600009                           |                                   |
| Lock Ultra                           | Short for SwitchBot Lock Ultra                            | W5600000                           |                                   |
| Standing Circulator Fan              | Short for SwitchBot Standing Circulator Fan               | W3800520                           |                                   |
| Pan/Tilt Cam Plus 2K                 | Short for SwitchBot Pan/Tilt Cam Plus 2K                  | W3101102                           |                                   |
| Pan/Tilt Cam Plus 3K                 | Short for SwitchBot Pan/Tilt Cam Plus 3K                  | W4001100                           |                                   |
| AI Hub                               | Short for SwitchBot AI Hub                                | W8002100                           |                                   |
| Candle Warmer Lamp                   | Short for SwitchBot Candle Warmer Lamp                    | W8302100 and W8302101              |                                   |
| Home Climate Panel                   | Short for SwitchBot Home Climate Panel                    | W7400000                           |                                   |
| Smart Radiator Thermostat            | Short for SwitchBot Smart Radiator Thermostat             | W7830000                           |                                   |
| AI Art Frame                         | Short for SwitchBot AI Art Frame                          | W8402000 and W8402010 and W8402020 |                                   |

### `Legacy` Cloud Services

> Important note: Beyond V9.0, there will NOT be a Cloud Services option in the app. You will see Third-party Services instead. Please read this article for more information, https://support.switch-bot.com/hc/en-us/articles/7257579858455

A SwitchBot app feature, which appears in the app <V9.0 that

1.  Enables SwitchBot products to be discovered and communicated with third-party services such as Home Assistant, Alexa, Google Home, IFTTT, SmartThings, and so forth
2.  Allows users to create customized smart scenes and widgets. For BLE-based devices such as Bot and Curtain
3.  You MUST first add a SwitchBot Hub such as Hub 2, Hub Mini with Matter Enabled, or Hub Mini
4.  Then enable Cloud Services on the Settings page in order to make use of the web API!

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

| Parameter     | Type   | Location | Required | Description                                                                        |
| ------------- | ------ | -------- | -------- | ---------------------------------------------------------------------------------- |
| Authorization | String | header   | Yes      | Open Token acquired                                                                |
| sign          | String | header   | Yes      | A signature generated from the token and secret key using a specific algorithm.    |
| t             | Long   | header   | Yes      | A 13 digit timestamp (standard time).                                              |
| nonce         | Long   | header   | Yes      | A random UUID generated by developers themselves to blend into the string to sign. |

### Standard HTTP Error Codes

The following table lists the most common HTTP error response,

| Code | Name                   | Description                                                                                                                                     |
| :--- | :--------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------- |
| 400  | Bad Request            | The client has issued an invalid request. This is commonly used to specify validation errors in a request payload.                              |
| 401  | Unauthorized           | Authorization for the API is required, but the request has not been authenticated.                                                              |
| 403  | Forbidden              | The request has been authenticated but does not have appropriate permissions, or a requested resource is not found.                             |
| 404  | Not Found              | Specifies the requested path does not exist.                                                                                                    |
| 406  | Not Acceptable         | The client has requested a MIME type via the Accept header for a value not supported by the server.                                             |
| 415  | Unsupported Media Type | The client has defined a contentType header that is not supported by the server.                                                                |
| 422  | Unprocessable Entity   | The client has made a valid request, but the server cannot process it. This is often used for APIs for which certain limits have been exceeded. |
| 429  | Too Many Requests      | The client has exceeded the number of requests allowed for a given time window.                                                                 |
| 500  | Internal Server Error  | An unexpected error on the SmartThings servers has occurred. These errors should be rare.                                                       |

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

- Hub
- Hub Plus
- Hub Mini
- Bot
- Curtain
- Plug
- Meter
- Motion Sensor
- Contact Sensor
- Color Bulb
- Humidifier
- Smart Fan
- Strip Light
- Plug Mini (US)
- Plug Mini (JP)
- Lock
- Meter Plus (JP)
- Meter Plus (US)
- Robot Vacuum Cleaner S1
- Robot Vacuum Cleaner S1 Plus
- Keypad
- Keypad Touch
- Ceiling Light
- Ceiling Light Pro
- Blind Tilt
- Hub 2
- Hub 3
- Outdoor Meter
- Battery Circulator Fan
- Curtain 3
- Lock Pro
- Floor Cleaning Robot S10
- Water Leak Detector
- Mini Robot Vacuum K10+
- Mini Robot Vacuum K10+ Pro
- Meter Pro
- Meter Pro CO2
- Circulator Fan
- Evaporative Humidifier
- Evaporative Humidifier (Auto-refill)
- K10+ Pro Combo
- Air Purifier VOC
- Air Purifier Table VOC
- Air Purifier PM2.5
- Air Purifier Table PM2.5
- Roller Shade
- Relay Switch 1PM
- Relay Switch 1
- Hub 3
- Relay Switch 2PM
- S20
- Floor Lamp
- Strip Light 3
- Garage Door Opener
- Lock Lite
- Video Doorbell
- Keypad Vision
- Lock Ultra
- K20+ Pro
- K11+
- Plug Mini (EU)
- RGBICWW Strip Light
- RGBICWW Floor Lamp
- RGBIC Neon Wire Rope Light
- Smart Radiator Thermostat
- Pan/Tilt Cam Plus 2K
- Pan/Tilt Cam Plus 3K
- `new` Standing Circulator Fan
- `new` AI Hub
- `new` Keypad Vision Pro
- `new` Candle Warmer Lamp
- `new` Presence Sensor
- `new` Home Climate Panel
- `new` RGBIC Neon Rope Light
- `new` AI Art Frame

Virtual infrared remote devices refer to virtual devices that are used to simulate infrared signals of a home appliance remote control. A SwitchBot Hub Plus, Hub Mini, Hub 2, Hub 3 or Ceiling Light is required in order to be able to create these virtual devices within the app. The types of appliances supported include,

- Air Conditioner
- TV
- Light
- Streamer
- Set Top Box
- DVD Player
- Fan
- Projector
- Camera
- Air Purifier
- Speaker
- Water Heater
- Robot Vacuum Cleaner
- Others

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

| Status Code | Body Content       | Message      | Description                                                             |
| ----------- | ------------------ | ------------ | ----------------------------------------------------------------------- |
| 100         | Device list object | success      | Returns an object that contains two device lists                        |
| n/a         | n/a                | Unauthorized | Http 401 Error. User permission is denied due to invalid token.         |
| 190         | n/a                | System error | Device internal error due to device states not synchronized with server |

The `deviceList` array contains a list of objects with the following key-value attributes. For detailed device properties, refer to the individual device documentation files in the devices folder.

#### Sample request

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

Get the status of a physical device that has been added to the current user's account. The response contains device-specific properties such as power state, temperature, battery level, lock state, position values, and other operational parameters depending on the device type.

#### Path parameters

| Name     | Type   | Required | Description |
| -------- | ------ | -------- | ----------- |
| deviceId | String | Yes      | device ID   |

#### Response structure

| Key Name   | Value Type |
| ---------- | ---------- |
| statusCode | Integer    |
| message    | String     |
| body       | Object     |

#### Response codes

| Status Code | Body Content       | Message      | Description                                                             |
| ----------- | ------------------ | ------------ | ----------------------------------------------------------------------- |
| 100         | Device list object | success      | Returns an object that contains two device lists                        |
| n/a         | n/a                | Unauthorized | Http 401 Error. User permission is denied due to invalid token.         |
| 190         | n/a                | System error | Device internal error due to device states not synchronized with server |


#### Sample requests

##### Get Meter status

```http
GET https://api.switch-bot.com/v1.1/devices/C271111EC0AB/status
```

Response:

```json
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

##### Get Curtain status

```http
GET https://api.switch-bot.com/v1.1/devices/E2F6032048AB/status
```

Response:

```json
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

Send control commands to physical devices and virtual infrared remote devices to control their behavior, such as turning on/off, changing settings, or triggering actions.

#### Path parameters

| Name     | Type   | Required | Description |
| -------- | ------ | -------- | ----------- |
| deviceId | String | Yes      | device ID   |

#### Request body parameters

| Name        | Type          | Required | Description                                                               |
| ----------- | ------------- | -------- | ------------------------------------------------------------------------- |
| command     | String        | Yes      | the name of the command                                                   |
| parameter   | String/Object | No       | some commands require parameters, such as `SetChannel` or position values |
| commandType | String        | No       | for customized buttons on virtual devices, set to `customize`             |

#### Response

| Key Name   | Value Type |
| ---------- | ---------- |
| statusCode | Integer    |
| message    | String     |
| body       | Object     |

#### Error codes

| Error code/message          | Description                                                                                            |
| --------------------------- | ------------------------------------------------------------------------------------------------------ |
| {"message": "Unauthorized"} | Http 401 Error. User permission is denied due to invalid token.                                        |
| 151                         | device type error                                                                                      |
| 152                         | device not found                                                                                       |
| 160                         | command is not supported                                                                               |
| 161                         | device offline                                                                                         |
| 171                         | hub device is offline                                                                                  |
| 190                         | Device internal error due to device states not synchronized with server. Or command format is invalid. |

#### Sample request

##### Control Floor Cleaning Robot S10

Start cleaning with vacuum and mop:

```http
POST https://api.switch-bot.com/v1.1/devices/F7538E1ABC23/commands
```

Request body:

```json
{
    "commandType": "command",
    "command": "startClean",
    "parameter": {
        "action": "sweep_mop",
        "param": {
            "fanLevel": 1,
            "waterLevel": 1,
            "times": 1
        }
    }
}
```

Response:

```json
{
    "statusCode": 100,
    "body": {
        "commandId": "CMD166444044923602"
    },
    "message": "success"
}
```

##### Change the cleaning settings


Request

```http
POST https://api.switch-bot.com/v1.1/devices/F7538E1ABC23/commands
```

```json
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

```json
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

```json
{
    "command": "setAll",
    "parameter": "26,1,3,on",
    "commandType": "command"
}
```

Response

```json
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

```json
{
    "command": "ボタン", // the name of the customized button
    "parameter": "default",
    "commandType": "customize"
}
```

Response

```json
{
    "statusCode": 100,
    "body": {},
    "message": "success"
}
```

## Scenes

The Scenes API allows you to access smart scenes created by users and execute manual scenes for home automation workflows.

### Get scene list

```http
GET /v1.1/scenes
```

#### Description

Get a list of all manual scenes created by the current user's account.

#### Response structure

| Key Name   | Value Type |
| ---------- | ---------- |
| statusCode | Integer    |
| message    | String     |
| body       | Array      |

#### Response body schema

The body contains an array of scene objects. Each scene object has:

| Key       | Type   | Description    |
| --------- | ------ | -------------- |
| sceneId   | String | a scene's ID   |
| sceneName | String | a scene's name |

#### Error codes

| Code/Message                | Description                                                             |
| --------------------------- | ----------------------------------------------------------------------- |
| 100                         | success                                                                 |
| {"message": "Unauthorized"} | Http 401 Error. User permission is denied due to invalid token.         |
| 190                         | Device internal error due to device states not synchronized with server |


#### Sample request

```http
GET https://api.switch-bot.com/v1.1/scenes
```

Response:

```json
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

Execute a manual scene from the user's list of scenes. This triggers all actions configured in the scene.

#### Path parameters

| Name    | Type   | Required | Description |
| ------- | ------ | -------- | ----------- |
| sceneId | String | Yes      | scene ID    |

#### Response structure

| Key Name   | Value Type |
| ---------- | ---------- |
| statusCode | Integer    |
| message    | String     |
| body       | Object     |

#### Error codes

| Code/Message                | Description                                                             |
| --------------------------- | ----------------------------------------------------------------------- |
| 100                         | success                                                                 |
| {"message": "Unauthorized"} | Http 401 Error. User permission is denied due to invalid token.         |
| 190                         | Device internal error due to device states not synchronized with server |


#### Sample request

```http
POST https://api.switch-bot.com/v1.1/scenes/T02-202009221414-48924101/execute
```

Response:

```json
{
    "statusCode": 100,
    "body": {},
    "message": "success"
}
```

## Webhook

### Configure webhook

```http
POST /v1.1/webhook/setupWebhook
```

#### Description

Configure the URL where webhook events will be sent. All device and scene events will be delivered to this endpoint.

#### Request body parameters

| Key Name   | Type   | Description                                     |
| ---------- | ------ | ----------------------------------------------- |
| action     | String | required; value: `setupWebhook`                 |
| url        | String | the URL endpoint where events will be sent      |
| deviceList | String | the list of devices; currently supports `"ALL"` |

#### Example request

```json
{
    "action": "setupWebhook",
    "url": "https://your-domain.com/switchbot-webhook",
    "deviceList": "ALL"
}
```

#### Response

```json
{
    "statusCode": 100,
    "body": {},
    "message": "success"
}
```

### Query webhook configuration

```http
POST /v1.1/webhook/queryWebhook
```

#### Description

Get current webhook configuration details.

#### Request body parameters

| Key Name | Value Type | Description                                                                                   |
| -------- | ---------- | --------------------------------------------------------------------------------------------- |
| action   | String     | the type of actions, currently supports "queryUrl", "queryDetails"                            |
| url      | String     | the url where all the events are sent to. you need to specify the url when using queryDetails |

#### Request types

**Query Webhook URL**:

```json
{
    "action": "queryUrl"
}
```

**Query Webhook Details**:

```json
{
    "action": "queryDetails",
    "urls": ["https://your-domain.com/switchbot-webhook"]
}
```

#### Response examples

**queryUrl Response**:

```json
{
    "statusCode": 100,
    "body": {
        "urls": ["https://your-domain.com/switchbot-webhook"]
    },
    "message": "success"
}
```

**queryDetails Response**:

```json
{
    "statusCode": 100,
    "body": [
        {
            "url": "https://your-domain.com/switchbot-webhook",
            "createTime": 1634567890,
            "lastUpdateTime": 1634567890,
            "deviceList": "ALL",
            "enable": true
        }
    ],
    "message": "success"
}
```

### Update webhook configuration

```http
POST /v1.1/webhook/updateWebhook
```

#### Description

Update webhook configuration such as URL, enable/disable status, or device list.

#### Request body parameters

| Key Name | Type   | Description                                                                                                                            |
| -------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| action   | String | value: `updateWebhook`                                                                                                                 |
| config   | Object | the configuration details you want to update. you can change the current url or enable/disable the webhook. refer to the example below |

#### Example request

```json
{
    "action": "updateWebhook",
    "config": {
        "url": "https://your-domain.com/new-webhook-url",
        "enable": true
    }
}
```

#### Response

```json
{
    "statusCode": 100,
    "body": {},
    "message": "success"
}
```

### Delete webhook

```http
POST /v1.1/webhook/deleteWebhook
```

#### Description

Delete the webhook configuration. After deletion, no events will be sent to the webhook URL.

#### Request body parameters

| Key Name | Type   | Description               |
| -------- | ------ | ------------------------- |
| action   | String | value: `deleteWebhook`    |
| url      | String | the webhook URL to delete |

#### Example request

```json
{
    "action": "deleteWebhook",
    "url": "https://your-domain.com/switchbot-webhook"
}
```

#### Response

```json
{
    "statusCode": 100,
    "body": {},
    "message": "success"
}
```

### Webhook event structure

Webhook events are sent as POST requests in JSON format. The structure varies by device type and event.

#### Common webhook event properties

| Property     | Type   | Description                  |
| ------------ | ------ | ---------------------------- |
| eventType    | String | the type of events           |
| eventVersion | String | the current event version    |
| context      | Object | the detail info of the event |

#### Bot event example

```json
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
#### Curtain event example

```json
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

## Device Specifications and Supported Features List

### Hubs

| Device                                                                             | List | Status | Command | Webhook |
| ---------------------------------------------------------------------------------- | ---- | ------ | ------- | ------- |
| [AI Hub](devices/hubs/ai-hub.md)                                                   | ✓    | ✓      | -       | -       |
| [Hub 2](devices/hubs/hub-2.md)                                                     | ✓    | ✓      | -       | ✓       |
| [Hub 3](devices/hubs/hub-3.md)                                                     | ✓    | ✓      | -       | ✓       |
| [Hub/Hub Plus/Hub Mini/Hub 2/Hub 3](devices/hubs/hubhub-plushub-minihub-2hub-3.md) | ✓    | -      | -       | -       |

### Locks & Security

| Device                                                                       | List | Status | Command | Webhook |
| ---------------------------------------------------------------------------- | ---- | ------ | ------- | ------- |
| [Keypad](devices/locks-security/keypad.md)                                   | ✓    | ✓      | ✓       | ✓       |
| [Keypad Touch](devices/locks-security/keypad-touch.md)                       | ✓    | ✓      | ✓       | ✓       |
| [Keypad Vision](devices/locks-security/keypad-vision.md)                     | ✓    | ✓      | ✓       | ✓       |
| [Keypad Vision Pro](devices/locks-security/keypad-vision-pro.md)             | ✓    | ✓      | ✓       | ✓       |
| [Lock](devices/locks-security/lock.md)                                       | ✓    | ✓      | ✓       | ✓       |
| [Lock Lite](devices/locks-security/lock-lite.md)                             | ✓    | ✓      | ✓       | ✓       |
| [Lock Pro](devices/locks-security/lock-pro.md)                               | ✓    | ✓      | ✓       | ✓       |
| [Lock Pro Matter Enabled](devices/locks-security/lock-pro-matter-enabled.md) | ✓    | ✓      | ✓       | ✓       |
| [Lock Ultra](devices/locks-security/lock-ultra.md)                           | ✓    | ✓      | ✓       | ✓       |
| [Lock Vision](devices/locks-security/lock-vision.md)                         | ✓    | ✓      | ✓       | ✓       |
| [Lock Vision Pro](devices/locks-security/lock-vision-pro.md)                 | ✓    | ✓      | ✓       | ✓       |
| [Video Doorbell](devices/cameras/video-doorbell.md)                          | ✓    | ✓      | ✓       | ✓       |

### Curtains & Blinds

| Device                                                  | List | Status | Command | Webhook |
| ------------------------------------------------------- | ---- | ------ | ------- | ------- |
| [Blind Tilt](devices/curtains-blinds/blind-tilt.md)     | ✓    | ✓      | ✓       | -       |
| [Curtain](devices/curtains-blinds/curtain.md)           | ✓    | ✓      | ✓       | ✓       |
| [Curtain 3](devices/curtains-blinds/curtain-3.md)       | ✓    | ✓      | ✓       | ✓       |
| [Roller Shade](devices/curtains-blinds/roller-shade.md) | ✓    | ✓      | ✓       | ✓       |

### Sensors

| Device                                                        | List | Status | Command | Webhook |
| ------------------------------------------------------------- | ---- | ------ | ------- | ------- |
| [Contact Sensor](devices/sensors/contact-sensor.md)           | ✓    | ✓      | -       | ✓       |
| [Meter](devices/sensors/meter.md)                             | ✓    | ✓      | -       | ✓       |
| [Meter Plus](devices/sensors/meter-plus.md)                   | ✓    | ✓      | -       | ✓       |
| [Meter Pro](devices/sensors/meter-pro.md)                     | ✓    | ✓      | -       | ✓       |
| [Meter Pro CO2](devices/sensors/meter-pro-co2.md)             | ✓    | ✓      | -       | ✓       |
| [Motion Sensor](devices/sensors/motion-sensor.md)             | ✓    | ✓      | -       | ✓       |
| [Outdoor Meter](devices/sensors/outdoor-meter.md)             | ✓    | ✓      | -       | ✓       |
| [Presence Sensor](devices/sensors/presence-sensor.md)         | ✓    | ✓      | -       | ✓       |
| [Water Leak Detector](devices/sensors/water-leak-detector.md) | ✓    | ✓      | -       | ✓       |

### Lighting

| Device                                                                       | List | Status | Command | Webhook |
| ---------------------------------------------------------------------------- | ---- | ------ | ------- | ------- |
| [Candle Warmer Lamp](devices/lighting/candle-warmer-lamp.md)                 | ✓    | ✓      | ✓       | ✓       |
| [Ceiling Light](devices/lighting/ceiling-light.md)                           | ✓    | ✓      | ✓       | ✓       |
| [Ceiling Light Pro](devices/lighting/ceiling-light-pro.md)                   | ✓    | ✓      | ✓       | ✓       |
| [Color Bulb](devices/lighting/color-bulb.md)                                 | ✓    | ✓      | ✓       | ✓       |
| [Floor Lamp](devices/lighting/floor-lamp.md)                                 | ✓    | ✓      | ✓       | ✓       |
| [RGBIC Neon Rope Light](devices/lighting/rgbic-neon-rope-light.md)           | ✓    | ✓      | ✓       | ✓       |
| [RGBIC Neon Wire Rope Light](devices/lighting/rgbic-neon-wire-rope-light.md) | ✓    | ✓      | ✓       | ✓       |
| [RGBICWW Floor Lamp](devices/lighting/rgbicww-floor-lamp.md)                 | ✓    | ✓      | ✓       | ✓       |
| [RGBICWW Strip Light](devices/lighting/rgbicww-strip-light.md)               | ✓    | ✓      | ✓       | ✓       |
| [Strip Light](devices/lighting/strip-light.md)                               | ✓    | ✓      | ✓       | ✓       |
| [Strip Light 3](devices/lighting/strip-light-3.md)                           | ✓    | ✓      | ✓       | ✓       |

### Robot Vacuum

| Device                                                                               | List | Status | Command | Webhook |
| ------------------------------------------------------------------------------------ | ---- | ------ | ------- | ------- |
| [Floor Cleaning Robot S10](devices/robot-vacuum/floor-cleaning-robot-s10.md)         | ✓    | ✓      | ✓       | ✓       |
| [Floor Cleaning Robot S20](devices/robot-vacuum/floor-cleaning-robot-s20.md)         | ✓    | ✓      | ✓       | ✓       |
| [K10+ Pro Combo](devices/robot-vacuum/k10-pro-combo.md)                              | ✓    | ✓      | ✓       | ✓       |
| [K20+ Pro](devices/robot-vacuum/k20-pro.md)                                          | ✓    | ✓      | ✓       | ✓       |
| [Mini Robot Vacuum K10+](devices/robot-vacuum/mini-robot-vacuum-k10.md)              | ✓    | ✓      | ✓       | ✓       |
| [Mini Robot Vacuum K10+ Pro](devices/robot-vacuum/mini-robot-vacuum-k10-pro.md)      | ✓    | ✓      | ✓       | ✓       |
| [Robot Vacuum Cleaner S1](devices/robot-vacuum/robot-vacuum-cleaner-s1.md)           | ✓    | ✓      | ✓       | ✓       |
| [Robot Vacuum Cleaner S1 Plus](devices/robot-vacuum/robot-vacuum-cleaner-s1-plus.md) | ✓    | ✓      | ✓       | ✓       |
| [Robot Vacuum K11+](devices/robot-vacuum/robot-vacuum-k11.md)                        | ✓    | ✓      | ✓       | ✓       |

### Climate Control

| Device                                                                                                | List | Status | Command | Webhook |
| ----------------------------------------------------------------------------------------------------- | ---- | ------ | ------- | ------- |
| [Air Purifier PM2.5](devices/climate-control/air-purifier-pm25.md)                                    | ✓    | ✓      | ✓       | ✓       |
| [Air Purifier Table PM2.5](devices/climate-control/air-purifier-table-pm25.md)                        | ✓    | ✓      | ✓       | ✓       |
| [Air Purifier Table VOC](devices/climate-control/air-purifier-table-voc.md)                           | ✓    | ✓      | ✓       | ✓       |
| [Air Purifier VOC](devices/climate-control/air-purifier-voc.md)                                       | ✓    | ✓      | ✓       | ✓       |
| [Battery Circulator Fan](devices/climate-control/battery-circulator-fan.md)                           | ✓    | ✓      | ✓       | ✓       |
| [Circulator Fan](devices/climate-control/circulator-fan.md)                                           | ✓    | ✓      | ✓       | ✓       |
| [Evaporative Humidifier](devices/climate-control/evaporative-humidifier.md)                           | ✓    | ✓      | ✓       | ✓       |
| [Evaporative Humidifier (Auto-refill)](devices/climate-control/evaporative-humidifier-auto-refill.md) | ✓    | ✓      | ✓       | ✓       |
| [Home Climate Panel](devices/climate-control/home-climate-panel.md)                                   | ✓    | ✓      | -       | ✓       |
| [Humidifier](devices/climate-control/humidifier.md)                                                   | ✓    | ✓      | ✓       | -       |
| [Smart Radiator Thermostat](devices/climate-control/smart-radiator-thermostat.md)                     | ✓    | ✓      | ✓       | ✓       |
| [Standing Circulator Fan](devices/climate-control/standing-circulator-fan.md)                         | ✓    | ✓      | ✓       | ✓       |

### Plugs & Switches

| Device                                                             | List | Status | Command | Webhook |
| ------------------------------------------------------------------ | ---- | ------ | ------- | ------- |
| [Garage Door Opener](devices/plugs-switches/garage-door-opener.md) | ✓    | ✓      | ✓       | ✓       |
| [Plug](devices/plugs-switches/plug.md)                             | ✓    | ✓      | ✓       | -       |
| [Plug Mini (EU)](devices/plugs-switches/plug-mini-eu.md)           | ✓    | ✓      | ✓       | ✓       |
| [Plug Mini (JP)](devices/plugs-switches/plug-mini-jp.md)           | ✓    | ✓      | ✓       | ✓       |
| [Plug Mini (US)](devices/plugs-switches/plug-mini-us.md)           | ✓    | ✓      | ✓       | ✓       |
| [Relay Switch 1](devices/plugs-switches/relay-switch-1.md)         | ✓    | ✓      | ✓       | ✓       |
| [Relay Switch 1PM](devices/plugs-switches/relay-switch-1pm.md)     | ✓    | ✓      | ✓       | ✓       |
| [Relay Switch 2PM](devices/plugs-switches/relay-switch-2pm.md)     | ✓    | ✓      | ✓       | ✓       |

### Cameras

| Device                                                         | List | Status | Command | Webhook |
| -------------------------------------------------------------- | ---- | ------ | ------- | ------- |
| [Indoor Cam](devices/cameras/indoor-cam.md)                    | ✓    | -      | -       | ✓       |
| [Pan/Tilt Cam](devices/cameras/pantilt-cam.md)                 | ✓    | -      | -       | ✓       |
| [Pan/Tilt Cam 2K](devices/cameras/pantilt-cam-2k.md)           | ✓    | -      | -       | -       |
| [Pan/Tilt Cam Plus 2K](devices/cameras/pantilt-cam-plus-2k.md) | ✓    | -      | -       | -       |
| [Pan/Tilt Cam Plus 3K](devices/cameras/pantilt-cam-plus-3k.md) | ✓    | -      | -       | -       |

### Others

| Device                                                                               | List | Status | Command | Webhook |
| ------------------------------------------------------------------------------------ | ---- | ------ | ------- | ------- |
| [Bot](devices/others/bot.md)                                                         | ✓    | ✓      | ✓       | ✓       |
| [Remote](devices/others/remote.md)                                                   | ✓    | -      | -       | -       |
| [AI Art Frame](devices/others/ai-art-frame.md)                                       | ✓    | ✓      | ✓       | ✓       |
| [Weather Station](devices/others/weather-station.md)                                 | ✓    | ✓      | ✓       | ✓       |
| [Virtual infrared remote devices](devices/others/virtual-infrared-remote-devices.md) | ✓    | -      | ✓       | -       |


----

* [SwitchBot (Official website)](https://www.switch-bot.com/)
* [Facebook @SwitchBotRobot](https://www.facebook.com/SwitchBotRobot/) 
* [Twitter @SwitchBot](https://twitter.com/switchbot) 