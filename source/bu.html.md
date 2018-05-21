
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



<h1 id="Vettd-Data-Observatory-VDO-API-Documentation">Vettd Data Observatory VDO API Documentation v0.9.0.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Vettd Data Observatory API allows clients to utilize Vettd's services to do some cool Data Science processing.

NOTE: Most calls require the Authorization to be set above. Status Code 401 means you are not logged in while 403 means you are logged in but just do not have permissions to perform the action.

Base URLs: <a href="/">/</a>

# Onboarding
You will need six values issued to you by Vettd to begin working with the API. Those values are below with different values to access our TEST and PRODUCTION environments:

|Value|Description|
|---|---|
|Client Id	|Your unique Id|
|Client Secret	|Your unique secret/password|
API Key	A value passed into every call (except authentication) as second factor of authentication
NOTE: The client secret and API Key can be reset on demand when needed by contacting Vettd.

The above information should be treated like you would treat a username and password. 
We can also lock down the access even further if you provide a while list of valid IPs that will be allowed to access the VDO API.  This list can be as a range and/or single IPs.

# High Level API Concepts
|Value|Definition|
|---|---|
|Asset|A physical file.|
|Dataset|A reference to 1 or more assets.|
|Workflow|A series of 1 or more tasks to perform. Workflows can call other workflows (building complex series of tasks)|
|Job|An instance of workflow.  When you tell the API to do perform some workflow it creates a JobId which is used to check on the status of the job and retrieve the output (an asset or a dataset) of what the job produced.| 

### :ballot_box_with_check: Concept 1: What is data

The system was built to be able to handle a variety of incoming data types (text files, pdfs, word docs, etc.…).  These files are saved as assets and often time converted down to text for further processing.  Each step that is taken during this processing will produce either an Asset or a Dataset (a group of assets) for easy review.

### :ballot_box_with_check: Concept 2: What is a Workflow

Workflows are just a series of steps you are asking our system to perform. You don’t care that the work is broken down into X number of steps, all that you need to be concerned about is that you ask it to perform a high-level task by giving in a reference to some input data and as the result it produces some output data. In the background workflows can reference other workflows so you can build very complex processing, but still the consuming user only cares about the input and the output.  Vettd will work with you and create custom workflows for your company, then all you need to do is call and consume the results

### :ballot_box_with_check: Concept 3: What is a Job

A job is just an instance of workflow in action. This allows you to call a workflow multiple times and still keep track of each individual job. We keep track of the instance by a Job Id.  The time it takes to process the job depends on the complexity of the workflow and the volume of data the tasks have to process.


# Example: Basic Usage  Steps

![sampe steps](source/images/samplesteps.png)


|Step|Name|Call :link:|
|---|---|---|
|1|Authenticate| <a href="#auth-call">Jump to Call</a>|
|2|List Workflows| <a href="#list-avaliable-workflows">Jump to Call</a>|
|3|Upload Files| <a href="#upload-files--assets-and-datasets-">Jump to Call</a>|
|4|Call Workflow/ Add Job| <a href="#add-job">Jump to Call</a>|
|5|Retrieve Job Results| <a href="#get-job">Jump to Call</a>|
|6|Download Results| <a href="#download-asset">Jump to Call Asset</a> or <a href="#download-dataset">Jump to Call Dataset</a>|



![sampe steps](source/images/pdf.png)
[Download New User Getting Started Guide - PDF](source/docs/VDO_API_NEW_User_Guide.pdf)

The above guide will walk you through a basic creation of job using a workflow and files you upload.



# Authentication

The VDO API is JSON based. In order to make an authenticated call to the API, you must include your access token with the call. OAuth2 uses a BEARER token that is passed along in an Authorization header.

To get a token make the following call:

## Authenticate

> Code samples

```shell
# You can also use wget
curl -X POST https://vettd.auth0.com/oauth/token \
  -H 'Cache-Control: no-cache'
  -H 'Content-Type: application/x-www-form-urlencoded'
  -d 'grant_type=client_credentials&audience=api.vettd.com%2Fvdo&client_id={CLIENT_ID_HERE}&client_secret={CLIENT_SECRET_HERE}

```

`POST https://vettd.auth0.com/oauth/token`

> Example responses

> 200 Response

```json
{
    "access_token": "eyJ0eXAiO…DhgE-Q3-cycw",
    "scope": "",
    "expires_in": 14400,
    "token_type": "Bearer"
}

```

