# Coronavirus API

![Coronavirus API](https://quarantine.country/coronavirus/api/coronavirus-api.png)

**Coronavirus API** > **Coronavirus Update**. Live coronavirus updates for statistics with historical data, maps, charts, graphs. Coronavirus (COVID-19) live updates and historical data including *Day*, *Week*, *Month*, *Year*, *Change per Day*, *Difference*, and *Summary*. *Total Cases*, *Active*, *Deaths*, *Recovered* and *% ratio*. World *Regions* by *Country* and by *State*. **Spots** (day, week, month, year and other). Free corona virus live updates with COVID-19 API.

> It is very important to verify the sources used by the API you’re about to implement in your own website/software. It is also important that the given **API has a way to detect and avoid passing wrong data** (e.g. caused by hacked source/database). There are simple ways of detecting wrong numbers, make sure the API you select is safely serving the correct case numbers.

## Coronavirus API ##

**[API Home Page](https://quarantine.country/coronavirus/api/)** | **[Demo](https://quarantine.country/coronavirus/cases/usa/)** | **[API Documentation](https://quarantine.country/coronavirus/api/documentation/v1/)**

### API Description ###
Coronavirus (COVID-19) live updates and historical data including *Day*, *Week*, *Month*, *Year*, *Change per Day*, *Difference*, and *Summary*. *Total Cases*, *Active*, *Deaths*, *Recovered* and *% ratio*. World *Regions* by *Country* and by *State*. **Spots** (day, week, month, year and other). Free corona virus live updates with COVID-19 API.

![Coronavirus API](https://quarantine.country/coronavirus/api/coronavirus-api.jpg)

### Feeds ###

- GET Latest Data: `https://public.api.quarantine.country/summary/latest`
- GET Region Statistics: `https://public.api.quarantine.country/summary/region?region=usa`

### Spots ###

- GET Day: `https://public.api.quarantine.country/spots/day?region=usa`
- GET Week: `https://public.api.quarantine.country/spots/week?region=usa`
- GET Month: `https://public.api.quarantine.country/spots/month?region=usa`
- GET Year: `https://public.api.quarantine.country/spots/year?region=usa`
- GET All: `https://public.api.quarantine.country/spots/all?region=usa`

### Ping ###

- GET Ping: `public.api.quarantine.country/ping`

### Examples ###


JavaScript - jQuery
```JavaScript
var form = new FormData();
form.append("client_id", "{{client_id}}");
form.append("client_secret", "{{client_secret}}");
form.append("grant_type", "client_credentials");
form.append("scope", "*");

var settings = {
  "url": "https://api.quarantine.country/api/v1/passport/token",
  "method": "POST",
  "timeout": 0,
  "processData": false,
  "mimeType": "multipart/form-data",
  "contentType": false,
  "data": form
};

$.ajax(settings).done(function (response) {
  console.log(response);
});

```

NodeJS
```JavaScript
var https = require('follow-redirects').https;
var fs = require('fs');

var options = {
  'method': 'POST',
  'hostname': 'https://api.quarantine.country',
  'path': '/api/v1/passport/token',
  'headers': {
  },
  'maxRedirects': 20
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"client_id\"\r\n\r\n{{client_id}}\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"client_secret\"\r\n\r\n{{client_secret}}\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"grant_type\"\r\n\r\nclient_credentials\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"scope\"\r\n\r\n*\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();
```

cURL
```bash
curl --location --request POST 'https://api.quarantine.country/api/v1/passport/token' \
--form 'client_id={{client_id}}' \
--form 'client_secret={{client_secret}}' \
--form 'grant_type=client_credentials' \
--form 'scope=*'
```

PHP - cURL
```PHP
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.quarantine.country/api/v1/passport/token",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('client_id' => '{{client_id}}','client_secret' => '{{client_secret}}','grant_type' => 'client_credentials','scope' => '*'),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

C - libcurl
```C
CURL *curl;
CURLcode res;
curl = curl_easy_init();
if(curl) {
  curl_easy_setopt(curl, CURLOPT_CUSTOMREQUEST, "POST");
  curl_easy_setopt(curl, CURLOPT_URL, "https://api.quarantine.country/api/v1/passport/token");
  curl_easy_setopt(curl, CURLOPT_FOLLOWLOCATION, 1L);
  curl_easy_setopt(curl, CURLOPT_DEFAULT_PROTOCOL, "https");
  struct curl_slist *headers = NULL;
  curl_easy_setopt(curl, CURLOPT_HTTPHEADER, headers);
  curl_mime *mime;
  curl_mimepart *part;
  mime = curl_mime_init(curl);
  part = curl_mime_addpart(mime);
  curl_mime_name(part, "client_id");
  curl_mime_data(part, "{{client_id}}", CURL_ZERO_TERMINATED);
  part = curl_mime_addpart(mime);
  curl_mime_name(part, "client_secret");
  curl_mime_data(part, "{{client_secret}}", CURL_ZERO_TERMINATED);
  part = curl_mime_addpart(mime);
  curl_mime_name(part, "grant_type");
  curl_mime_data(part, "client_credentials", CURL_ZERO_TERMINATED);
  part = curl_mime_addpart(mime);
  curl_mime_name(part, "scope");
  curl_mime_data(part, "*", CURL_ZERO_TERMINATED);
  curl_easy_setopt(curl, CURLOPT_MIMEPOST, mime);
  res = curl_easy_perform(curl);
  curl_mime_free(mime);
}
curl_easy_cleanup(curl);
```

More examples and details

[quarantine.country/coronavirus/api/documentation/v1/](https://quarantine.country/coronavirus/api/documentation/v1/)

### Latest updates ###

Please use `public.api.quarantine.country/*` on production and/or when using API without personal token

[Coronavirus API latest updates](https://quarantine.country/coronavirus/api/)
