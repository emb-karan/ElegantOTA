<p align="center"><img src="https://raw.githubusercontent.com/ayushsharma82/ElegantOTA/master/docs/logo.svg?sanitize=true" width="400"></p>

<hr/>
<p align="center">
<!-- <img src="https://img.shields.io/travis/com/ayushsharma82/ESP-DASH.svg?style=for-the-badge" />
&nbsp; -->
<img src="https://img.shields.io/github/last-commit/ayushsharma82/ElegantOTA.svg?style=for-the-badge" />
&nbsp;
<img src="https://img.shields.io/github/license/ayushsharma82/ElegantOTA.svg?style=for-the-badge" />
&nbsp;
<a href="https://www.buymeacoffee.com/6QGVpSj" target="_blank"><img src="https://img.shields.io/badge/Buy%20me%20a%20coffee-%245-orange?style=for-the-badge&logo=buy-me-a-coffee" /></a>
</p>
<hr/>


<p align="center">Push OTAs to ESP8266 Elegantly! </p>
<p align="center">
ElegantOTA provides a beautiful interface to upload Over the Air `.bin` updates to your ESP Modules with precise status and progress displayed over UI. This Library shows the current upload progress of your OTA and once finished, it will display the status of your OTA.
</p>

<br>
<br>

<p align="center"><img src="https://raw.githubusercontent.com/ayushsharma82/ElegantOTA/master/docs/elegantOtaDemo.gif"></p>

<br>
<br>

<h2>How to Install</h2>

###### Directly Through Arduino IDE ( Currently Submitted for Approval. Use Mannual Install till it gets Approved.)
Go to Sketch > Include Library > Library Manager > Search for "ElegantOTA" > Install

###### Manual Install

For Windows: Download the [Repository](https://github.com/ayushsharma82/ElegantOTA/archive/master.zip) and extract the .zip in Documents>Arduino>Libraries>{Place "ElegantOTA" folder Here}

For Linux: Download the [Repository](https://github.com/ayushsharma82/ElegantOTA/archive/master.zip) and extract the .zip in Sketchbook>Libraries>{Place "ElegantOTA" folder Here}

###### Manually through IDE

Download the [Repository](https://github.com/ayushsharma82/ElegantOTA/archive/master.zip), Go to Sketch>Include Library>Add .zip Library> Select the Downloaded .zip File.

<br>

<h2>Documentation</h2>
<p>ElegantOTA is a dead simple library which does your work in just 1 Line. Honestly, It's just a wrapper library which injects it's own elegant webpage instead of the ugly upload page which comes by default in Arduino Library.</p>

 Include ElegantOTA Library `#include <ElegantOTA.h>` at top of your Arduino Code.
 
 Paste this - `ElegantOTA.begin(&server);`  line above your `server.begin();`
 
 That's all!

<hr/>

Now copy the IPAddress displayed over your Serial Monitor and go to `http://<IPAddress>/update` in browser. ( where `<IPAddress>` is the IP of your ESP Module)

<hr/>

By default, ElegantOTA uses your chip id as a unique id for your esp chip on webpage. If you want to set a custom id, then you can set it via `ElegantOTA.setID("abcd123");`. Best to place it above `ElegantOTA.begin` function.

 
<br>
<h2>Example</h2>
 
```

#include <ESP8266WiFi.h>
#include <WiFiClient.h>
#include <ESP8266WebServer.h>
#include <ElegantOTA.h>

const char* ssid = "........";
const char* password = "........";

ESP8266WebServer server(80);


void setup(void) {
  Serial.begin(115200);
  WiFi.mode(WIFI_STA);
  WiFi.begin(ssid, password);
  Serial.println("");

  // Wait for connection
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  Serial.println("");
  Serial.print("Connected to ");
  Serial.println(ssid);
  Serial.print("IP address: ");
  Serial.println(WiFi.localIP());

  server.on("/", []() {
    server.send(200, "text/plain", "Hi! I am ESP8266.");
  });

  ElegantOTA.begin(&server);    // Start ElegantOTA
  server.begin();
  Serial.println("HTTP server started");
}

void loop(void) {
  server.handleClient();
}

```
<br>

<h2>Contributions</h2>
<p>Every Contribution to this repository is highly appriciated! Don't fear to create pull requests which enhance or fix the library as ultimatly you are going to help everybody.</p>
<p>
If you want to donate to the author then <b>you can buy me a coffee</b>, It really helps me keep these libraries updated:
<br/><br/>
<a href="https://www.buymeacoffee.com/6QGVpSj" target="_blank"><img src="https://img.shields.io/badge/Buy%20me%20a%20coffee-%245-orange?style=for-the-badge&logo=buy-me-a-coffee" /></a>
</p>
<br/>
<br/>


<h2>License</h2>
ElegantOTA is licensed under The MIT License ( MIT ).
<br/>
<br/>
<img src="https://img.shields.io/github/license/ayushsharma82/ElegantOTA.svg?style=for-the-badge" />
</div>