<h3 id="vdov1storagedatasetsbydatasetiddownloadget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AuthenicationResponse](#schemaauthenticate)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|



# Storage

## Upload Files - Assets and Datasets

<a id="opIdVdoV1StorageAssetsPost"></a>

> Code samples

```shell
# You can also use wget
curl -X POST //vdo/v1/storage/assets?assigntodataset=true \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
POST //vdo/v1/storage/assets?assigntodataset=true HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

<!--<aside class="success">
This operation does not require authentication
</aside>-->

## Single Asset

<a id="opIdVdoV1StorageAssetsByAssetidGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/storage/assets/{assetid} \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
GET //vdo/v1/storage/assets/{assetid} HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

<!--<aside class="success">
This operation does not require authentication
</aside>-->

## List Assets

<a id="opIdVdoV1StorageAssetsGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/storage/assets \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
GET //vdo/v1/storage/assets HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

<!--<aside class="success">
This operation does not require authentication
</aside>-->



## Single Dataset

<a id="opIdVdoV1StorageDatasetsGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/storage/datasets \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
GET //vdo/v1/storage/datasets HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

<!--<aside class="success">
This operation does not require authentication
</aside>-->

## Create Empty Dataset

<a id="opIdVdoV1StorageDatasetsPost"></a>

> Code samples

```shell
# You can also use wget
curl -X POST //vdo/v1/storage/datasets \
  -H 'Content-Type: application/json-patch+json' \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
POST //vdo/v1/storage/datasets HTTP/1.1
Host: null
Content-Type: application/json-patch+json
Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Content-Type':'application/json-patch+json',
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

<!--<aside class="success">
This operation does not require authentication
</aside>-->

## List Assets in a Dataset

<a id="opIdVdoV1StorageDatasetsByDatasetidAssetsGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/storage/datasets/{datasetid}/assets \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
GET //vdo/v1/storage/datasets/{datasetid}/assets HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

<!--<aside class="success">
This operation does not require authentication
</aside>-->


## Download Dataset

<a id="opIdVdoV1StorageDatasetsByDatasetidDownloadGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/storage/datasets/{datasetid}/download \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
GET //vdo/v1/storage/datasets/{datasetid}/download HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

<h3 id="vdov1storagedatasetsbydatasetiddownloadget-parameters">Parameters</h3>

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

<h3 id="vdov1storagedatasetsbydatasetiddownloadget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[FileResult](#schemafileresult)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<!--<aside class="success">
This operation does not require authentication
</aside>-->

## Download Asset

<a id="opIdVdoV1StorageAssetsByAssetidDownloadGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/storage/assets/{assetid}/download \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
GET //vdo/v1/storage/assets/{assetid}/download HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

<h3 id="vdov1storageassetsbyassetiddownloadget-parameters">Parameters</h3>

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

<h3 id="vdov1storageassetsbyassetiddownloadget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[FileResult](#schemafileresult)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<!--<aside class="success">
This operation does not require authentication
</aside>-->

# Job 

## List Jobs

