---
title: Vettd Data Observatory (VDO) API Documentation
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - javascript--nodejs: Node.JS
  - ruby: Ruby
  - python: Python
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<h1 id="VDO">Vettd Data Observatory (VDO) API Documentation v0.9.0.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Vettd Data Observatory API allows clients to utilize Vettd's services to do some cool Data Science processing.

NOTE: Most calls require the Authorization to be set above. Status Code 401 means you are not logged in while 403 means you are logged in but just do not have permissions to perform the action.

Base URLs:

* <a href="/">/</a>

# Authentication

* API Key (Bearer)
    - Parameter Name: **Authorization**, in: header. Please insert JWT with Bearer into field. You can use the POST /vdo/auth call to get the token. 

<h1 id="VDO-Download">Download</h1>

## GetDownloadDataset

<a id="opIdGetDownloadDataset"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/storage/datasets/{datasetid}/download \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/storage/datasets/{datasetid}/download HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/storage/datasets/{datasetid}/download',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/storage/datasets/{datasetid}/download',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/storage/datasets/{datasetid}/download',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/storage/datasets/{datasetid}/download', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/storage/datasets/{datasetid}/download");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/storage/datasets/{datasetid}/download", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/storage/datasets/{datasetid}/download`

*Download all assets of a dataset as a zip file*

<h3 id="GetDownloadDataset-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|datasetid|path|string(uuid)|true|none|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
{
  "contentType": "string",
  "fileDownloadName": "string",
  "lastModified": "2018-05-15T17:51:34Z",
  "entityTag": {
    "tag": {
      "buffer": "string",
      "offset": 0,
      "length": 0,
      "value": "string",
      "hasValue": true
    },
    "isWeak": true
  }
}
```

```json
{
  "contentType": "string",
  "fileDownloadName": "string",
  "lastModified": "2018-05-15T17:51:34Z",
  "entityTag": {
    "tag": {
      "buffer": "string",
      "offset": 0,
      "length": 0,
      "value": "string",
      "hasValue": true
    },
    "isWeak": true
  }
}
```

<h3 id="GetDownloadDataset-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[FileResult](#schemafileresult)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<aside class="success">
This operation does not require authentication
</aside>

## GetDownloadAssets

<a id="opIdGetDownloadAssets"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/storage/assets/{assetid}/download \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/storage/assets/{assetid}/download HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/storage/assets/{assetid}/download',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/storage/assets/{assetid}/download',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/storage/assets/{assetid}/download',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/storage/assets/{assetid}/download', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/storage/assets/{assetid}/download");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/storage/assets/{assetid}/download", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/storage/assets/{assetid}/download`

*Download an Asset by its Id*

<h3 id="GetDownloadAsset-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|assetid|path|string(uuid)|true|none|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
{
  "contentType": "string",
  "fileDownloadName": "string",
  "lastModified": "2018-05-15T17:51:34Z",
  "entityTag": {
    "tag": {
      "buffer": "string",
      "offset": 0,
      "length": 0,
      "value": "string",
      "hasValue": true
    },
    "isWeak": true
  }
}
```

```json
{
  "contentType": "string",
  "fileDownloadName": "string",
  "lastModified": "2018-05-15T17:51:34Z",
  "entityTag": {
    "tag": {
      "buffer": "string",
      "offset": 0,
      "length": 0,
      "value": "string",
      "hasValue": true
    },
    "isWeak": true
  }
}
```

<h3 id="GetDownloadAsset-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[FileResult](#schemafileresult)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="VDO-Entity">Entity</h1>

## EntitiesGet

<a id="opIdEntitiesGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/entities?startdate=2018-05-15T17%3A51%3A34Z&enddate=2018-05-15T17%3A51%3A34Z \
  -H 'Accept: application/json' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/entities?startdate=2018-05-15T17%3A51%3A34Z&enddate=2018-05-15T17%3A51%3A34Z HTTP/1.1
Host: null