<a id="opIdVdoV1JobsGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/jobs \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
GET //vdo/v1/jobs HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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
|» workFlow|[WorkFlowResponse](#schemaworkflowresponse)|false|none|none|
|»» id|string(uuid)|false|none|none|
|»» name|string|false|none|none|
|»» workflowtemplateid|string(uuid)|false|none|none|
|»» content|string|false|none|none|
|»» accesslevel|string|false|none|none|
|»» createdate|string(date-time)|false|none|none|
|»» version|integer(int32)|false|none|none|
|»» ispublished|boolean|false|none|none|
|»» companyid|string(uuid)|false|none|none|

<!--<aside class="success">
This operation does not require authentication
</aside>-->

## Add Job

<a id="opIdVdoV1JobsPost"></a>

> Code samples

```shell
# You can also use wget
curl -X POST //vdo/v1/jobs \
  -H 'Content-Type: application/json-patch+json' \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
POST //vdo/v1/jobs HTTP/1.1
Host: null
Content-Type: application/json-patch+json
Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Content-Type':'application/json-patch+json',
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

<!--<aside class="success">
This operation does not require authentication
</aside>-->

## Get Job

<a id="opIdVdoV1JobsByJobidGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/jobs/{jobid} \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
GET //vdo/v1/jobs/{jobid} HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

<!--<aside class="success">
This operation does not require authentication
</aside>-->

## Job Details

<a id="opIdVdoV1JobsByJobidWorkflowGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/jobs/{jobid}/workflow \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
GET //vdo/v1/jobs/{jobid}/workflow HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

<!--<aside class="success">
This operation does not require authentication
</aside>-->

## Restart Job

<a id="opIdVdoV1JobsByJobidProcessGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/jobs/{jobid}/process \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
GET //vdo/v1/jobs/{jobid}/process HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

<!--<aside class="success">
This operation does not require authentication
</aside>-->


# WorkFlow

## List Avaliable Workflows

<a id="opIdVdoV1WorkflowGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/workflow \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
GET //vdo/v1/workflow HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

*List of workflows avaliable to your account which you can initiate jobs.*

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

<!--<aside class="success">
This operation does not require authentication
</aside>-->

## Workflow Overview

<a id="opIdVdoV1WorkflowByWorkflowidGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/workflow/{workflowid} \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
GET //vdo/v1/workflow/{workflowid} HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

*Select single workflow (compact)*

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

<h3 id="vdov1workflowbyworkflowidget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[WorkFlowTemplateDTO](#schemaworkflowtemplatedto)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<!--<aside class="success">
This operation does not require authentication
</aside>-->

## Workflow with Details

<a id="opIdVdoV1WorkflowByWorkflowidContentGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/workflow/{workflowid}/content \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
GET //vdo/v1/workflow/{workflowid}/content HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

*Select single workflow with details of workflow included*

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

<h3 id="vdov1workflowbyworkflowidcontentget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[WorkFlowTemplateDTO](#schemaworkflowtemplatedto)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<!--<aside class="success">
This operation does not require authentication
</aside>-->

# Information

## Ping

<a id="opIdVdoV1InfoPingGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/info/ping \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
GET //vdo/v1/info/ping HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

<!--<aside class="success">
This operation does not require authentication
</aside>-->

Ver## VdoV1InfoVersionGet

<a id="opIdVdoV1InfoVersionGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/info/version \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
GET //vdo/v1/info/version HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

<!--<aside class="success">
This operation does not require authentication
</aside>-->

## Version

<a id="opIdVdoV1InfoVersionAdminGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/info/version/admin \
  -H 'Accept: text/plain'
  -H 'Authorization: Bearer YOUR_TOKEN'
  -H 'X-Api-Key: string

```

```http
GET //vdo/v1/info/version/admin HTTP/1.1
Host: null

Accept: text/plain
X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

```

```javascript
var headers = {
  'Accept':'text/plain',
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization': 'Bearer YOUR_TOKEN',
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
  'Authorization' => 'Bearer YOUR_TOKEN',
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
'Authorization' : 'Bearer YOUR_TOKEN',
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
		"Authorization": []string{"Bearer YOURTOKEN"},
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

<!--<aside class="success">
This operation does not require authentication
</aside>-->

## Role Claims

<a id="opIdVdoV1InfoClaimsGet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET //vdo/v1/info/claims \
  -H 'X-Api-Key: string

```

```http
GET //vdo/v1/info/claims HTTP/1.1
Host: null

X-Api-Key: string
Authorization: Bearer YOUR_TOKEN

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

<!--<aside class="success">
This operation does not require authentication
</aside>-->

# Schemas

## ApplicationVersion

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

## AuthenicationResponse

<a id="schemaauthenticate"></a>

```json
{
    "access_token": "string",
    "scope": "string",
    "expires_in": "integer",
    "token_type": "string"
}


```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|access_token|string|true|none|none|
|scope|string|false|none|none|
|expires_in|integer|true|read-only|none|
|token_type|string(int32)|true|none|none|




## AssetDTO

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


## AssetUploadResponse

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

## ClientAsUser

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

## DataSetDTO

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

## DataSetCreateRequest

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


## FileResult

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

## EntityTagHeaderValue

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


## EntityDataSaveRequest

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

## EntityData

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

## EntityResponse

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

## EntityAssetResponse

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


## IFormFile

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


## JobRequest

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

## JobParameter

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

## Job

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


## JobDetails

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

## JobDTO

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

## JobFlowDTO

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

## StringSegment

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

## TokenInformation

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

## TaskComplete

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

## UniqueIdentifier

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


## WorkFlowResponse

<a id="schemaworkflowresponse"></a>

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

## WorkFlowTemplateDTO

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

## WorkFlowIODTO

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


## WorkFlowDTO

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