Accept: application/json
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'application/json',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/entities',
  method: 'get',
  data: '?startdate=2018-05-15T17%3A51%3A34Z&enddate=2018-05-15T17%3A51%3A34Z',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/entities?startdate=2018-05-15T17%3A51%3A34Z&enddate=2018-05-15T17%3A51%3A34Z',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/entities',
  params: {
  'startdate' => 'string(date-time)',
'enddate' => 'string(date-time)'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/entities', params={
  'startdate': '2018-05-15T17:51:34Z',  'enddate': '2018-05-15T17:51:34Z'
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/entities?startdate=2018-05-15T17%3A51%3A34Z&enddate=2018-05-15T17%3A51%3A34Z");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/entities", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/entities`

<h3 id="vdov1entitiesget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|startdate|query|string(date-time)|true|none|
|enddate|query|string(date-time)|true|none|
|entitytype|query|string|false|none|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
[
  {
    "enitityId": "string",
    "source": "string",
    "sourceId": "string",
    "type": "string",
    "object": {},
    "createDate": "2018-05-15T17:51:34Z",
    "entityAssets": [
      {
        "enitityAssetId": "string",
        "assetId": "string",
        "type": "string",
        "object": {},
        "createDate": "2018-05-15T17:51:34Z"
      }
    ]
  }
]
```

<h3 id="vdov1entitiesget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<h3 id="vdov1entitiesget-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[EntityResponse](#schemaentityresponse)]|false|none|none|
|» enitityId|string(uuid)|false|none|none|
|» source|string|false|none|none|
|» sourceId|string(uuid)|false|none|none|
|» type|string|false|none|none|
|» object|object|false|none|none|
|» createDate|string(date-time)|false|none|none|
|» entityAssets|[[EntityAssetResponse](#schemaentityassetresponse)]|false|none|none|
|»» enitityAssetId|string(uuid)|false|none|none|
|»» assetId|string(uuid)|false|none|none|
|»» type|string|false|none|none|
|»» object|object|false|none|none|
|»» createDate|string(date-time)|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## EntitiesPost

<a id="opIdEntitiesPost"></a>

> Code samples

```shell
# You can also use wget
curl -X POST //vdo/v1/entities \
  -H 'Content-Type: application/json-patch+json' \
  -H 'Accept: application/json' \
  -H 'X-Api-Key: string'

```

```http
POST //vdo/v1/entities HTTP/1.1
Host: null
Content-Type: application/json-patch+json
Accept: application/json
X-Api-Key: string

```

```javascript
var headers = {
  'Content-Type':'application/json-patch+json',
  'Accept':'application/json',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/entities',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "uniqueid": "string",
  "source": "string",
  "entity": {
    "data": "string",
    "type": "string"
  },
  "entityasset": {
    "data": "string",
    "type": "string"
  }
}';
const headers = {
  'Content-Type':'application/json-patch+json',
  'Accept':'application/json',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/entities',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json-patch+json',
  'Accept' => 'application/json',
  'X-Api-Key' => 'string'
}

result = RestClient.post '//vdo/v1/entities',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json-patch+json',
  'Accept': 'application/json',
  'X-Api-Key': 'string'
}

r = requests.post('//vdo/v1/entities', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/entities");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json-patch+json"},
        "Accept": []string{"application/json"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "//vdo/v1/entities", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /vdo/v1/entities`

> Body parameter

```json
{
  "uniqueid": "string",
  "source": "string",
  "entity": {
    "data": "string",
    "type": "string"
  },
  "entityasset": {
    "data": "string",
    "type": "string"
  }
}
```

<h3 id="vdov1entitiespost-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|
|body|body|[EntityDataSaveRequest](#schemaentitydatasaverequest)|false|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "datatype": "string",
  "name": "string"
}
```

> 400 Response

```json
"string"
```

<h3 id="vdov1entitiespost-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[UniqueIdentifier](#schemauniqueidentifier)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|string|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="VDO-Information">Information</h1>

## InfoPingGet

<a id="opIdInfoPingGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/info/ping \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/info/ping HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/info/ping',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/info/ping',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/info/ping',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/info/ping', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/info/ping");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/info/ping", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/info/ping`

*Simple ping to see if API is alive*

<h3 id="vdov1infopingget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
"string"
```

```json
"string"
```

<h3 id="vdov1infopingget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|string|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<aside class="success">
This operation does not require authentication
</aside>

## InfoVersionGet

<a id="opIdInfoVersionGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/info/version \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/info/version HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/info/version',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/info/version',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/info/version',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/info/version', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/info/version");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/info/version", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/info/version`

*Version number and release date of VDO API*

<h3 id="vdov1infoversionget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
{
  "number": "string",
  "release_date": "2018-05-15T17:51:34Z",
  "lastRestartTime": "string",
  "redisDBNumber": "string",
  "environment": "string",
  "token_information": {
    "companyId": "string",
    "userId": "string",
    "auth0UserId": "string",
    "issuer": "string",
    "isUser": true,
    "userEmail": "string",
    "roles": [
      "string"
    ]
  }
}
```

```json
{
  "number": "string",
  "release_date": "2018-05-15T17:51:34Z",
  "lastRestartTime": "string",
  "redisDBNumber": "string",
  "environment": "string",
  "token_information": {
    "companyId": "string",
    "userId": "string",
    "auth0UserId": "string",
    "issuer": "string",
    "isUser": true,
    "userEmail": "string",
    "roles": [
      "string"
    ]
  }
}
```

<h3 id="vdov1infoversionget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ApplicationVersion](#schemaapplicationversion)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<aside class="success">
This operation does not require authentication
</aside>

## InfoVersionAdminGet

<a id="opIdInfoVersionAdminGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/info/version/admin \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/info/version/admin HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/info/version/admin',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/info/version/admin',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/info/version/admin',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/info/version/admin', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/info/version/admin");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/info/version/admin", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/info/version/admin`

*Version number and release date of VDO API*

<h3 id="vdov1infoversionadminget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
{
  "number": "string",
  "release_date": "2018-05-15T17:51:34Z",
  "lastRestartTime": "string",
  "redisDBNumber": "string",
  "environment": "string",
  "token_information": {
    "companyId": "string",
    "userId": "string",
    "auth0UserId": "string",
    "issuer": "string",
    "isUser": true,
    "userEmail": "string",
    "roles": [
      "string"
    ]
  }
}
```

```json
{
  "number": "string",
  "release_date": "2018-05-15T17:51:34Z",
  "lastRestartTime": "string",
  "redisDBNumber": "string",
  "environment": "string",
  "token_information": {
    "companyId": "string",
    "userId": "string",
    "auth0UserId": "string",
    "issuer": "string",
    "isUser": true,
    "userEmail": "string",
    "roles": [
      "string"
    ]
  }
}
```

<h3 id="vdov1infoversionadminget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ApplicationVersion](#schemaapplicationversion)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<aside class="success">
This operation does not require authentication
</aside>

## InfoClaimsGet

<a id="opIdInfoClaimsGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/info/claims \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/info/claims HTTP/1.1
Host: null

X-Api-Key: string

```

```javascript
var headers = {
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/info/claims',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'X-Api-Key':'string'

};

fetch('//vdo/v1/info/claims',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/info/claims',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/info/claims', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/info/claims");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/info/claims", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/info/claims`

<h3 id="vdov1infoclaimsget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|

<h3 id="vdov1infoclaimsget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|None|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="VDO-Job">Job</h1>

## JobsGet

<a id="opIdJobsGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/jobs \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/jobs HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/jobs',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/jobs',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/jobs',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/jobs', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/jobs");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/jobs", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/jobs`

<h3 id="vdov1jobsget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
[
  {
    "id": "string",
    "name": "string",
    "workflowcontnent": "string",
    "parameters": "string",
    "status": "string",
    "isarchived": true,
    "createdate": "2018-05-15T17:51:34Z",
    "updatedate": "2018-05-15T17:51:34Z",
    "workflowid": "string",
    "companyid": "string",
    "userid": "string",
    "ouputypename": "string",
    "ouputvalue": "string",
    "workFlow": {
      "id": "string",
      "name": "string",
      "workflowtemplateid": "string",
      "content": "string",
      "accesslevel": "string",
      "createdate": "2018-05-15T17:51:34Z",
      "version": 0,
      "ispublished": true,
      "companyid": "string"
    }
  }
]
```

```json
[
  {
    "id": "string",
    "name": "string",
    "workflowcontnent": "string",
    "parameters": "string",
    "status": "string",
    "isarchived": true,
    "createdate": "2018-05-15T17:51:34Z",
    "updatedate": "2018-05-15T17:51:34Z",
    "workflowid": "string",
    "companyid": "string",
    "userid": "string",
    "ouputypename": "string",
    "ouputvalue": "string",
    "workFlow": {
      "id": "string",
      "name": "string",
      "workflowtemplateid": "string",
      "content": "string",
      "accesslevel": "string",
      "createdate": "2018-05-15T17:51:34Z",
      "version": 0,
      "ispublished": true,
      "companyid": "string"
    }
  }
]
```

<h3 id="vdov1jobsget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<h3 id="vdov1jobsget-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Job](#schemajob)]|false|none|none|
|» id|string(uuid)|false|none|none|
|» name|string|false|none|none|
|» workflowcontnent|string|false|none|none|
|» parameters|string|false|none|none|
|» status|string|false|none|none|
|» isarchived|boolean|false|none|none|
|» createdate|string(date-time)|false|none|none|
|» updatedate|string(date-time)|false|none|none|
|» workflowid|string(uuid)|false|none|none|
|» companyid|string(uuid)|false|none|none|
|» userid|string(uuid)|false|none|none|
|» ouputypename|string|false|none|none|
|» ouputvalue|string|false|none|none|
|» workFlow|[WorkFlow](#schemaworkflow)|false|none|none|
|»» id|string(uuid)|false|none|none|
|»» name|string|false|none|none|
|»» workflowtemplateid|string(uuid)|false|none|none|
|»» content|string|false|none|none|
|»» accesslevel|string|false|none|none|
|»» createdate|string(date-time)|false|none|none|
|»» version|integer(int32)|false|none|none|
|»» ispublished|boolean|false|none|none|
|»» companyid|string(uuid)|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## JobsPost

<a id="opIdJobsPost"></a>

> Code samples

```shell
# You can also use wget
curl -X POST //vdo/v1/jobs \
  -H 'Content-Type: application/json-patch+json' \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
POST //vdo/v1/jobs HTTP/1.1
Host: null
Content-Type: application/json-patch+json
Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Content-Type':'application/json-patch+json',
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/jobs',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "workflowid": "string",
  "name": "string",
  "parameters": [
    {
      "id": "string",
      "value": "string"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json-patch+json',
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/jobs',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json-patch+json',
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.post '//vdo/v1/jobs',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json-patch+json',
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.post('//vdo/v1/jobs', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/jobs");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json-patch+json"},
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "//vdo/v1/jobs", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /vdo/v1/jobs`

> Body parameter

```json
{
  "workflowid": "string",
  "name": "string",
  "parameters": [
    {
      "id": "string",
      "value": "string"
    }
  ]
}
```

<h3 id="vdov1jobspost-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|
|body|body|[JobRequest](#schemajobrequest)|false|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "datatype": "string",
  "name": "string"
}
```

```json
{
  "id": "string",
  "datatype": "string",
  "name": "string"
}
```

> 400 Response

```json
"string"
```

```json
"string"
```

<h3 id="vdov1jobspost-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[UniqueIdentifier](#schemauniqueidentifier)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|string|

<aside class="success">
This operation does not require authentication
</aside>

## JobsByJobidGet

<a id="opIdJobsByJobidGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/jobs/{jobid} \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/jobs/{jobid} HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/jobs/{jobid}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/jobs/{jobid}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/jobs/{jobid}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/jobs/{jobid}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/jobs/{jobid}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/jobs/{jobid}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/jobs/{jobid}`

*Use to check on status of a job*

Check the status of a specific job as well as details of what assets/datasets where generated during the processing

<h3 id="vdov1jobsbyjobidget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|jobid|path|string(uuid)|true|none|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
{
  "job": {
    "id": "string",
    "name": "string",
    "inputvalues": [
      {
        "id": "string",
        "value": "string"
      }
    ],
    "status": "string",
    "createdate": "2018-05-15T17:51:34Z",
    "workflowid": "string",
    "ouputypename": "string",
    "ouputvalue": "string"
  },
  "steps": [
    {
      "id": "string",
      "jobid": "string",
      "iocounter": 0,
      "name": "string",
      "isinput": true,
      "value": "string",
      "type": "string",
      "status": "string",
      "stepid": "string"
    }
  ]
}
```

```json
{
  "job": {
    "id": "string",
    "name": "string",
    "inputvalues": [
      {
        "id": "string",
        "value": "string"
      }
    ],
    "status": "string",
    "createdate": "2018-05-15T17:51:34Z",
    "workflowid": "string",
    "ouputypename": "string",
    "ouputvalue": "string"
  },
  "steps": [
    {
      "id": "string",
      "jobid": "string",
      "iocounter": 0,
      "name": "string",
      "isinput": true,
      "value": "string",
      "type": "string",
      "status": "string",
      "stepid": "string"
    }
  ]
}
```

<h3 id="vdov1jobsbyjobidget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Job|[JobDetails](#schemajobdetails)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No Content: Job not found|None|

<aside class="success">
This operation does not require authentication
</aside>

## JobsByJobidWorkflowGet

<a id="opIdJobsByJobidWorkflowGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/jobs/{jobid}/workflow \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/jobs/{jobid}/workflow HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/jobs/{jobid}/workflow',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/jobs/{jobid}/workflow',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/jobs/{jobid}/workflow',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/jobs/{jobid}/workflow', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/jobs/{jobid}/workflow");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/jobs/{jobid}/workflow", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/jobs/{jobid}/workflow`

*Retrieves current list of job flow processing*

<h3 id="vdov1jobsbyjobidworkflowget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|jobid|path|string(uuid)|true|none|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "name": "string",
  "isservice": true,
  "iteratortype": 0,
  "inputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ],
  "children": [
    null
  ],
  "outputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ]
}
```

```json
{
  "id": "string",
  "name": "string",
  "isservice": true,
  "iteratortype": 0,
  "inputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ],
  "children": [
    null
  ],
  "outputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ]
}
```

<h3 id="vdov1jobsbyjobidworkflowget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[WorkFlowTemplateDTO](#schemaworkflowtemplatedto)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<aside class="success">
This operation does not require authentication
</aside>

## JobsByJobidProcessGet

<a id="opIdJobsByJobidProcessGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/jobs/{jobid}/process \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/jobs/{jobid}/process HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/jobs/{jobid}/process',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/jobs/{jobid}/process',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/jobs/{jobid}/process',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/jobs/{jobid}/process', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/jobs/{jobid}/process");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/jobs/{jobid}/process", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/jobs/{jobid}/process`

*Restart a Job process.  Rarely needed and only used when backend services go down and are restarted*

<h3 id="vdov1jobsbyjobidprocessget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|jobid|path|string(uuid)|true|none|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
true
```

```json
true
```

<h3 id="vdov1jobsbyjobidprocessget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|boolean|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<aside class="success">
This operation does not require authentication
</aside>

## JobsByJobidCompletePost

<a id="opIdJobsByJobidCompletePost"></a>

> Code samples

```shell
# You can also use wget
curl -X POST //vdo/v1/jobs/{jobid}/complete \
  -H 'Content-Type: application/json-patch+json' \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
POST //vdo/v1/jobs/{jobid}/complete HTTP/1.1
Host: null
Content-Type: application/json-patch+json
Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Content-Type':'application/json-patch+json',
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/jobs/{jobid}/complete',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "status": "string",
  "jobId": "string",
  "jobFlowId": "string",
  "dataType": "string",
  "dataId": "string"
}';
const headers = {
  'Content-Type':'application/json-patch+json',
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/jobs/{jobid}/complete',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json-patch+json',
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.post '//vdo/v1/jobs/{jobid}/complete',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json-patch+json',
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.post('//vdo/v1/jobs/{jobid}/complete', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/jobs/{jobid}/complete");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json-patch+json"},
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "//vdo/v1/jobs/{jobid}/complete", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /vdo/v1/jobs/{jobid}/complete`

*[POST] Used by microservices to notify api that a job task has been processed*

> Body parameter

```json
{
  "status": "string",
  "jobId": "string",
  "jobFlowId": "string",
  "dataType": "string",
  "dataId": "string"
}
```

<h3 id="vdov1jobsbyjobidcompletepost-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|jobid|path|string(uuid)|true|none|
|X-Api-Key|header|string|false|Your assigned application id|
|body|body|[TaskComplete](#schemataskcomplete)|false|none|

> Example responses

> 200 Response

```json
true
```

```json
true
```

<h3 id="vdov1jobsbyjobidcompletepost-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|boolean|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="VDO-PermissionTesting">PermissionTesting</h1>

## SecuritycheckNoneGet

<a id="opIdSecuritycheckNoneGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/securitycheck/none \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/securitycheck/none HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/securitycheck/none',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/securitycheck/none',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/securitycheck/none',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/securitycheck/none', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/securitycheck/none");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/securitycheck/none", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/securitycheck/none`

*No token required*

<h3 id="vdov1securitychecknoneget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
[
  "string"
]
```

```json
[
  "string"
]
```

<h3 id="vdov1securitychecknoneget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<h3 id="vdov1securitychecknoneget-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|

<aside class="success">
This operation does not require authentication
</aside>

## SecuritycheckReadGet

<a id="opIdSecuritycheckReadGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/securitycheck/read \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/securitycheck/read HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/securitycheck/read',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/securitycheck/read',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/securitycheck/read',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/securitycheck/read', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/securitycheck/read");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/securitycheck/read", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/securitycheck/read`

*Test Read level Permissions*

<h3 id="vdov1securitycheckreadget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
[
  "string"
]
```

```json
[
  "string"
]
```

<h3 id="vdov1securitycheckreadget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<h3 id="vdov1securitycheckreadget-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|

<aside class="success">
This operation does not require authentication
</aside>

## SecuritycheckWriteGet

<a id="opIdSecuritycheckWriteGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/securitycheck/write \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/securitycheck/write HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/securitycheck/write',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/securitycheck/write',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/securitycheck/write',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/securitycheck/write', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/securitycheck/write");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/securitycheck/write", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/securitycheck/write`

*Test Write Level Permissions*

<h3 id="vdov1securitycheckwriteget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
[
  "string"
]
```

```json
[
  "string"
]
```

<h3 id="vdov1securitycheckwriteget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<h3 id="vdov1securitycheckwriteget-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|

<aside class="success">
This operation does not require authentication
</aside>

## SecuritycheckReadwriteGet

<a id="opIdSecuritycheckReadwriteGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/securitycheck/readwrite \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/securitycheck/readwrite HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/securitycheck/readwrite',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/securitycheck/readwrite',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/securitycheck/readwrite',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/securitycheck/readwrite', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/securitycheck/readwrite");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/securitycheck/readwrite", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/securitycheck/readwrite`

*Test if you have both read and write permissions*

<h3 id="vdov1securitycheckreadwriteget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
[
  "string"
]
```

```json
[
  "string"
]
```

<h3 id="vdov1securitycheckreadwriteget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<h3 id="vdov1securitycheckreadwriteget-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|

<aside class="success">
This operation does not require authentication
</aside>

## SecuritycheckErrorGet

<a id="opIdSecuritycheckErrorGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/securitycheck/error \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/securitycheck/error HTTP/1.1
Host: null

X-Api-Key: string

```

```javascript
var headers = {
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/securitycheck/error',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'X-Api-Key':'string'

};

fetch('//vdo/v1/securitycheck/error',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/securitycheck/error',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/securitycheck/error', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/securitycheck/error");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/securitycheck/error", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/securitycheck/error`

<h3 id="vdov1securitycheckerrorget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|

<h3 id="vdov1securitycheckerrorget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|None|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="VDO-Storage">Storage</h1>

## StorageAssetsGet

<a id="opIdStorageAssetsGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/storage/assets \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/storage/assets HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/storage/assets',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/storage/assets',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/storage/assets',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/storage/assets', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/storage/assets");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/storage/assets", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/storage/assets`

*List of all the assets/files you have uploaded to Vettd.*

<h3 id="vdov1storageassetsget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
[
  {
    "id": "string",
    "createdate": "2018-05-15T17:51:34Z",
    "updatedate": "2018-05-15T17:51:34Z",
    "datatype": "string",
    "name": "string"
  }
]
```

```json
[
  {
    "id": "string",
    "createdate": "2018-05-15T17:51:34Z",
    "updatedate": "2018-05-15T17:51:34Z",
    "datatype": "string",
    "name": "string"
  }
]
```

<h3 id="vdov1storageassetsget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<h3 id="vdov1storageassetsget-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[AssetDTO](#schemaassetdto)]|false|none|none|
|» id|string(uuid)|false|none|none|
|» createdate|string(date-time)|false|none|none|
|» updatedate|string(date-time)|false|none|none|
|» datatype|string|false|none|none|
|» name|string|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## StorageAssetsPost

<a id="opIdStorageAssetsPost"></a>

> Code samples

```shell
# You can also use wget
curl -X POST //vdo/v1/storage/assets?assigntodataset=true \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
POST //vdo/v1/storage/assets?assigntodataset=true HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/storage/assets',
  method: 'post',
  data: '?assigntodataset=true',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/storage/assets?assigntodataset=true',
{
  method: 'POST',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.post '//vdo/v1/storage/assets',
  params: {
  'assigntodataset' => 'boolean'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.post('//vdo/v1/storage/assets', params={
  'assigntodataset': 'true'
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/storage/assets?assigntodataset=true");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "//vdo/v1/storage/assets", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /vdo/v1/storage/assets`

*Send assets/files into a DataSet 
Content-Type: application/x-www-form-urlencoded.
Zip files are allowed and will be unzipped on upload*

<h3 id="vdov1storageassetspost-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|files|query|array[any]|false|Except ZIP or single files (txt, doc, docx, json, pdf)|
|datatype|query|string|false|Eg. 'JobDescription' or 'Applicant'|
|datasetname|query|string|false|Optional: Give the name of your DataSet a friendly name - one will be generated if blank|
|assigntodataset|query|boolean|true|Optional: [Default to true] Usually an asset will be assigned to a dataset - set flag to false to supress connection|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
{
  "datasetid": "string",
  "datasetname": "string",
  "assets": [
    {
      "id": "string",
      "createdate": "2018-05-15T17:51:34Z",
      "updatedate": "2018-05-15T17:51:34Z",
      "datatype": "string",
      "name": "string"
    }
  ]
}
```

```json
{
  "datasetid": "string",
  "datasetname": "string",
  "assets": [
    {
      "id": "string",
      "createdate": "2018-05-15T17:51:34Z",
      "updatedate": "2018-05-15T17:51:34Z",
      "datatype": "string",
      "name": "string"
    }
  ]
}
```

<h3 id="vdov1storageassetspost-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AssetUploadResponse](#schemaassetuploadresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<aside class="success">
This operation does not require authentication
</aside>

## StorageAssetsByAssetidGet

<a id="opIdStorageAssetsByAssetidGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/storage/assets/{assetid} \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/storage/assets/{assetid} HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/storage/assets/{assetid}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/storage/assets/{assetid}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/storage/assets/{assetid}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/storage/assets/{assetid}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/storage/assets/{assetid}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/storage/assets/{assetid}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/storage/assets/{assetid}`

*Get Asset details by Id*

<h3 id="vdov1storageassetsbyassetidget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|assetid|path|string(uuid)|true|none|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "createdate": "2018-05-15T17:51:34Z",
  "updatedate": "2018-05-15T17:51:34Z",
  "datatype": "string",
  "name": "string"
}
```

```json
{
  "id": "string",
  "createdate": "2018-05-15T17:51:34Z",
  "updatedate": "2018-05-15T17:51:34Z",
  "datatype": "string",
  "name": "string"
}
```

<h3 id="vdov1storageassetsbyassetidget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AssetDTO](#schemaassetdto)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<aside class="success">
This operation does not require authentication
</aside>

## StorageDatasetsGet

<a id="opIdStorageDatasetsGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/storage/datasets \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/storage/datasets HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/storage/datasets',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/storage/datasets',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/storage/datasets',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/storage/datasets', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/storage/datasets");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/storage/datasets", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/storage/datasets`

*Returns list of all datasets*

<h3 id="vdov1storagedatasetsget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
[
  {
    "id": "string",
    "createdate": "2018-05-15T17:51:34Z",
    "name": "string",
    "datatype": "string"
  }
]
```

```json
[
  {
    "id": "string",
    "createdate": "2018-05-15T17:51:34Z",
    "name": "string",
    "datatype": "string"
  }
]
```

<h3 id="vdov1storagedatasetsget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<h3 id="vdov1storagedatasetsget-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[DataSetDTO](#schemadatasetdto)]|false|none|none|
|» id|string(uuid)|false|none|none|
|» createdate|string(date-time)|false|none|none|
|» name|string|false|none|none|
|» datatype|string|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## StorageDatasetsPost

<a id="opIdStorageDatasetsPost"></a>

> Code samples

```shell
# You can also use wget
curl -X POST //vdo/v1/storage/datasets \
  -H 'Content-Type: application/json-patch+json' \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
POST //vdo/v1/storage/datasets HTTP/1.1
Host: null
Content-Type: application/json-patch+json
Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Content-Type':'application/json-patch+json',
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/storage/datasets',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "name": "string",
  "datatype": "string"
}';
const headers = {
  'Content-Type':'application/json-patch+json',
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/storage/datasets',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json-patch+json',
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.post '//vdo/v1/storage/datasets',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json-patch+json',
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.post('//vdo/v1/storage/datasets', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/storage/datasets");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json-patch+json"},
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "//vdo/v1/storage/datasets", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /vdo/v1/storage/datasets`

*Create an empty dataset for future use of adding assets into it*

> Body parameter

```json
{
  "name": "string",
  "datatype": "string"
}
```

<h3 id="vdov1storagedatasetspost-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|
|body|body|[DataSetCreateRequest](#schemadatasetcreaterequest)|false|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "datatype": "string",
  "name": "string"
}
```

```json
{
  "id": "string",
  "datatype": "string",
  "name": "string"
}
```

<h3 id="vdov1storagedatasetspost-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Unique identifier for dataset|[UniqueIdentifier](#schemauniqueidentifier)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Error: Dataset not created|None|

<aside class="success">
This operation does not require authentication
</aside>

## StorageDatasetsByDatasetidAssetsGet

<a id="opIdStorageDatasetsByDatasetidAssetsGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/storage/datasets/{datasetid}/assets \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/storage/datasets/{datasetid}/assets HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/storage/datasets/{datasetid}/assets',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/storage/datasets/{datasetid}/assets',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/storage/datasets/{datasetid}/assets',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/storage/datasets/{datasetid}/assets', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/storage/datasets/{datasetid}/assets");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/storage/datasets/{datasetid}/assets", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/storage/datasets/{datasetid}/assets`

*Return Assets associatted with a DataSet*

<h3 id="vdov1storagedatasetsbydatasetidassetsget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|datasetid|path|string(uuid)|true|none|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
[
  {
    "id": "string",
    "createdate": "2018-05-15T17:51:34Z",
    "updatedate": "2018-05-15T17:51:34Z",
    "datatype": "string",
    "name": "string"
  }
]
```

```json
[
  {
    "id": "string",
    "createdate": "2018-05-15T17:51:34Z",
    "updatedate": "2018-05-15T17:51:34Z",
    "datatype": "string",
    "name": "string"
  }
]
```

<h3 id="vdov1storagedatasetsbydatasetidassetsget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<h3 id="vdov1storagedatasetsbydatasetidassetsget-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[AssetDTO](#schemaassetdto)]|false|none|none|
|» id|string(uuid)|false|none|none|
|» createdate|string(date-time)|false|none|none|
|» updatedate|string(date-time)|false|none|none|
|» datatype|string|false|none|none|
|» name|string|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="VDO-User">User</h1>

## UsersPost

<a id="opIdUsersPost"></a>

> Code samples

```shell
# You can also use wget
curl -X POST //vdo/v1/users \
  -H 'Content-Type: application/json-patch+json' \
  -H 'Accept: application/json' \
  -H 'X-Api-Key: string'

```

```http
POST //vdo/v1/users HTTP/1.1
Host: null
Content-Type: application/json-patch+json
Accept: application/json
X-Api-Key: string

```

```javascript
var headers = {
  'Content-Type':'application/json-patch+json',
  'Accept':'application/json',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/users',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "thirdpartyid": "string",
  "companyname": "string",
  "username": "string",
  "email": "string",
  "workflowids": [
    "string"
  ]
}';
const headers = {
  'Content-Type':'application/json-patch+json',
  'Accept':'application/json',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/users',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json-patch+json',
  'Accept' => 'application/json',
  'X-Api-Key' => 'string'
}

result = RestClient.post '//vdo/v1/users',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json-patch+json',
  'Accept': 'application/json',
  'X-Api-Key': 'string'
}

r = requests.post('//vdo/v1/users', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/users");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json-patch+json"},
        "Accept": []string{"application/json"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "//vdo/v1/users", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /vdo/v1/users`

> Body parameter

```json
{
  "thirdpartyid": "string",
  "companyname": "string",
  "username": "string",
  "email": "string",
  "workflowids": [
    "string"
  ]
}
```

<h3 id="vdov1userspost-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|
|body|body|[ClientAsUser](#schemaclientasuser)|false|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "datatype": "string",
  "name": "string"
}
```

> 400 Response

```json
"string"
```

<h3 id="vdov1userspost-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[UniqueIdentifier](#schemauniqueidentifier)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|string|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="VDO-WorkFlow">WorkFlow</h1>

## WorkflowGet

<a id="opIdWorkflowGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/workflow \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/workflow HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/workflow',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/workflow',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/workflow',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/workflow', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/workflow");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/workflow", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/workflow`

<h3 id="vdov1workflowget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
[
  {
    "id": "string",
    "name": "string",
    "workflow": {},
    "version": 0
  }
]
```

```json
[
  {
    "id": "string",
    "name": "string",
    "workflow": {},
    "version": 0
  }
]
```

<h3 id="vdov1workflowget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<h3 id="vdov1workflowget-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[WorkFlowDTO](#schemaworkflowdto)]|false|none|none|
|» id|string(uuid)|false|none|none|
|» name|string|false|none|none|
|» workflow|object|false|read-only|none|
|» version|integer(int32)|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## WorkflowByWorkflowidGet

<a id="opIdWorkflowByWorkflowidGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/workflow/{workflowid} \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/workflow/{workflowid} HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/workflow/{workflowid}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/workflow/{workflowid}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/workflow/{workflowid}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/workflow/{workflowid}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/workflow/{workflowid}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/workflow/{workflowid}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/workflow/{workflowid}`

<h3 id="vdov1workflowbyworkflowidget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|workflowid|path|string(uuid)|true|none|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "name": "string",
  "isservice": true,
  "iteratortype": 0,
  "inputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ],
  "children": [
    null
  ],
  "outputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ]
}
```

```json
{
  "id": "string",
  "name": "string",
  "isservice": true,
  "iteratortype": 0,
  "inputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ],
  "children": [
    null
  ],
  "outputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ]
}
```

<h3 id="vdov1workflowbyworkflowidget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[WorkFlowTemplateDTO](#schemaworkflowtemplatedto)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<aside class="success">
This operation does not require authentication
</aside>

## WorkflowByWorkflowidContentGet

<a id="opIdWorkflowByWorkflowidContentGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/workflow/{workflowid}/content \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/workflow/{workflowid}/content HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/workflow/{workflowid}/content',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/workflow/{workflowid}/content',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/workflow/{workflowid}/content',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/workflow/{workflowid}/content', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/workflow/{workflowid}/content");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/workflow/{workflowid}/content", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/workflow/{workflowid}/content`

<h3 id="vdov1workflowbyworkflowidcontentget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|workflowid|path|string(uuid)|true|none|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "name": "string",
  "isservice": true,
  "iteratortype": 0,
  "inputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ],
  "children": [
    null
  ],
  "outputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ]
}
```

```json
{
  "id": "string",
  "name": "string",
  "isservice": true,
  "iteratortype": 0,
  "inputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ],
  "children": [
    null
  ],
  "outputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ]
}
```

<h3 id="vdov1workflowbyworkflowidcontentget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[WorkFlowTemplateDTO](#schemaworkflowtemplatedto)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="VDO-WorkFlowTemplate">WorkFlowTemplate</h1>

## TemplatesGet

<a id="opIdTemplatesGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/templates \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/templates HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/templates',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/templates',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/templates',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/templates', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/templates");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/templates", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/templates`

<h3 id="vdov1templatesget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
[
  {
    "id": "string",
    "name": "string",
    "isservice": true,
    "iteratortype": 0,
    "inputs": [
      {
        "id": "string",
        "name": "string",
        "typename": "string",
        "iocounter": 0
      }
    ],
    "children": [
      null
    ],
    "outputs": [
      {
        "id": "string",
        "name": "string",
        "typename": "string",
        "iocounter": 0
      }
    ]
  }
]
```

```json
[
  {
    "id": "string",
    "name": "string",
    "isservice": true,
    "iteratortype": 0,
    "inputs": [
      {
        "id": "string",
        "name": "string",
        "typename": "string",
        "iocounter": 0
      }
    ],
    "children": [
      null
    ],
    "outputs": [
      {
        "id": "string",
        "name": "string",
        "typename": "string",
        "iocounter": 0
      }
    ]
  }
]
```

<h3 id="vdov1templatesget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<h3 id="vdov1templatesget-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[WorkFlowTemplateDTO](#schemaworkflowtemplatedto)]|false|none|none|
|» id|string(uuid)|false|none|none|
|» name|string|false|none|none|
|» isservice|boolean|false|none|none|
|» iteratortype|integer(int32)|false|none|none|
|» inputs|[[WorkFlowIODTO](#schemaworkflowiodto)]|false|none|none|
|»» id|string(uuid)|false|none|none|
|»» name|string|false|none|none|
|»» typename|string|false|none|none|
|»» iocounter|integer(int32)|false|none|none|
|» children|[[WorkFlowTemplateDTO](#schemaworkflowtemplatedto)]|false|none|none|
|» outputs|[[WorkFlowIODTO](#schemaworkflowiodto)]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|iteratortype|0|
|iteratortype|1|
|iteratortype|2|

<aside class="success">
This operation does not require authentication
</aside>

## TemplatesByWorkflowtemplateidGet

<a id="opIdTemplatesByWorkflowtemplateidGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/templates/{workflowtemplateid} \
  -H 'Accept: text/plain' \
  -H 'X-Api-Key: string'

```

```http
GET //vdo/v1/templates/{workflowtemplateid} HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string

```

```javascript
var headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

$.ajax({
  url: '//vdo/v1/templates/{workflowtemplateid}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/plain',
  'X-Api-Key':'string'

};

fetch('//vdo/v1/templates/{workflowtemplateid}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain',
  'X-Api-Key' => 'string'
}

result = RestClient.get '//vdo/v1/templates/{workflowtemplateid}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain',
  'X-Api-Key': 'string'
}

r = requests.get('//vdo/v1/templates/{workflowtemplateid}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("//vdo/v1/templates/{workflowtemplateid}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        "X-Api-Key": []string{"string"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "//vdo/v1/templates/{workflowtemplateid}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /vdo/v1/templates/{workflowtemplateid}`

<h3 id="vdov1templatesbyworkflowtemplateidget-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|workflowtemplateid|path|string(uuid)|true|none|
|X-Api-Key|header|string|false|Your assigned application id|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "name": "string",
  "isservice": true,
  "iteratortype": 0,
  "inputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ],
  "children": [
    null
  ],
  "outputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ]
}
```

```json
{
  "id": "string",
  "name": "string",
  "isservice": true,
  "iteratortype": 0,
  "inputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ],
  "children": [
    null
  ],
  "outputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ]
}
```

<h3 id="vdov1templatesbyworkflowtemplateidget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[WorkFlowTemplateDTO](#schemaworkflowtemplatedto)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

<h2 id="tocSfileresult">FileResult</h2>

<a id="schemafileresult"></a>

```json
{
  "contentType": "string",
  "fileDownloadName": "string",
  "lastModified": "2018-05-15T17:51:34Z",
  "entityTag": {
    "tag": {
      "buffer": "string",
      "offset": 0,
      "length": 0,
      "value": "string",
      "hasValue": true
    },
    "isWeak": true
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|contentType|string|false|read-only|none|
|fileDownloadName|string|false|none|none|
|lastModified|string(date-time)|false|none|none|
|entityTag|[EntityTagHeaderValue](#schemaentitytagheadervalue)|false|none|none|

<h2 id="tocSentitytagheadervalue">EntityTagHeaderValue</h2>

<a id="schemaentitytagheadervalue"></a>

```json
{
  "tag": {
    "buffer": "string",
    "offset": 0,
    "length": 0,
    "value": "string",
    "hasValue": true
  },
  "isWeak": true
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|tag|[StringSegment](#schemastringsegment)|false|none|none|
|isWeak|boolean|false|read-only|none|

<h2 id="tocSstringsegment">StringSegment</h2>

<a id="schemastringsegment"></a>

```json
{
  "buffer": "string",
  "offset": 0,
  "length": 0,
  "value": "string",
  "hasValue": true
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|buffer|string|false|read-only|none|
|offset|integer(int32)|false|read-only|none|
|length|integer(int32)|false|read-only|none|
|value|string|false|read-only|none|
|hasValue|boolean|false|read-only|none|

<h2 id="tocSentitydatasaverequest">EntityDataSaveRequest</h2>

<a id="schemaentitydatasaverequest"></a>

```json
{
  "uniqueid": "string",
  "source": "string",
  "entity": {
    "data": "string",
    "type": "string"
  },
  "entityasset": {
    "data": "string",
    "type": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|uniqueid|string(uuid)|false|none|none|
|source|string|false|none|none|
|entity|[EntityData](#schemaentitydata)|false|none|none|
|entityasset|[EntityData](#schemaentitydata)|false|none|none|

<h2 id="tocSentitydata">EntityData</h2>

<a id="schemaentitydata"></a>

```json
{
  "data": "string",
  "type": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|string|false|none|none|
|type|string|false|none|none|

<h2 id="tocSuniqueidentifier">UniqueIdentifier</h2>

<a id="schemauniqueidentifier"></a>

```json
{
  "id": "string",
  "datatype": "string",
  "name": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|false|none|none|
|datatype|string|false|none|none|
|name|string|false|none|none|

<h2 id="tocSentityresponse">EntityResponse</h2>

<a id="schemaentityresponse"></a>

```json
{
  "enitityId": "string",
  "source": "string",
  "sourceId": "string",
  "type": "string",
  "object": {},
  "createDate": "2018-05-15T17:51:34Z",
  "entityAssets": [
    {
      "enitityAssetId": "string",
      "assetId": "string",
      "type": "string",
      "object": {},
      "createDate": "2018-05-15T17:51:34Z"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|enitityId|string(uuid)|false|none|none|
|source|string|false|none|none|
|sourceId|string(uuid)|false|none|none|
|type|string|false|none|none|
|object|object|false|none|none|
|createDate|string(date-time)|false|none|none|
|entityAssets|[[EntityAssetResponse](#schemaentityassetresponse)]|false|none|none|

<h2 id="tocSentityassetresponse">EntityAssetResponse</h2>

<a id="schemaentityassetresponse"></a>

```json
{
  "enitityAssetId": "string",
  "assetId": "string",
  "type": "string",
  "object": {},
  "createDate": "2018-05-15T17:51:34Z"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|enitityAssetId|string(uuid)|false|none|none|
|assetId|string(uuid)|false|none|none|
|type|string|false|none|none|
|object|object|false|none|none|
|createDate|string(date-time)|false|none|none|

<h2 id="tocSapplicationversion">ApplicationVersion</h2>

<a id="schemaapplicationversion"></a>

```json
{
  "number": "string",
  "release_date": "2018-05-15T17:51:34Z",
  "lastRestartTime": "string",
  "redisDBNumber": "string",
  "environment": "string",
  "token_information": {
    "companyId": "string",
    "userId": "string",
    "auth0UserId": "string",
    "issuer": "string",
    "isUser": true,
    "userEmail": "string",
    "roles": [
      "string"
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|number|string|false|none|none|
|release_date|string(date-time)|false|none|none|
|lastRestartTime|string|false|none|none|
|redisDBNumber|string|false|none|none|
|environment|string|false|none|none|
|token_information|[TokenInformation](#schematokeninformation)|false|none|none|

<h2 id="tocStokeninformation">TokenInformation</h2>

<a id="schematokeninformation"></a>

```json
{
  "companyId": "string",
  "userId": "string",
  "auth0UserId": "string",
  "issuer": "string",
  "isUser": true,
  "userEmail": "string",
  "roles": [
    "string"
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|companyId|string(uuid)|false|none|none|
|userId|string(uuid)|false|none|none|
|auth0UserId|string|false|none|none|
|issuer|string|false|none|none|
|isUser|boolean|false|none|none|
|userEmail|string|false|none|none|
|roles|[string]|false|none|none|

<h2 id="tocSjobrequest">JobRequest</h2>

<a id="schemajobrequest"></a>

```json
{
  "workflowid": "string",
  "name": "string",
  "parameters": [
    {
      "id": "string",
      "value": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|workflowid|string(uuid)|false|none|none|
|name|string|false|none|none|
|parameters|[[JobParameter](#schemajobparameter)]|false|none|none|

<h2 id="tocSjobparameter">JobParameter</h2>

<a id="schemajobparameter"></a>

```json
{
  "id": "string",
  "value": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|false|none|none|
|value|string|false|none|none|

<h2 id="tocSjob">Job</h2>

<a id="schemajob"></a>

```json
{
  "id": "string",
  "name": "string",
  "workflowcontnent": "string",
  "parameters": "string",
  "status": "string",
  "isarchived": true,
  "createdate": "2018-05-15T17:51:34Z",
  "updatedate": "2018-05-15T17:51:34Z",
  "workflowid": "string",
  "companyid": "string",
  "userid": "string",
  "ouputypename": "string",
  "ouputvalue": "string",
  "workFlow": {
    "id": "string",
    "name": "string",
    "workflowtemplateid": "string",
    "content": "string",
    "accesslevel": "string",
    "createdate": "2018-05-15T17:51:34Z",
    "version": 0,
    "ispublished": true,
    "companyid": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|false|none|none|
|name|string|false|none|none|
|workflowcontnent|string|false|none|none|
|parameters|string|false|none|none|
|status|string|false|none|none|
|isarchived|boolean|false|none|none|
|createdate|string(date-time)|false|none|none|
|updatedate|string(date-time)|false|none|none|
|workflowid|string(uuid)|false|none|none|
|companyid|string(uuid)|false|none|none|
|userid|string(uuid)|false|none|none|
|ouputypename|string|false|none|none|
|ouputvalue|string|false|none|none|
|workFlow|[WorkFlow](#schemaworkflow)|false|none|none|

<h2 id="tocSworkflow">WorkFlow</h2>

<a id="schemaworkflow"></a>

```json
{
  "id": "string",
  "name": "string",
  "workflowtemplateid": "string",
  "content": "string",
  "accesslevel": "string",
  "createdate": "2018-05-15T17:51:34Z",
  "version": 0,
  "ispublished": true,
  "companyid": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|false|none|none|
|name|string|false|none|none|
|workflowtemplateid|string(uuid)|false|none|none|
|content|string|false|none|none|
|accesslevel|string|false|none|none|
|createdate|string(date-time)|false|none|none|
|version|integer(int32)|false|none|none|
|ispublished|boolean|false|none|none|
|companyid|string(uuid)|false|none|none|

<h2 id="tocSjobdetails">JobDetails</h2>

<a id="schemajobdetails"></a>

```json
{
  "job": {
    "id": "string",
    "name": "string",
    "inputvalues": [
      {
        "id": "string",
        "value": "string"
      }
    ],
    "status": "string",
    "createdate": "2018-05-15T17:51:34Z",
    "workflowid": "string",
    "ouputypename": "string",
    "ouputvalue": "string"
  },
  "steps": [
    {
      "id": "string",
      "jobid": "string",
      "iocounter": 0,
      "name": "string",
      "isinput": true,
      "value": "string",
      "type": "string",
      "status": "string",
      "stepid": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|job|[JobDTO](#schemajobdto)|false|none|none|
|steps|[[JobFlowDTO](#schemajobflowdto)]|false|none|none|

<h2 id="tocSjobdto">JobDTO</h2>

<a id="schemajobdto"></a>

```json
{
  "id": "string",
  "name": "string",
  "inputvalues": [
    {
      "id": "string",
      "value": "string"
    }
  ],
  "status": "string",
  "createdate": "2018-05-15T17:51:34Z",
  "workflowid": "string",
  "ouputypename": "string",
  "ouputvalue": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|false|none|none|
|name|string|false|none|none|
|inputvalues|[[JobParameter](#schemajobparameter)]|false|read-only|none|
|status|string|false|none|none|
|createdate|string(date-time)|false|none|none|
|workflowid|string(uuid)|false|none|none|
|ouputypename|string|false|none|none|
|ouputvalue|string|false|none|none|

<h2 id="tocSjobflowdto">JobFlowDTO</h2>

<a id="schemajobflowdto"></a>

```json
{
  "id": "string",
  "jobid": "string",
  "iocounter": 0,
  "name": "string",
  "isinput": true,
  "value": "string",
  "type": "string",
  "status": "string",
  "stepid": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|false|none|none|
|jobid|string(uuid)|false|none|none|
|iocounter|number(double)|false|none|none|
|name|string|false|none|none|
|isinput|boolean|false|none|none|
|value|string|false|none|none|
|type|string|false|none|none|
|status|string|false|none|none|
|stepid|string(uuid)|false|none|none|

<h2 id="tocSworkflowtemplatedto">WorkFlowTemplateDTO</h2>

<a id="schemaworkflowtemplatedto"></a>

```json
{
  "id": "string",
  "name": "string",
  "isservice": true,
  "iteratortype": 0,
  "inputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ],
  "children": [
    null
  ],
  "outputs": [
    {
      "id": "string",
      "name": "string",
      "typename": "string",
      "iocounter": 0
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|false|none|none|
|name|string|false|none|none|
|isservice|boolean|false|none|none|
|iteratortype|integer(int32)|false|none|none|
|inputs|[[WorkFlowIODTO](#schemaworkflowiodto)]|false|none|none|
|children|[[WorkFlowTemplateDTO](#schemaworkflowtemplatedto)]|false|none|none|
|outputs|[[WorkFlowIODTO](#schemaworkflowiodto)]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|iteratortype|0|
|iteratortype|1|
|iteratortype|2|

<h2 id="tocSworkflowiodto">WorkFlowIODTO</h2>

<a id="schemaworkflowiodto"></a>

```json
{
  "id": "string",
  "name": "string",
  "typename": "string",
  "iocounter": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|false|none|none|
|name|string|false|none|none|
|typename|string|false|none|none|
|iocounter|integer(int32)|false|none|none|

<h2 id="tocStaskcomplete">TaskComplete</h2>

<a id="schemataskcomplete"></a>

```json
{
  "status": "string",
  "jobId": "string",
  "jobFlowId": "string",
  "dataType": "string",
  "dataId": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|status|string|false|none|none|
|jobId|string(uuid)|false|none|none|
|jobFlowId|string(uuid)|false|none|none|
|dataType|string|false|none|none|
|dataId|string|false|none|none|

<h2 id="tocSassetdto">AssetDTO</h2>

<a id="schemaassetdto"></a>

```json
{
  "id": "string",
  "createdate": "2018-05-15T17:51:34Z",
  "updatedate": "2018-05-15T17:51:34Z",
  "datatype": "string",
  "name": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|false|none|none|
|createdate|string(date-time)|false|none|none|
|updatedate|string(date-time)|false|none|none|
|datatype|string|false|none|none|
|name|string|false|none|none|

<h2 id="tocSiformfile">IFormFile</h2>

<a id="schemaiformfile"></a>

```json
{
  "contentType": "string",
  "contentDisposition": "string",
  "headers": {
    "property1": [
      "string"
    ],
    "property2": [
      "string"
    ]
  },
  "length": 0,
  "name": "string",
  "fileName": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|contentType|string|false|read-only|none|
|contentDisposition|string|false|read-only|none|
|headers|object|false|read-only|none|
|» **additionalProperties**|[string]|false|none|none|
|length|integer(int64)|false|read-only|none|
|name|string|false|read-only|none|
|fileName|string|false|read-only|none|

<h2 id="tocSassetuploadresponse">AssetUploadResponse</h2>

<a id="schemaassetuploadresponse"></a>

```json
{
  "datasetid": "string",
  "datasetname": "string",
  "assets": [
    {
      "id": "string",
      "createdate": "2018-05-15T17:51:34Z",
      "updatedate": "2018-05-15T17:51:34Z",
      "datatype": "string",
      "name": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|datasetid|string(uuid)|false|none|none|
|datasetname|string|false|none|none|
|assets|[[AssetDTO](#schemaassetdto)]|false|none|none|

<h2 id="tocSdatasetdto">DataSetDTO</h2>

<a id="schemadatasetdto"></a>

```json
{
  "id": "string",
  "createdate": "2018-05-15T17:51:34Z",
  "name": "string",
  "datatype": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|false|none|none|
|createdate|string(date-time)|false|none|none|
|name|string|false|none|none|
|datatype|string|false|none|none|

<h2 id="tocSdatasetcreaterequest">DataSetCreateRequest</h2>

<a id="schemadatasetcreaterequest"></a>

```json
{
  "name": "string",
  "datatype": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|false|none|none|
|datatype|string|false|none|none|

<h2 id="tocSclientasuser">ClientAsUser</h2>

<a id="schemaclientasuser"></a>

```json
{
  "thirdpartyid": "string",
  "companyname": "string",
  "username": "string",
  "email": "string",
  "workflowids": [
    "string"
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|thirdpartyid|string|false|none|none|
|companyname|string|false|none|none|
|username|string|false|none|none|
|email|string|false|none|none|
|workflowids|[string]|false|none|none|

<h2 id="tocSworkflowdto">WorkFlowDTO</h2>

<a id="schemaworkflowdto"></a>

```json
{
  "id": "string",
  "name": "string",
  "workflow": {},
  "version": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|false|none|none|
|name|string|false|none|none|
|workflow|object|false|read-only|none|
|version|integer(int32)|false|none|none|

