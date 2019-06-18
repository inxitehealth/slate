---
title: INXITE API
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

<h1 id="inxite-api">INXITE API v1.1.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

This documentation is for the INXITE Platform API.

Base URLs:

* <a href="https://api.test/">https://api.test/</a>

Email: <a href="mailto:development@inxitehealth.com">Support</a>

# Authentication

* API Key (Bearer)
    - Parameter Name: **Authorization**, in: header.

<h1 id="inxite-api-login">Login</h1>

## Obtain an Access Token

> Code samples

```shell
# You can also use wget
curl -X POST https://api.test/login \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Accept: application/json'

```

```http
POST https://api.test/login HTTP/1.1
Host: api.test
Content-Type: application/x-www-form-urlencoded
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.test/login',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "username": "string",
  "password": "string",
  "time_zone": "string",
  "api_key": "string",
  "api_secret": "string"
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json'

};

fetch('https://api.test/login',
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
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.test/login',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Accept': 'application/json'
}

r = requests.post('https://api.test/login', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/login");
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
        "Content-Type": []string{"application/x-www-form-urlencoded"},
        "Accept": []string{"application/json"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.test/login", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /login`

Log in to the INXITE platform to obtain an Access Token

> Body parameter

```yaml
username: string
password: string
time_zone: string
api_key: string
api_secret: string

```

<h3 id="obtain-an-access-token-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|username|body|string|true|Only required if the API key being used was issued to an organization|
|password|body|string|true|Required if the API key being used was issued to an organization|
|time_zone|body|string|true|One of the tz database names as maintained by the IANA at https://www.iana.org/time-zones or, for convenience, listed here https://en.wikipedia.org/wiki/List_of_tz_database_time_zones|
|api_key|body|string|true|INXITE API Key|
|api_secret|body|string|true|INXITE API Secret|

> Example responses

> 200 Response

```json
{
  "access_token": "string",
  "token_type": "string",
  "expires_in": 0,
  "refresh_token": "string"
}
```

<h3 id="obtain-an-access-token-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[JWT](#schemajwt)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[JWT_errors](#schemajwt_errors)|

<aside class="success">
This operation does not require authentication
</aside>

## Obtain a new Access Token

> Code samples

```shell
# You can also use wget
curl -X POST https://api.test/refresh \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Accept: application/json'

```

```http
POST https://api.test/refresh HTTP/1.1
Host: api.test
Content-Type: application/x-www-form-urlencoded
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.test/refresh',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "refresh_token": "string"
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json'

};

fetch('https://api.test/refresh',
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
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.test/refresh',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Accept': 'application/json'
}

r = requests.post('https://api.test/refresh', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/refresh");
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
        "Content-Type": []string{"application/x-www-form-urlencoded"},
        "Accept": []string{"application/json"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.test/refresh", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /refresh`

Obtain a new Access Token

> Body parameter

```yaml
refresh_token: string

```

<h3 id="obtain-a-new-access-token-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|refresh_token|body|string|false|The Refresh Token string|

> Example responses

> 200 Response

```json
{
  "access_token": "string",
  "token_type": "string",
  "expires_in": 0,
  "refresh_token": "string"
}
```

<h3 id="obtain-a-new-access-token-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[JWT](#schemajwt)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[JWT_errors](#schemajwt_errors)|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="inxite-api-patient">Patient</h1>

## Search patients

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/patients?first_name=string&last_name=string&date_of_birth=2019-06-18&postal_code=string \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/patients?first_name=string&last_name=string&date_of_birth=2019-06-18&postal_code=string HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients',
  method: 'get',
  data: '?first_name=string&last_name=string&date_of_birth=2019-06-18&postal_code=string',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients?first_name=string&last_name=string&date_of_birth=2019-06-18&postal_code=string',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/patients',
  params: {
  'first_name' => 'string',
'last_name' => 'string',
'date_of_birth' => 'string(date)',
'postal_code' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/patients', params={
  'first_name': 'string',  'last_name': 'string',  'date_of_birth': '2019-06-18',  'postal_code': 'string'
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients?first_name=string&last_name=string&date_of_birth=2019-06-18&postal_code=string");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/patients", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /patients`

Search patients

<h3 id="search-patients-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|first_name|query|string|true|Patient first name|
|last_name|query|string|true|Patient last name|
|date_of_birth|query|string(date)|true|Patient date of birth|
|postal_code|query|string|true|Patient postal code|

> Example responses

> 200 Response

```json
[
  {
    "patient_id": 0,
    "user_id": 0,
    "uuid": "string",
    "organizations": [
      {
        "id": 0,
        "name": "string",
        "code": "string"
      }
    ],
    "title": "Mr.",
    "first_name": "string",
    "middle_name": "string",
    "last_name": "string",
    "suffix": "Jr.",
    "preferred_name": "string",
    "date_of_birth": "2019-06-18",
    "gender": "Male",
    "source_organization_id": 0,
    "ssn": "string",
    "marital_status": "Married",
    "blood_type": "A Negative",
    "organ_donor": false,
    "street": "string",
    "city": "string",
    "state": "string",
    "postal_code": "string",
    "country_code": "USA",
    "phone_home": "string",
    "phone_home_disconnected": false,
    "phone_cell": "string",
    "phone_cell_disconnected": false,
    "email": "user@example.com",
    "employer": {
      "name": "string",
      "street": "string",
      "city": "string",
      "state": "string",
      "postal_code": "string",
      "occupation": "string",
      "industry": "string"
    },
    "language_id": "string",
    "interpreter": false,
    "ethnicity": "Hispanic or Latino",
    "race": "American Indian/Alaska Native",
    "emergency": [
      {
        "name": "string",
        "phone": "string",
        "relation": "string"
      }
    ],
    "caregiver": [
      {
        "name": "string",
        "phone": "string",
        "relation": "string",
        "power_of_attorney": true
      }
    ],
    "deceased": false,
    "deceased_reason": "string",
    "deceased_date": "2019-06-18",
    "created": {
      "date": "2019-06-18T20:09:43Z",
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    }
  }
]
```

<h3 id="search-patients-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Errors|Inline|

<h3 id="search-patients-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Patient](#schemapatient)]|false|none|none|
|» patient_id|integer|false|none|none|
|» user_id|integer|false|none|none|
|» uuid|string|false|none|none|
|» organizations|[[PatientOrganizations](#schemapatientorganizations)]|false|none|none|
|»» id|integer|false|none|Organization ID|
|»» name|string|false|none|Organization Name|
|»» code|string|false|none|Organization Code|
|» title|string|false|none|none|
|» first_name|string|false|none|none|
|» middle_name|string|false|none|none|
|» last_name|string|false|none|none|
|» suffix|string|false|none|none|
|» preferred_name|string|false|none|none|
|» date_of_birth|string(date)|false|none|none|
|» gender|string|false|none|none|
|» source_organization_id|integer|false|none|none|
|» ssn|string|false|none|none|
|» marital_status|string|false|none|none|
|» blood_type|string|false|none|none|
|» organ_donor|boolean|false|none|none|
|» street|string|false|none|none|
|» city|string|false|none|none|
|» state|string|false|none|none|
|» postal_code|string|false|none|none|
|» country_code|string|false|none|none|
|» phone_home|string|false|none|none|
|» phone_home_disconnected|boolean|false|none|none|
|» phone_cell|string|false|none|none|
|» phone_cell_disconnected|boolean|false|none|none|
|» email|string(email)|false|none|none|
|» employer|[EmployerObject](#schemaemployerobject)|false|none|Patient Employer information|
|»» name|string|false|none|Employer name|
|»» street|string|false|none|Employer street address|
|»» city|string|false|none|Employer city|
|»» state|string|false|none|Employer state|
|»» postal_code|string|false|none|Employer postal code|
|»» occupation|string|false|none|Employee occupation|
|»» industry|string|false|none|Employer industry|
|» language_id|string|false|none|none|
|» interpreter|boolean|false|none|none|
|» ethnicity|string|false|none|none|
|» race|string|false|none|none|
|» emergency|[[PatientEmergencyObject](#schemapatientemergencyobject)]|false|none|none|
|»» name|string|false|none|Emergency contact name|
|»» phone|string|false|none|Emergency contact phone number|
|»» relation|string|false|none|Emergency contact relationship|
|» caregiver|[[PatientCaregiverObject](#schemapatientcaregiverobject)]|false|none|none|
|»» name|string|false|none|Caregiver contact name|
|»» phone|string|false|none|Caregiver contact phone number|
|»» relation|string|false|none|Caregiver contact relationship|
|»» power_of_attorney|boolean|false|none|Caregiver contact is POA (Power of Attorney)?|
|» deceased|boolean|false|none|none|
|» deceased_reason|string|false|none|none|
|» deceased_date|string(date)|false|none|none|
|» created|[CreatedObject](#schemacreatedobject)|false|none|Information on the individual who created the record|
|»» date|string(date-time)|false|none|Date and time of record creation|
|»» first_name|string|false|none|First name of individual who created the record|
|»» last_name|string|false|none|Last name of individual who created the record|
|»» user_id|integer|false|none|User ID for individual who created the record|

#### Enumerated Values

|Property|Value|
|---|---|
|title|Mr.|
|title|Mrs.|
|title|Ms.|
|title|Dr.|
|suffix|Jr.|
|suffix|Sr.|
|suffix|II|
|suffix|III|
|suffix|Esq.|
|gender|Male|
|gender|Female|
|marital_status|Married|
|marital_status|Single|
|marital_status|Divorced|
|marital_status|Widowed|
|marital_status|Separated|
|marital_status|Domestic Partner|
|blood_type|A Negative|
|blood_type|A Positive|
|blood_type|AB Negative|
|blood_type|AB Positive|
|blood_type|B Negative|
|blood_type|B Positive|
|blood_type|O Negative|
|blood_type|O Positive|
|ethnicity|Hispanic or Latino|
|ethnicity|Not Hispanic or Latino|
|ethnicity|Unknown|
|ethnicity|Declined To Specify|
|race|American Indian/Alaska Native|
|race|Asian|
|race|Black/African American|
|race|Caucasian/White|
|race|Multi-Racial|
|race|Native Hawaiian/Other Pacific Islander|
|race|Other|
|race|Unknown|
|race|Declined To Specify|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» first_name|[string]|false|none|none|
|» last_name|[string]|false|none|none|
|» date_of_birth|[string]|false|none|none|
|» postal_code|[string]|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Create a patient

> Code samples

```shell
# You can also use wget
curl -X POST https://api.test/patients \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
POST https://api.test/patients HTTP/1.1
Host: api.test
Content-Type: application/x-www-form-urlencoded
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "organization_ids": [
    0
  ],
  "title": "Mr.",
  "first_name": "string",
  "middle_name": "string",
  "last_name": "string",
  "suffix": "Jr.",
  "preferred_name": "string",
  "date_of_birth": "2019-06-18",
  "gender": "Male",
  "source_organization_id": 0,
  "ssn": "string",
  "marital_status": "Married",
  "blood_type": "A Negative",
  "organ_donor": false,
  "street": "string",
  "city": "string",
  "state": "string",
  "postal_code": "string",
  "country_code": "USA",
  "phone_home": "string",
  "phone_home_disconnected": false,
  "phone_cell": "string",
  "phone_cell_disconnected": false,
  "email": "user@example.com",
  "occupation": "string",
  "industry": "Accommodations",
  "employer_name": "string",
  "employer_street": "string",
  "employer_city": "string",
  "employer_state": "string",
  "employer_postal_code": "string",
  "language_id": "string",
  "interpreter": false,
  "ethnicity": "Hispanic or Latino",
  "race": "American Indian/Alaska Native",
  "guardian_name": "string",
  "guardian_phone": "string",
  "guardian_relationship": "Child",
  "alt_guardian_name": "string",
  "alt_guardian_phone": "string",
  "alt_guardian_relationship": "Child",
  "caregiver_name": "string",
  "caregiver_phone": "string",
  "caregiver_relationship": "Child",
  "caregiver_poa": false,
  "deceased": false,
  "deceased_reason": "string",
  "deceased_date": "2019-06-18"
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients',
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
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Accept' => 'application/json',
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'https://api.test/patients',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.post('https://api.test/patients', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients");
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
        "Content-Type": []string{"application/x-www-form-urlencoded"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.test/patients", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /patients`

Create a patient.

> Body parameter

```yaml
organization_ids:
  - 0
title: Mr.
first_name: string
middle_name: string
last_name: string
suffix: Jr.
preferred_name: string
date_of_birth: '2019-06-18'
gender: Male
source_organization_id: 0
ssn: string
marital_status: Married
blood_type: A Negative
organ_donor: false
street: string
city: string
state: string
postal_code: string
country_code: USA
phone_home: string
phone_home_disconnected: false
phone_cell: string
phone_cell_disconnected: false
email: user@example.com
occupation: string
industry: Accommodations
employer_name: string
employer_street: string
employer_city: string
employer_state: string
employer_postal_code: string
language_id: string
interpreter: false
ethnicity: Hispanic or Latino
race: American Indian/Alaska Native
guardian_name: string
guardian_phone: string
guardian_relationship: Child
alt_guardian_name: string
alt_guardian_phone: string
alt_guardian_relationship: Child
caregiver_name: string
caregiver_phone: string
caregiver_relationship: Child
caregiver_poa: false
deceased: false
deceased_reason: string
deceased_date: '2019-06-18'

```

<h3 id="create-a-patient-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_ids|body|[integer]|true|Organization ID's array|
|title|body|string|false|Title|
|first_name|body|string|true|First Name|
|middle_name|body|string|false|Middle Name|
|last_name|body|string|true|Last Name|
|suffix|body|string|false|Suffix|
|preferred_name|body|string|false|Preferred Name|
|date_of_birth|body|string(date)|true|Date of Birth (YYYY-MM-DD)|
|gender|body|string|true|Gender|
|source_organization_id|body|integer|false|Source Organization InXite ID (Default to POST Organization ID)|
|ssn|body|string|false|SSN Last 4|
|marital_status|body|string|false|Marital Status|
|blood_type|body|string|false|Blood Type|
|organ_donor|body|boolean|false|Flag to indicate if the patient is an organ donor|
|street|body|string|false|Address|
|city|body|string|false|City|
|state|body|string|false|2 letter state code|
|postal_code|body|string|true|Postal Code (Max length 5)|
|country_code|body|string|false|Country Code|
|phone_home|body|string|true|Home Phone|
|phone_home_disconnected|body|boolean|false|Home Phone Disconnected|
|phone_cell|body|string|false|Cell Phone|
|phone_cell_disconnected|body|boolean|false|Cell Phone Disconnected|
|email|body|string(email)|false|Email address|
|occupation|body|string|false|Occupation|
|industry|body|string|false|Industry|
|employer_name|body|string|false|Employer Name|
|employer_street|body|string|false|Employer Address|
|employer_city|body|string|false|Employer City|
|employer_state|body|string|false|2 letter state code|
|employer_postal_code|body|string|false|Employer Postal Code (Max length 5)|
|language_id|body|string|false|InXite Language ID|
|interpreter|body|boolean|false|Flag to indicate if the patient requires an interpreter|
|ethnicity|body|string|false|Ethnicity|
|race|body|string|false|Race|
|guardian_name|body|string|false|Emergency Contact/Guardian Name|
|guardian_phone|body|string|false|Emergency Contact/Guardian Phone|
|guardian_relationship|body|string|false|Emergency Contact/Guardian Relation|
|alt_guardian_name|body|string|false|Alter Emergency Contact/Guardian Name|
|alt_guardian_phone|body|string|false|Alter Emergency Contact/Guardian Phone|
|alt_guardian_relationship|body|string|false|Alter Emergency Contact/Guardian Relation|
|caregiver_name|body|string|false|Caregiver Name|
|caregiver_phone|body|string|false|Caregiver Phone|
|caregiver_relationship|body|string|false|Caregiver Relation|
|caregiver_poa|body|boolean|false|Does Caregiver is POA (Power of Attorney)?|
|deceased|body|boolean|false|Patient Deceased|
|deceased_reason|body|string|false|Patient Deceased Reason|
|deceased_date|body|string(date)|false|Patient Deceased Date (YYYY-MM-DD)|

#### Enumerated Values

|Parameter|Value|
|---|---|
|title|Mr.|
|title|Mrs.|
|title|Ms.|
|title|Dr.|
|suffix|Jr.|
|suffix|Sr.|
|suffix|II|
|suffix|III|
|suffix|Esq.|
|gender|Male|
|gender|Female|
|marital_status|Married|
|marital_status|Single|
|marital_status|Divorced|
|marital_status|Widowed|
|marital_status|Separated|
|marital_status|Domestic Partner|
|blood_type|A Negative|
|blood_type|A Positive|
|blood_type|AB Negative|
|blood_type|AB Positive|
|blood_type|B Negative|
|blood_type|B Positive|
|blood_type|O Negative|
|blood_type|O Positive|
|industry|Accommodations|
|industry|Accounting|
|industry|Advertising|
|industry|Aerospace|
|industry|Agriculture & Agribusiness|
|industry|Air Transportation|
|industry|Apparel & Accessories|
|industry|Auto|
|industry|Banking|
|industry|Beauty & Cosmetics|
|industry|Biotechnology|
|industry|Chemical|
|industry|Communications|
|industry|Computer|
|industry|Construction|
|industry|Consulting|
|industry|Consumer Products|
|industry|Education|
|industry|Electronics|
|industry|Employment|
|industry|Energy|
|industry|Entertainment & Recreation|
|industry|Fashion|
|industry|Financial Services|
|industry|Food & Beverage|
|industry|Health|
|industry|Healthcare|
|industry|Information Technology|
|industry|Insurance|
|industry|Journalism & News|
|industry|Legal Services|
|industry|Manufacturing|
|industry|Media & Broadcasting|
|industry|Medical Devices & Supplies|
|industry|Motion Pictures & Video|
|industry|Music|
|industry|Pharmaceutical|
|industry|Public Administration|
|industry|Public Relations|
|industry|Publishing|
|industry|Real Estate|
|industry|Retail|
|industry|Service|
|industry|Sports|
|industry|Technology|
|industry|Telecommunications|
|industry|Tourism|
|industry|Transportation|
|industry|Travel|
|industry|Utilities|
|industry|Video Game|
|industry|Web Services|
|ethnicity|Hispanic or Latino|
|ethnicity|Not Hispanic or Latino|
|ethnicity|Unknown|
|ethnicity|Declined To Specify|
|race|American Indian/Alaska Native|
|race|Asian|
|race|Black/African American|
|race|Caucasian/White|
|race|Multi-Racial|
|race|Native Hawaiian/Other Pacific Islander|
|race|Other|
|race|Unknown|
|race|Declined To Specify|
|guardian_relationship|Child|
|guardian_relationship|Father|
|guardian_relationship|Grandparent|
|guardian_relationship|Mother|
|guardian_relationship|Other|
|guardian_relationship|Sibling|
|guardian_relationship|Spouse|
|alt_guardian_relationship|Child|
|alt_guardian_relationship|Father|
|alt_guardian_relationship|Grandparent|
|alt_guardian_relationship|Mother|
|alt_guardian_relationship|Other|
|alt_guardian_relationship|Sibling|
|alt_guardian_relationship|Spouse|
|caregiver_relationship|Child|
|caregiver_relationship|Father|
|caregiver_relationship|Grandparent|
|caregiver_relationship|Mother|
|caregiver_relationship|Other|
|caregiver_relationship|Sibling|
|caregiver_relationship|Spouse|

> Example responses

> 201 Response

```json
{
  "patient_id": 0,
  "user_id": 0,
  "uuid": "string",
  "organizations": [
    {
      "id": 0,
      "name": "string",
      "code": "string"
    }
  ],
  "title": "Mr.",
  "first_name": "string",
  "middle_name": "string",
  "last_name": "string",
  "suffix": "Jr.",
  "preferred_name": "string",
  "date_of_birth": "2019-06-18",
  "gender": "Male",
  "source_organization_id": 0,
  "ssn": "string",
  "marital_status": "Married",
  "blood_type": "A Negative",
  "organ_donor": false,
  "street": "string",
  "city": "string",
  "state": "string",
  "postal_code": "string",
  "country_code": "USA",
  "phone_home": "string",
  "phone_home_disconnected": false,
  "phone_cell": "string",
  "phone_cell_disconnected": false,
  "email": "user@example.com",
  "employer": {
    "name": "string",
    "street": "string",
    "city": "string",
    "state": "string",
    "postal_code": "string",
    "occupation": "string",
    "industry": "string"
  },
  "language_id": "string",
  "interpreter": false,
  "ethnicity": "Hispanic or Latino",
  "race": "American Indian/Alaska Native",
  "emergency": [
    {
      "name": "string",
      "phone": "string",
      "relation": "string"
    }
  ],
  "caregiver": [
    {
      "name": "string",
      "phone": "string",
      "relation": "string",
      "power_of_attorney": true
    }
  ],
  "deceased": false,
  "deceased_reason": "string",
  "deceased_date": "2019-06-18",
  "created": {
    "date": "2019-06-18T20:09:43Z",
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  }
}
```

<h3 id="create-a-patient-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|[Patient](#schemapatient)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get patient

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/patients/{patient_id} \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/patients/{patient_id} HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/patients/{patient_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/patients/{patient_id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/patients/{patient_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /patients/{patient_id}`

Get a patient record

<h3 id="get-patient-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|integer|true|Patient ID|

> Example responses

> 200 Response

```json
{
  "patient_id": 0,
  "user_id": 0,
  "uuid": "string",
  "organizations": [
    {
      "id": 0,
      "name": "string",
      "code": "string"
    }
  ],
  "title": "Mr.",
  "first_name": "string",
  "middle_name": "string",
  "last_name": "string",
  "suffix": "Jr.",
  "preferred_name": "string",
  "date_of_birth": "2019-06-18",
  "gender": "Male",
  "source_organization_id": 0,
  "ssn": "string",
  "marital_status": "Married",
  "blood_type": "A Negative",
  "organ_donor": false,
  "street": "string",
  "city": "string",
  "state": "string",
  "postal_code": "string",
  "country_code": "USA",
  "phone_home": "string",
  "phone_home_disconnected": false,
  "phone_cell": "string",
  "phone_cell_disconnected": false,
  "email": "user@example.com",
  "employer": {
    "name": "string",
    "street": "string",
    "city": "string",
    "state": "string",
    "postal_code": "string",
    "occupation": "string",
    "industry": "string"
  },
  "language_id": "string",
  "interpreter": false,
  "ethnicity": "Hispanic or Latino",
  "race": "American Indian/Alaska Native",
  "emergency": [
    {
      "name": "string",
      "phone": "string",
      "relation": "string"
    }
  ],
  "caregiver": [
    {
      "name": "string",
      "phone": "string",
      "relation": "string",
      "power_of_attorney": true
    }
  ],
  "deceased": false,
  "deceased_reason": "string",
  "deceased_date": "2019-06-18",
  "created": {
    "date": "2019-06-18T20:09:43Z",
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  }
}
```

<h3 id="get-patient-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[Patient](#schemapatient)|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get patient appointments

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/patients/{patient_id}/appointments \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/patients/{patient_id}/appointments HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/appointments',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/appointments',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/patients/{patient_id}/appointments',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/patients/{patient_id}/appointments', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/appointments");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/patients/{patient_id}/appointments", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /patients/{patient_id}/appointments`

Get patient appointments

<h3 id="get-patient-appointments-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "patient": {
      "id": 0,
      "first_name": "string",
      "last_name": "string"
    },
    "date": "2019-06-18",
    "time": "string",
    "specialty": {
      "id": 0,
      "name": "string"
    },
    "provider": {
      "first_name": "string",
      "last_name": "string",
      "id": 0
    },
    "status": "pending",
    "created": {
      "date": "2019-06-18T20:09:43Z",
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    },
    "updated": {
      "date": "2019-06-18T20:09:43Z",
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    }
  }
]
```

<h3 id="get-patient-appointments-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<h3 id="get-patient-appointments-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Appointment](#schemaappointment)]|false|none|none|
|» id|integer|false|none|The InXite identifier for the appointment|
|» patient|object|false|none|Basic patient information|
|»» id|integer|false|none|The InXite identifier for the patient|
|»» first_name|string|false|none|Patient first name|
|»» last_name|string|false|none|Patient last name|
|» date|string(date)|false|none|Date of appointment|
|» time|string|false|none|Time of appointment|
|» specialty|object|false|none|none|
|»» id|integer|false|none|InXite specialty ID|
|»» name|string|false|none|Name of specialty|
|» provider|object|false|none|none|
|»» first_name|string|false|none|First name of provider|
|»» last_name|string|false|none|Last name of provider|
|»» id|integer|false|none|Provider ID|
|» status|string|false|none|Appointment status|
|» created|[CreatedObject](#schemacreatedobject)|false|none|Information on the individual who created the record|
|»» date|string(date-time)|false|none|Date and time of record creation|
|»» first_name|string|false|none|First name of individual who created the record|
|»» last_name|string|false|none|Last name of individual who created the record|
|»» user_id|integer|false|none|User ID for individual who created the record|
|» updated|[UpdatedObject](#schemaupdatedobject)|false|none|Information on the individual who last updated the record|
|»» date|string(date-time)|false|none|Date and time of the most recent record update|
|»» first_name|string|false|none|First name of individual who last updated the record|
|»» last_name|string|false|none|Last name of individual who last updated the record|
|»» user_id|integer|false|none|User ID for individual who last updated the record|

#### Enumerated Values

|Property|Value|
|---|---|
|status|pending|
|status|scheduled|
|status|cancelled|
|status|rescheduled|
|status|complete|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Create a patient appointment

> Code samples

```shell
# You can also use wget
curl -X POST https://api.test/patients/{patient_id}/appointments \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Authorization: API_KEY'

```

```http
POST https://api.test/patients/{patient_id}/appointments HTTP/1.1
Host: api.test
Content-Type: application/x-www-form-urlencoded

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/appointments',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "provider_id": 0,
  "status": "pending",
  "date": "2019-06-18",
  "time": "string",
  "specialty_id": 0
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/appointments',
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
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'https://api.test/patients/{patient_id}/appointments',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Authorization': 'API_KEY'
}

r = requests.post('https://api.test/patients/{patient_id}/appointments', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/appointments");
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
        "Content-Type": []string{"application/x-www-form-urlencoded"},
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.test/patients/{patient_id}/appointments", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /patients/{patient_id}/appointments`

Create a patient appointment.

> Body parameter

```yaml
provider_id: 0
status: pending
date: '2019-06-18'
time: string
specialty_id: 0

```

<h3 id="create-a-patient-appointment-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|
|provider_id|body|integer|false|Provider ID|
|status|body|string|true|Current appointment status|
|date|body|string(date)|false|Date of appointment|
|time|body|string|false|Time of appointment|
|specialty_id|body|integer|true|Specialty ID obtained from GET /specialty endpoint|

#### Enumerated Values

|Parameter|Value|
|---|---|
|status|pending|
|status|scheduled|
|status|cancelled|
|status|rescheduled|
|status|complete|

<h3 id="create-a-patient-appointment-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get a patient appointment

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/patients/{patient_id}/appointments/{appointment_id} \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/patients/{patient_id}/appointments/{appointment_id} HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/appointments/{appointment_id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/appointments/{appointment_id}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/patients/{patient_id}/appointments/{appointment_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/patients/{patient_id}/appointments/{appointment_id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/appointments/{appointment_id}");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/patients/{patient_id}/appointments/{appointment_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /patients/{patient_id}/appointments/{appointment_id}`

Get a patient appointment

<h3 id="get-a-patient-appointment-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|integer|true|Patient ID|
|appointment_id|path|integer|true|Appointment ID|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "patient": {
    "id": 0,
    "first_name": "string",
    "last_name": "string"
  },
  "date": "2019-06-18",
  "time": "string",
  "specialty": {
    "id": 0,
    "name": "string"
  },
  "provider": {
    "first_name": "string",
    "last_name": "string",
    "id": 0
  },
  "status": "pending",
  "created": {
    "date": "2019-06-18T20:09:43Z",
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  },
  "updated": {
    "date": "2019-06-18T20:09:43Z",
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  }
}
```

<h3 id="get-a-patient-appointment-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[Appointment](#schemaappointment)|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Update a patient appointment

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.test/patients/{patient_id}/appointments/{appointment_id} \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Authorization: API_KEY'

```

```http
PUT https://api.test/patients/{patient_id}/appointments/{appointment_id} HTTP/1.1
Host: api.test
Content-Type: application/x-www-form-urlencoded

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/appointments/{appointment_id}',
  method: 'put',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "provider_id": 0,
  "status": "pending",
  "date": "2019-06-18",
  "time": "string",
  "specialty_id": 0
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/appointments/{appointment_id}',
{
  method: 'PUT',
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
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Authorization' => 'API_KEY'
}

result = RestClient.put 'https://api.test/patients/{patient_id}/appointments/{appointment_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Authorization': 'API_KEY'
}

r = requests.put('https://api.test/patients/{patient_id}/appointments/{appointment_id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/appointments/{appointment_id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
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
        "Content-Type": []string{"application/x-www-form-urlencoded"},
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://api.test/patients/{patient_id}/appointments/{appointment_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /patients/{patient_id}/appointments/{appointment_id}`

Update a patient appointment.

> Body parameter

```yaml
provider_id: 0
status: pending
date: '2019-06-18'
time: string
specialty_id: 0

```

<h3 id="update-a-patient-appointment-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|
|appointment_id|path|string|true|Appointment ID|
|provider_id|body|integer|false|Provider ID|
|status|body|string|true|Current appointment status|
|date|body|string(date)|false|Date of appointment|
|time|body|string|false|Time of appointment|
|specialty_id|body|integer|true|Specialty ID obtained from GET /specialty endpoint|

#### Enumerated Values

|Parameter|Value|
|---|---|
|status|pending|
|status|scheduled|
|status|cancelled|
|status|rescheduled|
|status|complete|

<h3 id="update-a-patient-appointment-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get patient diagnoses

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/patients/{patient_id}/diagnoses \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/patients/{patient_id}/diagnoses HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/diagnoses',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/diagnoses',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/patients/{patient_id}/diagnoses',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/patients/{patient_id}/diagnoses', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/diagnoses");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/patients/{patient_id}/diagnoses", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /patients/{patient_id}/diagnoses`

Get patient diagnoses

<h3 id="get-patient-diagnoses-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "title": "string",
    "diagnosis": "string",
    "chronic": true,
    "active": true
  }
]
```

<h3 id="get-patient-diagnoses-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<h3 id="get-patient-diagnoses-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Diagnosis](#schemadiagnosis)]|false|none|none|
|» id|integer|false|none|The InXite identifier for the Diagnosis|
|» title|string|false|none|The Title Diagnosis|
|» diagnosis|string|false|none|The ICD code|
|» chronic|boolean|false|none|Chronic status|
|» active|boolean|false|none|Active status|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get a patient diagnosis

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/patients/{patient_id}/diagnoses/{diagnosis_id} \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/patients/{patient_id}/diagnoses/{diagnosis_id} HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/diagnoses/{diagnosis_id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/diagnoses/{diagnosis_id}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/patients/{patient_id}/diagnoses/{diagnosis_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/patients/{patient_id}/diagnoses/{diagnosis_id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/diagnoses/{diagnosis_id}");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/patients/{patient_id}/diagnoses/{diagnosis_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /patients/{patient_id}/diagnoses/{diagnosis_id}`

Get a patient diagnosis

<h3 id="get-a-patient-diagnosis-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|
|diagnosis_id|path|string|true|Diagnosis ID|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "title": "string",
  "diagnosis": "string",
  "chronic": true,
  "active": true
}
```

<h3 id="get-a-patient-diagnosis-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[Diagnosis](#schemadiagnosis)|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Update a patient diagnosis

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.test/patients/{patient_id}/diagnoses/{diagnosis_id} \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Authorization: API_KEY'

```

```http
PUT https://api.test/patients/{patient_id}/diagnoses/{diagnosis_id} HTTP/1.1
Host: api.test
Content-Type: application/x-www-form-urlencoded

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/diagnoses/{diagnosis_id}',
  method: 'put',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "chronic": true
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/diagnoses/{diagnosis_id}',
{
  method: 'PUT',
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
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Authorization' => 'API_KEY'
}

result = RestClient.put 'https://api.test/patients/{patient_id}/diagnoses/{diagnosis_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Authorization': 'API_KEY'
}

r = requests.put('https://api.test/patients/{patient_id}/diagnoses/{diagnosis_id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/diagnoses/{diagnosis_id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
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
        "Content-Type": []string{"application/x-www-form-urlencoded"},
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://api.test/patients/{patient_id}/diagnoses/{diagnosis_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /patients/{patient_id}/diagnoses/{diagnosis_id}`

Update a patient Diagnosis. This is only used to update the chronic for the moment

> Body parameter

```yaml
chronic: true

```

<h3 id="update-a-patient-diagnosis-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|
|diagnosis_id|path|string|true|InXite Diagnosis ID|
|chronic|body|boolean|true|Chronic as true or false|

<h3 id="update-a-patient-diagnosis-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get current patient health score

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/patients/{patient_id}/healthscore \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/patients/{patient_id}/healthscore HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/healthscore',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/healthscore',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/patients/{patient_id}/healthscore',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/patients/{patient_id}/healthscore', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/healthscore");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/patients/{patient_id}/healthscore", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /patients/{patient_id}/healthscore`

Get current patient health score

<h3 id="get-current-patient-health-score-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "patient_id": 0,
  "score": 0,
  "metrics": [
    {
      "id": 0,
      "category": "string",
      "level": "string",
      "metric_id": 0,
      "metric_level": "string",
      "name": "string",
      "score": 0,
      "source": {
        "id": 0,
        "module": "string"
      },
      "unit": "string",
      "value": {
        "current": "string",
        "text": "string"
      },
      "created": {
        "date": "2019-06-18T20:09:43Z",
        "first_name": "string",
        "last_name": "string",
        "user_id": 0
      },
      "updated": {
        "date": "2019-06-18T20:09:43Z",
        "first_name": "string",
        "last_name": "string",
        "user_id": 0
      }
    }
  ],
  "created": {
    "date": "2019-06-18T20:09:43Z",
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  }
}
```

<h3 id="get-current-patient-health-score-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[HealthScore](#schemahealthscore)|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get a patient health score

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/patients/{patient_id}/healthscore/{healthscore_id} \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/patients/{patient_id}/healthscore/{healthscore_id} HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/healthscore/{healthscore_id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/healthscore/{healthscore_id}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/patients/{patient_id}/healthscore/{healthscore_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/patients/{patient_id}/healthscore/{healthscore_id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/healthscore/{healthscore_id}");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/patients/{patient_id}/healthscore/{healthscore_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /patients/{patient_id}/healthscore/{healthscore_id}`

Get a patient health score

<h3 id="get-a-patient-health-score-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|
|healthscore_id|path|string|true|Health Score ID|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "patient_id": 0,
  "score": 0,
  "metrics": [
    {
      "id": 0,
      "category": "string",
      "level": "string",
      "metric_id": 0,
      "metric_level": "string",
      "name": "string",
      "score": 0,
      "source": {
        "id": 0,
        "module": "string"
      },
      "unit": "string",
      "value": {
        "current": "string",
        "text": "string"
      },
      "created": {
        "date": "2019-06-18T20:09:43Z",
        "first_name": "string",
        "last_name": "string",
        "user_id": 0
      },
      "updated": {
        "date": "2019-06-18T20:09:43Z",
        "first_name": "string",
        "last_name": "string",
        "user_id": 0
      }
    }
  ],
  "created": {
    "date": "2019-06-18T20:09:43Z",
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  }
}
```

<h3 id="get-a-patient-health-score-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[HealthScore](#schemahealthscore)|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get patient medications

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/patients/{patient_id}/medications \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/patients/{patient_id}/medications HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/medications',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/medications',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/patients/{patient_id}/medications',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/patients/{patient_id}/medications', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/medications");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/patients/{patient_id}/medications", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /patients/{patient_id}/medications`

Get patient medications

<h3 id="get-patient-medications-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|

> Example responses

> 200 Response

```json
[
  {
    "id": "string",
    "rxImage": "string",
    "title": "string",
    "desc": "string"
  }
]
```

<h3 id="get-patient-medications-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<h3 id="get-patient-medications-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|
|» id|string|false|none|INXITE medication ID|
|» rxImage|string|false|none|URL to medication image|
|» title|string|false|none|Medication Name|
|» desc|string|false|none|Default Medication Description|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Create patient medication

> Code samples

```shell
# You can also use wget
curl -X POST https://api.test/patients/{patient_id}/medications \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
POST https://api.test/patients/{patient_id}/medications HTTP/1.1
Host: api.test
Content-Type: application/x-www-form-urlencoded
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/medications',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "medication_name": "string",
  "rxnorm_cui": 0,
  "start_date": "2019-06-18",
  "end_date": "2019-06-18",
  "quantity": 0,
  "dose": 0,
  "units": "string",
  "take": 0,
  "form_id": 0,
  "route_id": 0,
  "interval_id": 0,
  "refill_count": 0,
  "per_refill_count": 0,
  "instructions": "string"
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/medications',
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
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Accept' => 'application/json',
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'https://api.test/patients/{patient_id}/medications',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.post('https://api.test/patients/{patient_id}/medications', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/medications");
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
        "Content-Type": []string{"application/x-www-form-urlencoded"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.test/patients/{patient_id}/medications", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /patients/{patient_id}/medications`

Create patient medication

> Body parameter

```yaml
medication_name: string
rxnorm_cui: 0
start_date: '2019-06-18'
end_date: '2019-06-18'
quantity: 0
dose: 0
units: string
take: 0
form_id: 0
route_id: 0
interval_id: 0
refill_count: 0
per_refill_count: 0
instructions: string

```

<h3 id="create-patient-medication-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|
|medication_name|body|string|true|Full medication name|
|rxnorm_cui|body|integer|false|RxNorm concept ID|
|start_date|body|string(date)|true|Medication start date|
|end_date|body|string(date)|false|Medication end date|
|quantity|body|integer|false|Initial quantity (count)|
|dose|body|integer|false|Strength|
|units|body|string|false|Unit of measure|
|take|body|integer|false|How many to take|
|form_id|body|integer|false|Form factor|
|route_id|body|integer|false|Route of administration|
|interval_id|body|integer|false|Frequency|
|refill_count|body|integer|false|Number of refills|
|per_refill_count|body|integer|false|Number of units per refill|
|instructions|body|string|false|Instructions for taking the medication|

> Example responses

> 201 Response

```json
{
  "id": "string",
  "rxImage": "string",
  "title": "string",
  "desc": "string"
}
```

<h3 id="create-patient-medication-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|OK|[PatientMedication](#schemapatientmedication)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get patient's medication details

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/patients/{patient_id}/medications/details \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/patients/{patient_id}/medications/details HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/medications/details',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/medications/details',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/patients/{patient_id}/medications/details',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/patients/{patient_id}/medications/details', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/medications/details");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/patients/{patient_id}/medications/details", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /patients/{patient_id}/medications/details`

Get patient's medication details / prices

<h3 id="get-patient's-medication-details-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|
|postal_code|query|string|false|postal code to find accurate pricing|
|medication_brand|query|string|false|Set whether this is a brand or generic medication|
|medication_qty|query|string|false|Quantity of the medication to search|
|medication_gsn|query|string|false|Filter the current state of the medication search by changing a filter|

> Example responses

> 200 Response

```json
[
  {
    "drugInfo": {
      "brandName": "string",
      "description": "string",
      "genericName": "string"
    },
    "drugs": [
      {
        "pharmacy": {
          "name": "string",
          "streetAddress": "string",
          "city": "string",
          "state": "string",
          "postal_code": "string",
          "latitude": 0,
          "longitude": 0,
          "hoursOfOperation": "string",
          "phone": "string",
          "npi": "string",
          "distance": "string",
          "listingSlug": "string",
          "pharmacyLogo": {
            "imgUrl": "string",
            "imgStyle": "string",
            "brand": "string",
            "url": "string"
          }
        },
        "drug": {
          "ndcCode": 0,
          "brandGenericIndicator": "string",
          "gsn": "string",
          "drugRanking": "string",
          "quantity": "string",
          "quantityRanking": "string",
          "labelName": "string"
        },
        "pricing": {
          "price": "string",
          "discount": 0,
          "group": "string",
          "bin": "string",
          "pcn": "string",
          "couponCode": "string"
        }
      }
    ],
    "forms": {
      "form": "string",
      "gsn": 0,
      "isSelected": true,
      "ranking": "string"
    },
    "names": [
      {
        "drugName": "string",
        "brandGenericIndicator": "string",
        "isSelected": true
      }
    ],
    "quantities": [
      {
        "quantity": 0,
        "quantityUom": "string",
        "gsn": 0,
        "isSelected": true,
        "ranking": 0
      }
    ],
    "strengths": [
      {
        "strength": 0,
        "gsn": 0,
        "isSelected": true,
        "ranking": 0
      }
    ],
    "meta": {
      "brandName": "string",
      "gsn": 0,
      "genericName": "string",
      "ndc": "string",
      "drugDescription": 0,
      "image": [
        "string"
      ],
      "lowPrice": "string",
      "highPrice": "string"
    },
    "drugInfoDetails": {
      "brandName": "string",
      "genericName": "string",
      "drugDescription": "string",
      "administerInstructions": "string",
      "contraindications": "string",
      "disclaimer": "string",
      "interactions": "string",
      "missedDoseInfo": "string",
      "monitorReactions": "string",
      "sideEffects": "string",
      "storageInfo": "string"
    }
  }
]
```

<h3 id="get-patient's-medication-details-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<h3 id="get-patient's-medication-details-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[PatientMedicationDetails](#schemapatientmedicationdetails)]|false|none|none|
|» drugInfo|object|false|none|none|
|»» brandName|string|false|none|Brand name of the medication|
|»» description|string|false|none|What the medication does|
|»» genericName|string|false|none|Generic name of the medication|
|» drugs|[object]|false|none|none|
|»» pharmacy|object|false|none|none|
|»»» name|string|false|none|Name of the pharmacy|
|»»» streetAddress|string|false|none|Street address of the pharmacy|
|»»» city|string|false|none|Name of the pharmacy|
|»»» state|string|false|none|Street address of the pharmacy|
|»»» postal_code|string|false|none|Name of the pharmacy|
|»»» latitude|integer|false|none|Street address of the pharmacy|
|»»» longitude|integer|false|none|Name of the pharmacy|
|»»» hoursOfOperation|string|false|none|Street address of the pharmacy|
|»»» phone|string|false|none|Name of the pharmacy|
|»»» npi|string|false|none|Street address of the pharmacy|
|»»» distance|string|false|none|Name of the pharmacy|
|»»» listingSlug|string|false|none|Street address of the pharmacy|
|»»» pharmacyLogo|object|false|none|none|
|»»»» imgUrl|string|false|none|Pharmacy Logo|
|»»»» imgStyle|string|false|none|Pharmacy Logo recommended styling|
|»»»» brand|string|false|none|Pharmacy Logo Name|
|»»»» url|string|false|none|Pharmacy Url location|
|»»» drug|object|false|none|none|
|»»»» ndcCode|integer|false|none|Drug's NDC code|
|»»»» brandGenericIndicator|string|false|none|Medication Type|
|»»»» gsn|string|false|none|current filter state of medication|
|»»»» drugRanking|string|false|none|position of drug options|
|»»»» quantity|string|false|none|Medication quantity options|
|»»»» quantityRanking|string|false|none|Current quantity option|
|»»»» labelName|string|false|none|Filtered medication label|
|»»» pricing|object|false|none|none|
|»»»» price|string|false|none|Price from discount|
|»»»» discount|integer|false|none|amount discounted from price|
|»»»» group|string|false|none|medication routing information|
|»»»» bin|string|false|none|medication routing information|
|»»»» pcn|string|false|none|3rd party company code|
|»»»» couponCode|string|false|none|pharmacy discount coupon code|
|»»» forms|object|false|none|none|
|»»»» form|string|false|none|type of medication|
|»»»» gsn|integer|false|none|filter option|
|»»»» isSelected|boolean|false|none|none|
|»»»» ranking|string|false|none|filter option position|
|»»» names|[object]|false|none|none|
|»»»» drugName|string|false|none|medication name option|
|»»»» brandGenericIndicator|string|false|none|brand category|
|»»»» isSelected|boolean|false|none|none|
|»»» quantities|[object]|false|none|none|
|»»»» quantity|integer|false|none|amount option|
|»»»» quantityUom|string|false|none|quantity form type|
|»»»» gsn|integer|false|none|filter option value|
|»»»» isSelected|boolean|false|none|none|
|»»»» ranking|integer|false|none|filter option position|
|»»» strengths|[object]|false|none|none|
|»»»» strength|integer|false|none|amount option|
|»»»» gsn|integer|false|none|filter option value|
|»»»» isSelected|boolean|false|none|none|
|»»»» ranking|integer|false|none|filter option position|
|»»» meta|object|false|none|none|
|»»»» brandName|string|false|none|brand name of the medication|
|»»»» gsn|integer|false|none|filter option|
|»»»» genericName|string|false|none|generic name of the medication|
|»»»» ndc|string|false|none|mational drug code directory value|
|»»»» drugDescription|integer|false|none|medication intention|
|»»»» image|[string]|false|none|none|
|»»»» lowPrice|string|false|none|lowest pricing option found|
|»»»» highPrice|string|false|none|highest pricing option found|
|»»» drugInfoDetails|object|false|none|none|
|»»»» brandName|string|false|none|brand name of the medication|
|»»»» genericName|string|false|none|generic name of the medication|
|»»»» drugDescription|string|false|none|medication intention|
|»»»» administerInstructions|string|false|none|drug usage instructions|
|»»»» contraindications|string|false|none|drug precautions|
|»»»» disclaimer|string|false|none|disclaimer summary|
|»»»» interactions|string|false|none|drug interactions|
|»»»» missedDoseInfo|string|false|none|missed dose assistance|
|»»»» monitorReactions|string|false|none|monitor reactions of medications|
|»»»» sideEffects|string|false|none|possible side effects from taking medication|
|»»»» storageInfo|string|false|none|medicine storage information|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get a patient medication

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/patients/{patient_id}/medications/{medication_id} \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/patients/{patient_id}/medications/{medication_id} HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/medications/{medication_id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/medications/{medication_id}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/patients/{patient_id}/medications/{medication_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/patients/{patient_id}/medications/{medication_id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/medications/{medication_id}");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/patients/{patient_id}/medications/{medication_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /patients/{patient_id}/medications/{medication_id}`

Get a patient medication

<h3 id="get-a-patient-medication-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|
|medication_id|path|string|true|Medication ID|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "rxImage": "string",
  "title": "string",
  "desc": "string"
}
```

<h3 id="get-a-patient-medication-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[PatientMedication](#schemapatientmedication)|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Update a patient medication

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.test/patients/{patient_id}/medications/{medication_id} \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Authorization: API_KEY'

```

```http
PUT https://api.test/patients/{patient_id}/medications/{medication_id} HTTP/1.1
Host: api.test
Content-Type: application/x-www-form-urlencoded

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/medications/{medication_id}',
  method: 'put',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "start_date": "2019-06-18",
  "end_date": "2019-06-18",
  "quantity": 0,
  "dose": 0,
  "units": "string",
  "take": 0,
  "form_id": 0,
  "route_id": 0,
  "interval_id": 0,
  "refill_count": 0,
  "per_refill_count": 0,
  "instructions": "string"
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/medications/{medication_id}',
{
  method: 'PUT',
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
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Authorization' => 'API_KEY'
}

result = RestClient.put 'https://api.test/patients/{patient_id}/medications/{medication_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Authorization': 'API_KEY'
}

r = requests.put('https://api.test/patients/{patient_id}/medications/{medication_id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/medications/{medication_id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
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
        "Content-Type": []string{"application/x-www-form-urlencoded"},
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://api.test/patients/{patient_id}/medications/{medication_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /patients/{patient_id}/medications/{medication_id}`

Update a patient medication

> Body parameter

```yaml
start_date: '2019-06-18'
end_date: '2019-06-18'
quantity: 0
dose: 0
units: string
take: 0
form_id: 0
route_id: 0
interval_id: 0
refill_count: 0
per_refill_count: 0
instructions: string

```

<h3 id="update-a-patient-medication-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|
|medication_id|path|string|true|Medication ID|
|start_date|body|string(date)|true|Medication start date|
|end_date|body|string(date)|false|Medication end date|
|quantity|body|integer|false|Initial quantity (count)|
|dose|body|integer|false|Strength|
|units|body|string|false|Unit of measure|
|take|body|integer|false|How many to take|
|form_id|body|integer|false|Form factor|
|route_id|body|integer|false|Route of administration|
|interval_id|body|integer|false|Frequency|
|refill_count|body|integer|false|Number of refills|
|per_refill_count|body|integer|false|Number of units per refill|
|instructions|body|string|false|Instructions for taking the medication|

<h3 id="update-a-patient-medication-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get patient products

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/patients/{patient_id}/products \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/patients/{patient_id}/products HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/products',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/products',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/patients/{patient_id}/products',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/patients/{patient_id}/products', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/products");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/patients/{patient_id}/products", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /patients/{patient_id}/products`

Get patient products

<h3 id="get-patient-products-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|

> Example responses

> 200 Response

```json
[
  {
    "condition": [
      {
        "id": 0,
        "partner_id": 0,
        "title": "string",
        "slug": "string",
        "offsite_product": 0,
        "product_url": "string",
        "category_id": 0,
        "description": "string",
        "featured_image": "string",
        "price": "string",
        "compare_at_price": "string",
        "enabled": 0,
        "created_at": "string",
        "updated_at": "string",
        "deleted_at": "string",
        "images": [
          {
            "id": 0,
            "partner_product_id": 0,
            "url": "string",
            "created_at": "string",
            "updated_at": "string"
          }
        ]
      }
    ]
  }
]
```

<h3 id="get-patient-products-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<h3 id="get-patient-products-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[PatientProducts](#schemapatientproducts)]|false|none|none|
|» condition|[object]|false|none|none|
|»» id|integer|false|none|product id|
|»» partner_id|integer|false|none|id of the 3rd party partner|
|»» title|string|false|none|product title|
|»» slug|string|false|none|keyword slug|
|»» offsite_product|integer|false|none|internal or external product|
|»» product_url|string|false|none|url to product page|
|»» category_id|integer|false|none|product category id|
|»» description|string|false|none|product description|
|»» featured_image|string|false|none|main image of product|
|»» price|string|false|none|current product price|
|»» compare_at_price|string|false|none|original product page|
|»» enabled|integer|false|none|product active or inactive|
|»» created_at|string|false|none|product creation date|
|»» updated_at|string|false|none|product last updated date|
|»» deleted_at|string|false|none|product deletion date|
|»» images|[object]|false|none|none|
|»»» id|integer|false|none|product image id|
|»»» partner_product_id|integer|false|none|partners product id|
|»»» url|string|false|none|url to product image|
|»»» created_at|string|false|none|product image creation date|
|»»» updated_at|string|false|none|product image last updated date|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get patient product categories

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/patients/{patient_id}/products/categories \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/patients/{patient_id}/products/categories HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/products/categories',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/products/categories',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/patients/{patient_id}/products/categories',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/patients/{patient_id}/products/categories', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/products/categories");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/patients/{patient_id}/products/categories", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /patients/{patient_id}/products/categories`

Get patient product categories

<h3 id="get-patient-product-categories-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|

> Example responses

> 200 Response

```json
[
  {
    "id": "string",
    "name": "string",
    "slug": "string",
    "created_at": "string",
    "updated_at": "string"
  }
]
```

<h3 id="get-patient-product-categories-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<h3 id="get-patient-product-categories-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[PatientProductCategories](#schemapatientproductcategories)]|false|none|none|
|» id|string|false|none|category id|
|» name|string|false|none|category label|
|» slug|string|false|none|category keywords|
|» created_at|string|false|none|creation date of this category|
|» updated_at|string|false|none|last date the category was updated|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Create a patient share

> Code samples

```shell
# You can also use wget
curl -X POST https://api.test/patients/{patient_id}/shares \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
POST https://api.test/patients/{patient_id}/shares HTTP/1.1
Host: api.test
Content-Type: application/x-www-form-urlencoded
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/shares',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "name": "string",
  "anonymous": true,
  "options": "string"
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/shares',
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
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Accept' => 'application/json',
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'https://api.test/patients/{patient_id}/shares',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.post('https://api.test/patients/{patient_id}/shares', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/shares");
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
        "Content-Type": []string{"application/x-www-form-urlencoded"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.test/patients/{patient_id}/shares", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /patients/{patient_id}/shares`

Create a patient share

> Body parameter

```yaml
name: string
anonymous: true
options: string

```

<h3 id="create-a-patient-share-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|
|name|body|string|true|Name of the document|
|anonymous|body|boolean|true|Anonymous access|
|options|body|string|true|Options JSON  { "data" : [ "activity-plan", "appointments", "diagnoses", "goals", "health-metrics", "medications","problems"]}|

> Example responses

> 201 Response

```json
{
  "id": 0,
  "patient_id": 0,
  "name": "string",
  "hash": "string",
  "created": {
    "date": "2019-06-18T20:09:43Z",
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  },
  "anonymous": true,
  "active": true,
  "expiration_date": "2019-06-18T20:09:43Z",
  "share_url": "string",
  "image_url": "string",
  "image": "string",
  "options": {
    "data": [
      "allergies"
    ]
  }
}
```

<h3 id="create-a-patient-share-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|[Share](#schemashare)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get all patient shares

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/patients/{patient_id}/shares \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/patients/{patient_id}/shares HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/shares',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/shares',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/patients/{patient_id}/shares',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/patients/{patient_id}/shares', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/shares");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/patients/{patient_id}/shares", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /patients/{patient_id}/shares`

Get all patient shares

<h3 id="get-all-patient-shares-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "patient_id": 0,
    "name": "string",
    "hash": "string",
    "created": {
      "date": "2019-06-18T20:09:43Z",
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    },
    "anonymous": true,
    "active": true,
    "expiration_date": "2019-06-18T20:09:43Z",
    "share_url": "string",
    "image_url": "string",
    "image": "string",
    "options": {
      "data": [
        "allergies"
      ]
    }
  }
]
```

<h3 id="get-all-patient-shares-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<h3 id="get-all-patient-shares-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Share](#schemashare)]|false|none|none|
|» id|integer|false|none|Identifier|
|» patient_id|integer|false|none|Patient Id|
|» name|string|false|none|Share document name|
|» hash|string|false|none|Unique Identifier for a share|
|» created|[CreatedObject](#schemacreatedobject)|false|none|Information on the individual who created the record|
|»» date|string(date-time)|false|none|Date and time of record creation|
|»» first_name|string|false|none|First name of individual who created the record|
|»» last_name|string|false|none|Last name of individual who created the record|
|»» user_id|integer|false|none|User ID for individual who created the record|
|» anonymous|boolean|false|none|Anonymous access|
|» active|boolean|false|none|Active|
|» expiration_date|string(date-time)|false|none|Share expiration date and time|
|» share_url|string|false|none|Direct share url|
|» image_url|string|false|none|Share QR code image url|
|» image|string|false|none|Share QR code image|
|» options|object|false|none|Data object|
|»» data|[string]|false|none|Data elements|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get a patient share

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/patients/{patient_id}/shares/{share_id} \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/patients/{patient_id}/shares/{share_id} HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/shares/{share_id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/shares/{share_id}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/patients/{patient_id}/shares/{share_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/patients/{patient_id}/shares/{share_id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/shares/{share_id}");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/patients/{patient_id}/shares/{share_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /patients/{patient_id}/shares/{share_id}`

Get a patient share

<h3 id="get-a-patient-share-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|
|share_id|path|integer|true|Share ID|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "patient_id": 0,
  "name": "string",
  "hash": "string",
  "created": {
    "date": "2019-06-18T20:09:43Z",
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  },
  "anonymous": true,
  "active": true,
  "expiration_date": "2019-06-18T20:09:43Z",
  "share_url": "string",
  "image_url": "string",
  "image": "string",
  "options": {
    "data": [
      "allergies"
    ]
  }
}
```

<h3 id="get-a-patient-share-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[Share](#schemashare)|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Send a patient share

> Code samples

```shell
# You can also use wget
curl -X POST https://api.test/patients/{patient_id}/shares/{share_id}/send \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Authorization: API_KEY'

```

```http
POST https://api.test/patients/{patient_id}/shares/{share_id}/send HTTP/1.1
Host: api.test
Content-Type: application/x-www-form-urlencoded

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/patients/{patient_id}/shares/{share_id}/send',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "to": "string",
  "first_name": "string",
  "last_name": "string",
  "type": "mms"
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Authorization':'API_KEY'

};

fetch('https://api.test/patients/{patient_id}/shares/{share_id}/send',
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
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'https://api.test/patients/{patient_id}/shares/{share_id}/send',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Authorization': 'API_KEY'
}

r = requests.post('https://api.test/patients/{patient_id}/shares/{share_id}/send', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/patients/{patient_id}/shares/{share_id}/send");
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
        "Content-Type": []string{"application/x-www-form-urlencoded"},
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.test/patients/{patient_id}/shares/{share_id}/send", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /patients/{patient_id}/shares/{share_id}/send`

Send a patient share

> Body parameter

```yaml
to: string
first_name: string
last_name: string
type: mms

```

<h3 id="send-a-patient-share-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|path|string|true|Patient ID|
|share_id|path|integer|true|Share ID|
|to|body|string|true|Either phone number or email address|
|first_name|body|string|true|First name|
|last_name|body|string|true|Last name|
|type|body|string|true|Either mms or email|

#### Enumerated Values

|Parameter|Value|
|---|---|
|type|mms|
|type|email|

<h3 id="send-a-patient-share-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

<h1 id="inxite-api-assessments">Assessments</h1>

## Create SOAR assessment

> Code samples

```shell
# You can also use wget
curl -X POST https://api.test/soar \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
POST https://api.test/soar HTTP/1.1
Host: api.test
Content-Type: application/x-www-form-urlencoded
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/soar',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "patient_id": 0,
  "date_time": "2019-06-18T20:09:43Z"
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/soar',
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
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Accept' => 'application/json',
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'https://api.test/soar',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.post('https://api.test/soar', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/soar");
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
        "Content-Type": []string{"application/x-www-form-urlencoded"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.test/soar", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /soar`

Create SOAR assessment

> Body parameter

```yaml
patient_id: 0
date_time: '2019-06-18T20:09:43Z'

```

<h3 id="create-soar-assessment-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|patient_id|body|integer|true|Patient ID|
|date_time|body|string(date-time)|false|Assessment completion date and time|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "body": {
    "PatientID": 0,
    "RequestTime": "2019-06-18T20:09:43Z",
    "ResponseTime": "2019-06-18T20:09:43Z",
    "Filename": "string",
    "Errors": true,
    "report": "string",
    "OARS": {
      "Overall": {
        "risk": "L",
        "score": 0
      },
      "EL": {
        "risk": "L",
        "score": 0
      },
      "AB": {
        "risk": "L",
        "score": 0
      }
    },
    "IDAS": {
      "PHQ": {
        "risk": "L",
        "score": 0
      },
      "GAD": {
        "risk": "L",
        "score": 0
      }
    }
  }
}
```

<h3 id="create-soar-assessment-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|

<h3 id="create-soar-assessment-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» statusCode|integer|false|none|The response status code|
|» body|object|false|none|none|
|»» PatientID|integer|false|none|none|
|»» RequestTime|string(date-time)|false|none|none|
|»» ResponseTime|string(date-time)|false|none|none|
|»» Filename|string|false|none|The name of the return PDF report|
|»» Errors|boolean|false|none|True if errors exist, else false|
|»» report|string|false|none|The Base64-encoded PDF report|
|»» OARS|object|false|none|none|
|»»» Overall|[SoarAssessmentCategoryScore](#schemasoarassessmentcategoryscore)|false|none|none|
|»»»» risk|string|false|none|none|
|»»»» score|integer|false|none|none|
|»»» EL|[SoarAssessmentCategoryScore](#schemasoarassessmentcategoryscore)|false|none|none|
|»»» AB|[SoarAssessmentCategoryScore](#schemasoarassessmentcategoryscore)|false|none|none|
|»» IDAS|object|false|none|none|
|»»» PHQ|[SoarAssessmentCategoryScore](#schemasoarassessmentcategoryscore)|false|none|none|
|»»» GAD|[SoarAssessmentCategoryScore](#schemasoarassessmentcategoryscore)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|risk|L|
|risk|M|
|risk|H|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

<h1 id="inxite-api-communications">Communications</h1>

## Send Email(s)

> Code samples

```shell
# You can also use wget
curl -X POST https://api.test/emails \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Authorization: API_KEY'

```

```http
POST https://api.test/emails HTTP/1.1
Host: api.test
Content-Type: application/x-www-form-urlencoded

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/emails',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "to": [
    "string"
  ],
  "entity": "string",
  "entity_id": "string"
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Authorization':'API_KEY'

};

fetch('https://api.test/emails',
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
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'https://api.test/emails',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Authorization': 'API_KEY'
}

r = requests.post('https://api.test/emails', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/emails");
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
        "Content-Type": []string{"application/x-www-form-urlencoded"},
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.test/emails", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /emails`

Send Email(s) used for Shares but not using anymore, replace by /shares/{shareId}/send

> Body parameter

```yaml
to:
  - string
entity: string
entity_id: string

```

<h3 id="send-email(s)-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|to|body|[string]|true|Array of to email addresses|
|entity|body|string|true|Identifier for what data needs to send like `Share`|
|entity_id|body|string|true|Entity Id, identifier for the entity|

<h3 id="send-email(s)-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|None|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Data found|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Errors|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Send Message(s)

> Code samples

```shell
# You can also use wget
curl -X POST https://api.test/messages \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Authorization: API_KEY'

```

```http
POST https://api.test/messages HTTP/1.1
Host: api.test
Content-Type: application/x-www-form-urlencoded

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/messages',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "to": [
    "string"
  ],
  "entity": "string",
  "entity_id": "string"
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Authorization':'API_KEY'

};

fetch('https://api.test/messages',
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
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'https://api.test/messages',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Authorization': 'API_KEY'
}

r = requests.post('https://api.test/messages', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/messages");
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
        "Content-Type": []string{"application/x-www-form-urlencoded"},
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.test/messages", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /messages`

Send Message(s) used for Shares but not using anymore, replace by /shares/{shareId}/send

> Body parameter

```yaml
to:
  - string
entity: string
entity_id: string

```

<h3 id="send-message(s)-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|to|body|[string]|true|Array of to phone numbers|
|entity|body|string|true|Identifier for what data needs to send like `Share`|
|entity_id|body|string|true|Entity Id, identifier for the entity|

<h3 id="send-message(s)-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|None|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Data found|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Errors|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Send Notification(s)

> Code samples

```shell
# You can also use wget
curl -X POST https://api.test/notifications \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
POST https://api.test/notifications HTTP/1.1
Host: api.test
Content-Type: application/x-www-form-urlencoded
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/notifications',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "type": "string",
  "action": "string",
  "patient_id": 0,
  "user_id": 0
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/notifications',
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
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Accept' => 'application/json',
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'https://api.test/notifications',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.post('https://api.test/notifications', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/notifications");
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
        "Content-Type": []string{"application/x-www-form-urlencoded"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.test/notifications", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /notifications`

Send Notification(s)

> Body parameter

```yaml
type: string
action: string
patient_id: 0
user_id: 0

```

<h3 id="send-notification(s)-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|type|body|string|true|The type of notification (allergy, medication, etc.)|
|action|body|string|true|The action completed (added, updated, etc.)|
|patient_id|body|integer|false|The patient ID|
|user_id|body|integer|false|The user ID for the notification recipient|

> Example responses

> 201 Response

```json
{
  "id": 0,
  "patient_id": 0,
  "type": "string",
  "action": "string"
}
```

<h3 id="send-notification(s)-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|[Notification](#schemanotification)|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Data found|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Errors|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

<h1 id="inxite-api-organizations">Organizations</h1>

## Get all organizations

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/organizations \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/organizations HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/organizations',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/organizations',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/organizations',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/organizations', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/organizations");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/organizations", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /organizations`

Get all organizations or search by name or code

<h3 id="get-all-organizations-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|name|query|string|false|Organization name|
|code|query|string|false|Organization code|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "name": "string",
    "code": "string",
    "street": "string",
    "city": "string",
    "state": "string",
    "county": "string",
    "postal_code": "string",
    "country_code": "string",
    "phone": "string",
    "fax": "string",
    "email": "string"
  }
]
```

<h3 id="get-all-organizations-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Errors|None|

<h3 id="get-all-organizations-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Organization](#schemaorganization)]|false|none|none|
|» id|integer|false|none|Organization Id|
|» name|string|false|none|Organization name|
|» code|string|false|none|Organization code|
|» street|string|false|none|Organization street|
|» city|string|false|none|Organization city|
|» state|string|false|none|Organization state like OH, NY|
|» county|string|false|none|Organization county|
|» postal_code|string|false|none|Organization 5 digit postal code|
|» country_code|string|false|none|Organization country code USA|
|» phone|string|false|none|Organization contact number|
|» fax|string|false|none|Organization fax number|
|» email|string|false|none|Organization email|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get a organization

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/organizations/{organization_id} \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/organizations/{organization_id} HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/organizations/{organization_id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/organizations/{organization_id}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/organizations/{organization_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/organizations/{organization_id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/organizations/{organization_id}");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/organizations/{organization_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /organizations/{organization_id}`

Get a organization

<h3 id="get-a-organization-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_id|path|integer|true|Organization ID|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "name": "string",
  "code": "string",
  "street": "string",
  "city": "string",
  "state": "string",
  "county": "string",
  "postal_code": "string",
  "country_code": "string",
  "phone": "string",
  "fax": "string",
  "email": "string"
}
```

<h3 id="get-a-organization-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[Organization](#schemaorganization)|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Errors|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get all Health Scores for an organization

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/organizations/{organization_id}/healthscores \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/organizations/{organization_id}/healthscores HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/organizations/{organization_id}/healthscores',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/organizations/{organization_id}/healthscores',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/organizations/{organization_id}/healthscores',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/organizations/{organization_id}/healthscores', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/organizations/{organization_id}/healthscores");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/organizations/{organization_id}/healthscores", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /organizations/{organization_id}/healthscores`

Get all Health Scores for an organization

<h3 id="get-all-health-scores-for-an-organization-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_id|path|string|true|Organization ID|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "patient_id": 0,
    "score": 0,
    "metrics": [
      {
        "id": 0,
        "category": "string",
        "level": "string",
        "metric_id": 0,
        "metric_level": "string",
        "name": "string",
        "score": 0,
        "source": {
          "id": 0,
          "module": "string"
        },
        "unit": "string",
        "value": {
          "current": "string",
          "text": "string"
        },
        "created": {
          "date": "2019-06-18T20:09:43Z",
          "first_name": "string",
          "last_name": "string",
          "user_id": 0
        },
        "updated": {
          "date": "2019-06-18T20:09:43Z",
          "first_name": "string",
          "last_name": "string",
          "user_id": 0
        }
      }
    ],
    "created": {
      "date": "2019-06-18T20:09:43Z",
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    }
  }
]
```

<h3 id="get-all-health-scores-for-an-organization-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|

<h3 id="get-all-health-scores-for-an-organization-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[HealthScore](#schemahealthscore)]|false|none|none|
|» id|integer|false|none|none|
|» patient_id|integer|false|none|none|
|» score|integer|false|none|none|
|» metrics|[[HealthMetricValue](#schemahealthmetricvalue)]|false|none|none|
|»» id|integer|false|none|none|
|»» category|string|false|none|none|
|»» level|string|false|none|none|
|»» metric_id|integer|false|none|none|
|»» metric_level|string|false|none|none|
|»» name|string|false|none|none|
|»» score|integer|false|none|none|
|»» source|object|false|none|none|
|»»» id|integer|false|none|none|
|»»» module|string|false|none|none|
|»» unit|string|false|none|none|
|»» value|object|false|none|none|
|»»» current|string|false|none|none|
|»»» text|string|false|none|none|
|»» created|[CreatedObject](#schemacreatedobject)|false|none|Information on the individual who created the record|
|»»» date|string(date-time)|false|none|Date and time of record creation|
|»»» first_name|string|false|none|First name of individual who created the record|
|»»» last_name|string|false|none|Last name of individual who created the record|
|»»» user_id|integer|false|none|User ID for individual who created the record|
|»» updated|[UpdatedObject](#schemaupdatedobject)|false|none|Information on the individual who last updated the record|
|»»» date|string(date-time)|false|none|Date and time of the most recent record update|
|»»» first_name|string|false|none|First name of individual who last updated the record|
|»»» last_name|string|false|none|Last name of individual who last updated the record|
|»»» user_id|integer|false|none|User ID for individual who last updated the record|
|»» created|[CreatedObject](#schemacreatedobject)|false|none|Information on the individual who created the record|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

<h1 id="inxite-api-reference">Reference</h1>

## Get available medication forms

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/reference/medication_forms \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/reference/medication_forms HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/reference/medication_forms',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/reference/medication_forms',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/reference/medication_forms',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/reference/medication_forms', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/reference/medication_forms");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/reference/medication_forms", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /reference/medication_forms`

Get available medication forms

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "route": "Capsule"
  }
]
```

<h3 id="get-available-medication-forms-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<h3 id="get-available-medication-forms-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|integer|false|none|none|
|» route|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|route|Capsule|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get available medication frequencies

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/reference/medication_frequencies \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/reference/medication_frequencies HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/reference/medication_frequencies',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/reference/medication_frequencies',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/reference/medication_frequencies',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/reference/medication_frequencies', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/reference/medication_frequencies");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/reference/medication_frequencies", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /reference/medication_frequencies`

Get available medication frequencies

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "route": "a.c. (Before meals)"
  }
]
```

<h3 id="get-available-medication-frequencies-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<h3 id="get-available-medication-frequencies-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|integer|false|none|none|
|» route|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|route|a.c. (Before meals)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get available medication routes

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/reference/medication_routes \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/reference/medication_routes HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/reference/medication_routes',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/reference/medication_routes',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/reference/medication_routes',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/reference/medication_routes', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/reference/medication_routes");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/reference/medication_routes", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /reference/medication_routes`

Get available medication routes

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "route": "AAA (Apply to affected area)"
  }
]
```

<h3 id="get-available-medication-routes-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<h3 id="get-available-medication-routes-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|integer|false|none|none|
|» route|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|route|AAA (Apply to affected area)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get available medication units

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/reference/medication_units \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/reference/medication_units HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/reference/medication_units',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/reference/medication_units',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/reference/medication_units',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/reference/medication_units', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/reference/medication_units");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/reference/medication_units", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /reference/medication_units`

Get available medication units

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "route": "mg"
  }
]
```

<h3 id="get-available-medication-units-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<h3 id="get-available-medication-units-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|integer|false|none|none|
|» route|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|route|mg|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get all specialties

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/reference/specialty \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/reference/specialty HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/reference/specialty',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/reference/specialty',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/reference/specialty',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/reference/specialty', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/reference/specialty");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/reference/specialty", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /reference/specialty`

Get all specialties

<h3 id="get-all-specialties-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|name|query|string|false|Name of specialty|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "name": "string"
  }
]
```

<h3 id="get-all-specialties-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|

<h3 id="get-all-specialties-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Specialty](#schemaspecialty)]|false|none|none|
|» id|integer|false|none|Specialty ID|
|» name|string|false|none|Name of specialty|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get specialty by ID

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/reference/specialty/{specialty_id} \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/reference/specialty/{specialty_id} HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/reference/specialty/{specialty_id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/reference/specialty/{specialty_id}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/reference/specialty/{specialty_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/reference/specialty/{specialty_id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/reference/specialty/{specialty_id}");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/reference/specialty/{specialty_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /reference/specialty/{specialty_id}`

Get specialty by ID

<h3 id="get-specialty-by-id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|specialty_id|path|integer|true|Specialty ID|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "name": "string"
}
```

<h3 id="get-specialty-by-id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[Specialty](#schemaspecialty)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get all langauges

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/reference/languages \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/reference/languages HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/reference/languages',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/reference/languages',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/reference/languages',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/reference/languages', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/reference/languages");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/reference/languages", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /reference/languages`

Get all langauges

<h3 id="get-all-langauges-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|name|query|string|false|Name of language|

> Example responses

> 200 Response

```json
[
  {
    "name": "string",
    "id": "string"
  }
]
```

<h3 id="get-all-langauges-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<h3 id="get-all-langauges-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[LanguageObject](#schemalanguageobject)]|false|none|[Information on language]|
|» name|string|false|none|Name of the language|
|» id|string|false|none|Lanuage ID|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get a langauge

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/reference/languages/{language_id} \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/reference/languages/{language_id} HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/reference/languages/{language_id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/reference/languages/{language_id}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/reference/languages/{language_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/reference/languages/{language_id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/reference/languages/{language_id}");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/reference/languages/{language_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /reference/languages/{language_id}`

Get a langauge

<h3 id="get-a-langauge-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|language_id|path|string|true|Language ID|

> Example responses

> 200 Response

```json
{
  "name": "string",
  "id": "string"
}
```

<h3 id="get-a-langauge-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[LanguageObject](#schemalanguageobject)|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No results found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

<h1 id="inxite-api-share-requests">Share Requests</h1>

## Request share Access

> Code samples

```shell
# You can also use wget
curl -X POST https://api.test/shares/{shareHash}/requests \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Accept: application/json'

```

```http
POST https://api.test/shares/{shareHash}/requests HTTP/1.1
Host: api.test
Content-Type: application/x-www-form-urlencoded
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.test/shares/{shareHash}/requests',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "firstname": "string",
  "lastname": "string",
  "organization": "string",
  "email": "string",
  "phone": "string",
  "postal_code": "string"
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json'

};

fetch('https://api.test/shares/{shareHash}/requests',
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
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.test/shares/{shareHash}/requests',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Accept': 'application/json'
}

r = requests.post('https://api.test/shares/{shareHash}/requests', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/shares/{shareHash}/requests");
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
        "Content-Type": []string{"application/x-www-form-urlencoded"},
        "Accept": []string{"application/json"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.test/shares/{shareHash}/requests", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /shares/{shareHash}/requests`

Request share access, it uses user_id if request comes with token or else response with 401 No User Information Found.

> Body parameter

```yaml
firstname: string
lastname: string
organization: string
email: string
phone: string
postal_code: string

```

<h3 id="request-share-access-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|shareHash|path|string|true|Share Identifier (Not row id, use Hash)|
|firstname|body|string|false|Requester first name, Required if no token|
|lastname|body|string|false|Requester last name, Required if no token|
|organization|body|string|false|Requester organization|
|email|body|string|false|Requester email address|
|phone|body|string|false|Requester phone number|
|postal_code|body|string|false|Requester postal code|

> Example responses

> 201 Response

```json
{
  "name": "string",
  "request_status": "declined",
  "share_status": true,
  "share_hash": "string",
  "request_id": "string",
  "share_direct_image_url": "string",
  "expiration_date": "2019-06-18T20:09:43Z",
  "share": {
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  },
  "request": {
    "organization": "string",
    "phone": "string",
    "email": "string",
    "postal_code": "string",
    "access_type": "email",
    "created": {
      "date": "2019-06-18T20:09:43Z",
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    },
    "updated": {
      "date": "2019-06-18T20:09:43Z",
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    },
    "data": "string"
  }
}
```

<h3 id="request-share-access-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|[ShareRequest](#schemasharerequest)|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Data found|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Errors|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Code Expired or No User information found|None|

<aside class="success">
This operation does not require authentication
</aside>

## Get Particular request status or data

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/shares/{shareHash}/requests/{requestHash} \
  -H 'Accept: application/json'

```

```http
GET https://api.test/shares/{shareHash}/requests/{requestHash} HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.test/shares/{shareHash}/requests/{requestHash}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.test/shares/{shareHash}/requests/{requestHash}',
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
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.test/shares/{shareHash}/requests/{requestHash}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.test/shares/{shareHash}/requests/{requestHash}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/shares/{shareHash}/requests/{requestHash}");
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

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/shares/{shareHash}/requests/{requestHash}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /shares/{shareHash}/requests/{requestHash}`

Get Particular request status or data

<h3 id="get-particular-request-status-or-data-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|shareHash|path|string|true|Share Identifier (Not row id, use Hash)|
|requestHash|path|string|true|Request Identifier (Not row id, use Hash)|

> Example responses

> 200 Response

```json
{
  "name": "string",
  "request_status": "declined",
  "share_status": true,
  "share_hash": "string",
  "request_id": "string",
  "share_direct_image_url": "string",
  "expiration_date": "2019-06-18T20:09:43Z",
  "share": {
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  },
  "request": {
    "organization": "string",
    "phone": "string",
    "email": "string",
    "postal_code": "string",
    "access_type": "email",
    "created": {
      "date": "2019-06-18T20:09:43Z",
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    },
    "updated": {
      "date": "2019-06-18T20:09:43Z",
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    },
    "data": "string"
  }
}
```

<h3 id="get-particular-request-status-or-data-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[ShareRequest](#schemasharerequest)|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Data found|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Errors|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Code Expired or No User information found|None|

<aside class="success">
This operation does not require authentication
</aside>

## Update an existing request

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.test/shares/{shareHash}/requests/{requestHash} \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Accept: application/json'

```

```http
PATCH https://api.test/shares/{shareHash}/requests/{requestHash} HTTP/1.1
Host: api.test
Content-Type: application/x-www-form-urlencoded
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.test/shares/{shareHash}/requests/{requestHash}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "status": "approve"
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json'

};

fetch('https://api.test/shares/{shareHash}/requests/{requestHash}',
{
  method: 'PATCH',
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
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://api.test/shares/{shareHash}/requests/{requestHash}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Accept': 'application/json'
}

r = requests.patch('https://api.test/shares/{shareHash}/requests/{requestHash}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/shares/{shareHash}/requests/{requestHash}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
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
        "Content-Type": []string{"application/x-www-form-urlencoded"},
        "Accept": []string{"application/json"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://api.test/shares/{shareHash}/requests/{requestHash}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PATCH /shares/{shareHash}/requests/{requestHash}`

Update an existing request

> Body parameter

```yaml
status: approve

```

<h3 id="update-an-existing-request-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|shareHash|path|string|true|Share Identifier (Not row id, use Hash)|
|requestHash|path|string|true|Request Identifier (Not row id, use Hash)|
|status|body|string|false|Request Status|

#### Enumerated Values

|Parameter|Value|
|---|---|
|status|approve|
|status|Approve|
|status|decline|
|status|Decline|

> Example responses

> 200 Response

```json
{
  "name": "string",
  "request_status": "declined",
  "share_status": true,
  "share_hash": "string",
  "request_id": "string",
  "share_direct_image_url": "string",
  "expiration_date": "2019-06-18T20:09:43Z",
  "share": {
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  },
  "request": {
    "organization": "string",
    "phone": "string",
    "email": "string",
    "postal_code": "string",
    "access_type": "email",
    "created": {
      "date": "2019-06-18T20:09:43Z",
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    },
    "updated": {
      "date": "2019-06-18T20:09:43Z",
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    },
    "data": "string"
  }
}
```

<h3 id="update-an-existing-request-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[ShareRequest](#schemasharerequest)|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Data found|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Errors|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Code Expired or No User information found|None|

<aside class="success">
This operation does not require authentication
</aside>

## Validate share hash and request hash for given params

> Code samples

```shell
# You can also use wget
curl -X POST https://api.test/shares/{shareHash}/requests/{requestHash} \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Accept: application/json'

```

```http
POST https://api.test/shares/{shareHash}/requests/{requestHash} HTTP/1.1
Host: api.test
Content-Type: application/x-www-form-urlencoded
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.test/shares/{shareHash}/requests/{requestHash}',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "first_name": "string",
  "last_name": "string",
  "email": "string",
  "phone": "string"
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/json'

};

fetch('https://api.test/shares/{shareHash}/requests/{requestHash}',
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
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.test/shares/{shareHash}/requests/{requestHash}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Accept': 'application/json'
}

r = requests.post('https://api.test/shares/{shareHash}/requests/{requestHash}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/shares/{shareHash}/requests/{requestHash}");
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
        "Content-Type": []string{"application/x-www-form-urlencoded"},
        "Accept": []string{"application/json"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.test/shares/{shareHash}/requests/{requestHash}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /shares/{shareHash}/requests/{requestHash}`

Validate share hash and request hash for given params (currently used for direct access)

> Body parameter

```yaml
first_name: string
last_name: string
email: string
phone: string

```

<h3 id="validate-share-hash-and-request-hash-for-given-params-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|shareHash|path|string|true|Share Identifier (Not row id, use Hash)|
|requestHash|path|string|true|Request Identifier (Not row id, use Hash)|
|first_name|body|string|true|First name|
|last_name|body|string|true|Last name|
|email|body|string|false|Email address|
|phone|body|string|false|Phone number|

> Example responses

> 201 Response

```json
{
  "name": "string",
  "request_status": "declined",
  "share_status": true,
  "share_hash": "string",
  "request_id": "string",
  "share_direct_image_url": "string",
  "expiration_date": "2019-06-18T20:09:43Z",
  "share": {
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  },
  "request": {
    "organization": "string",
    "phone": "string",
    "email": "string",
    "postal_code": "string",
    "access_type": "email",
    "created": {
      "date": "2019-06-18T20:09:43Z",
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    },
    "updated": {
      "date": "2019-06-18T20:09:43Z",
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    },
    "data": "string"
  }
}
```

<h3 id="validate-share-hash-and-request-hash-for-given-params-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|[ShareRequest](#schemasharerequest)|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Data found|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Errors|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Code Expired or Not a Valid Combination|None|

<aside class="success">
This operation does not require authentication
</aside>

## Get all requests status

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/sharesRequests?active=true \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/sharesRequests?active=true HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/sharesRequests',
  method: 'get',
  data: '?active=true',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/sharesRequests?active=true',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/sharesRequests',
  params: {
  'active' => 'boolean'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/sharesRequests', params={
  'active': 'true'
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/sharesRequests?active=true");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/sharesRequests", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /sharesRequests`

Get all requests status

<h3 id="get-all-requests-status-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|active|query|boolean|true|Get only active share requests|

> Example responses

> 200 Response

```json
[
  {
    "name": "string",
    "request_status": "declined",
    "share_status": true,
    "share_hash": "string",
    "request_id": "string",
    "share_direct_image_url": "string",
    "expiration_date": "2019-06-18T20:09:43Z",
    "share": {
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    },
    "request": {
      "organization": "string",
      "phone": "string",
      "email": "string",
      "postal_code": "string",
      "access_type": "email",
      "created": {
        "date": "2019-06-18T20:09:43Z",
        "first_name": "string",
        "last_name": "string",
        "user_id": 0
      },
      "updated": {
        "date": "2019-06-18T20:09:43Z",
        "first_name": "string",
        "last_name": "string",
        "user_id": 0
      },
      "data": "string"
    }
  }
]
```

<h3 id="get-all-requests-status-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Data found|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Errors|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Code Expired or No User information found|None|

<h3 id="get-all-requests-status-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[ShareRequest](#schemasharerequest)]|false|none|none|
|» name|string|false|none|Share document name|
|» request_status|string|false|none|Request status|
|» share_status|boolean|false|none|Active/Inactive|
|» share_hash|string|false|none|Unique identifier for a share|
|» request_id|string|false|none|Unique identifier/hash for a request|
|» share_direct_image_url|string|false|none|Share QR code image url|
|» expiration_date|string(date-time)|false|none|Share expiration date and time|
|» share|[ShareCreatedObject](#schemasharecreatedobject)|false|none|Information on the individual who created the share|
|»» first_name|string|false|none|First name of individual who created the record|
|»» last_name|string|false|none|Last name of individual who created the record|
|»» user_id|integer|false|none|User ID for individual who created the record|
|» request|[ShareRequesterCreatedObject](#schemasharerequestercreatedobject)|false|none|Information on the individual who requested the access|
|»» organization|string|false|none|Organization name of the individual who requested the access|
|»» phone|string|false|none|Phone number of the individual who requested the access|
|»» email|string|false|none|Email address of the individual who requested the access|
|»» postal_code|string|false|none|Postal code of the individual who requested the access|
|»» access_type|string|false|none|Mechanism used to send the share|
|»» created|[CreatedObject](#schemacreatedobject)|false|none|Information on the individual who created the record|
|»»» date|string(date-time)|false|none|Date and time of record creation|
|»»» first_name|string|false|none|First name of individual who created the record|
|»»» last_name|string|false|none|Last name of individual who created the record|
|»»» user_id|integer|false|none|User ID for individual who created the record|
|»» updated|[UpdatedObject](#schemaupdatedobject)|false|none|Information on the individual who last updated the record|
|»»» date|string(date-time)|false|none|Date and time of the most recent record update|
|»»» first_name|string|false|none|First name of individual who last updated the record|
|»»» last_name|string|false|none|Last name of individual who last updated the record|
|»»» user_id|integer|false|none|User ID for individual who last updated the record|
|»» data|string|false|none|Data is an object, Object can be available only if request_status is approved|

#### Enumerated Values

|Property|Value|
|---|---|
|request_status|declined|
|request_status|pending|
|request_status|approved|
|access_type|email|
|access_type|mms|
|access_type|null|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get an existing request status or data

> Code samples

```shell
# You can also use wget
curl -X GET https://api.test/sharesRequests/{requestHash} \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://api.test/sharesRequests/{requestHash} HTTP/1.1
Host: api.test
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

$.ajax({
  url: 'https://api.test/sharesRequests/{requestHash}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'

};

fetch('https://api.test/sharesRequests/{requestHash}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://api.test/sharesRequests/{requestHash}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://api.test/sharesRequests/{requestHash}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.test/sharesRequests/{requestHash}");
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
        "Authorization": []string{"API_KEY"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.test/sharesRequests/{requestHash}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /sharesRequests/{requestHash}`

Get an existing request status or data. Same as GET /shares/{shareHash}/requests/{requestHash}

<h3 id="get-an-existing-request-status-or-data-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|requestHash|path|string|true|Request Identifier (Not row id, use Hash)|

> Example responses

> 200 Response

```json
{
  "name": "string",
  "request_status": "declined",
  "share_status": true,
  "share_hash": "string",
  "request_id": "string",
  "share_direct_image_url": "string",
  "expiration_date": "2019-06-18T20:09:43Z",
  "share": {
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  },
  "request": {
    "organization": "string",
    "phone": "string",
    "email": "string",
    "postal_code": "string",
    "access_type": "email",
    "created": {
      "date": "2019-06-18T20:09:43Z",
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    },
    "updated": {
      "date": "2019-06-18T20:09:43Z",
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    },
    "data": "string"
  }
}
```

<h3 id="get-an-existing-request-status-or-data-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[ShareRequest](#schemasharerequest)|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Data found|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Errors|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Code Expired or No User information found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

# Schemas

<h2 id="tocSappointment">Appointment</h2>

<a id="schemaappointment"></a>

```json
{
  "id": 0,
  "patient": {
    "id": 0,
    "first_name": "string",
    "last_name": "string"
  },
  "date": "2019-06-18",
  "time": "string",
  "specialty": {
    "id": 0,
    "name": "string"
  },
  "provider": {
    "first_name": "string",
    "last_name": "string",
    "id": 0
  },
  "status": "pending",
  "created": {
    "date": "2019-06-18T20:09:43Z",
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  },
  "updated": {
    "date": "2019-06-18T20:09:43Z",
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|The InXite identifier for the appointment|
|patient|object|false|none|Basic patient information|
|» id|integer|false|none|The InXite identifier for the patient|
|» first_name|string|false|none|Patient first name|
|» last_name|string|false|none|Patient last name|
|date|string(date)|false|none|Date of appointment|
|time|string|false|none|Time of appointment|
|specialty|object|false|none|none|
|» id|integer|false|none|InXite specialty ID|
|» name|string|false|none|Name of specialty|
|provider|object|false|none|none|
|» first_name|string|false|none|First name of provider|
|» last_name|string|false|none|Last name of provider|
|» id|integer|false|none|Provider ID|
|status|string|false|none|Appointment status|
|created|[CreatedObject](#schemacreatedobject)|false|none|Information on the individual who created the record|
|updated|[UpdatedObject](#schemaupdatedobject)|false|none|Information on the individual who last updated the record|

#### Enumerated Values

|Property|Value|
|---|---|
|status|pending|
|status|scheduled|
|status|cancelled|
|status|rescheduled|
|status|complete|

<h2 id="tocScreatedobject">CreatedObject</h2>

<a id="schemacreatedobject"></a>

```json
{
  "date": "2019-06-18T20:09:43Z",
  "first_name": "string",
  "last_name": "string",
  "user_id": 0
}

```

*Information on the individual who created the record*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|date|string(date-time)|false|none|Date and time of record creation|
|first_name|string|false|none|First name of individual who created the record|
|last_name|string|false|none|Last name of individual who created the record|
|user_id|integer|false|none|User ID for individual who created the record|

<h2 id="tocSemployerobject">EmployerObject</h2>

<a id="schemaemployerobject"></a>

```json
{
  "name": "string",
  "street": "string",
  "city": "string",
  "state": "string",
  "postal_code": "string",
  "occupation": "string",
  "industry": "string"
}

```

*Patient Employer information*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|false|none|Employer name|
|street|string|false|none|Employer street address|
|city|string|false|none|Employer city|
|state|string|false|none|Employer state|
|postal_code|string|false|none|Employer postal code|
|occupation|string|false|none|Employee occupation|
|industry|string|false|none|Employer industry|

<h2 id="tocSpatientemergencyobject">PatientEmergencyObject</h2>

<a id="schemapatientemergencyobject"></a>

```json
{
  "name": "string",
  "phone": "string",
  "relation": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|false|none|Emergency contact name|
|phone|string|false|none|Emergency contact phone number|
|relation|string|false|none|Emergency contact relationship|

<h2 id="tocSpatientcaregiverobject">PatientCaregiverObject</h2>

<a id="schemapatientcaregiverobject"></a>

```json
{
  "name": "string",
  "phone": "string",
  "relation": "string",
  "power_of_attorney": true
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|false|none|Caregiver contact name|
|phone|string|false|none|Caregiver contact phone number|
|relation|string|false|none|Caregiver contact relationship|
|power_of_attorney|boolean|false|none|Caregiver contact is POA (Power of Attorney)?|

<h2 id="tocSdiagnosis">Diagnosis</h2>

<a id="schemadiagnosis"></a>

```json
{
  "id": 0,
  "title": "string",
  "diagnosis": "string",
  "chronic": true,
  "active": true
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|The InXite identifier for the Diagnosis|
|title|string|false|none|The Title Diagnosis|
|diagnosis|string|false|none|The ICD code|
|chronic|boolean|false|none|Chronic status|
|active|boolean|false|none|Active status|

<h2 id="tocShealthscore">HealthScore</h2>

<a id="schemahealthscore"></a>

```json
{
  "id": 0,
  "patient_id": 0,
  "score": 0,
  "metrics": [
    {
      "id": 0,
      "category": "string",
      "level": "string",
      "metric_id": 0,
      "metric_level": "string",
      "name": "string",
      "score": 0,
      "source": {
        "id": 0,
        "module": "string"
      },
      "unit": "string",
      "value": {
        "current": "string",
        "text": "string"
      },
      "created": {
        "date": "2019-06-18T20:09:43Z",
        "first_name": "string",
        "last_name": "string",
        "user_id": 0
      },
      "updated": {
        "date": "2019-06-18T20:09:43Z",
        "first_name": "string",
        "last_name": "string",
        "user_id": 0
      }
    }
  ],
  "created": {
    "date": "2019-06-18T20:09:43Z",
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|patient_id|integer|false|none|none|
|score|integer|false|none|none|
|metrics|[[HealthMetricValue](#schemahealthmetricvalue)]|false|none|none|
|created|[CreatedObject](#schemacreatedobject)|false|none|Information on the individual who created the record|

<h2 id="tocShealthmetricvalue">HealthMetricValue</h2>

<a id="schemahealthmetricvalue"></a>

```json
{
  "id": 0,
  "category": "string",
  "level": "string",
  "metric_id": 0,
  "metric_level": "string",
  "name": "string",
  "score": 0,
  "source": {
    "id": 0,
    "module": "string"
  },
  "unit": "string",
  "value": {
    "current": "string",
    "text": "string"
  },
  "created": {
    "date": "2019-06-18T20:09:43Z",
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  },
  "updated": {
    "date": "2019-06-18T20:09:43Z",
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|category|string|false|none|none|
|level|string|false|none|none|
|metric_id|integer|false|none|none|
|metric_level|string|false|none|none|
|name|string|false|none|none|
|score|integer|false|none|none|
|source|object|false|none|none|
|» id|integer|false|none|none|
|» module|string|false|none|none|
|unit|string|false|none|none|
|value|object|false|none|none|
|» current|string|false|none|none|
|» text|string|false|none|none|
|created|[CreatedObject](#schemacreatedobject)|false|none|Information on the individual who created the record|
|updated|[UpdatedObject](#schemaupdatedobject)|false|none|Information on the individual who last updated the record|

<h2 id="tocSinsurance">Insurance</h2>

<a id="schemainsurance"></a>

```json
{
  "id": 0,
  "type": "primary",
  "name": "string",
  "insurance_company_id": 0,
  "plan": "string",
  "policy_number": "string",
  "group_number": "string",
  "subscriber_first_name": "string",
  "subscriber_last_name": "string",
  "subscriber_middle_name": "string",
  "subscriber_relationship": "string",
  "start_date": "2019-06-18",
  "end_date": "string",
  "active": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|type|string|false|none|none|
|name|string|false|none|none|
|insurance_company_id|integer|false|none|none|
|plan|string|false|none|none|
|policy_number|string|false|none|none|
|group_number|string|false|none|none|
|subscriber_first_name|string|false|none|none|
|subscriber_last_name|string|false|none|none|
|subscriber_middle_name|string|false|none|none|
|subscriber_relationship|string|false|none|none|
|start_date|string(date)|false|none|none|
|end_date|string|false|none|none|
|active|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|primary|
|type|secondary|
|type|tertiary|
|type|pharmacy|

<h2 id="tocSjwt">JWT</h2>

<a id="schemajwt"></a>

```json
{
  "access_token": "string",
  "token_type": "string",
  "expires_in": 0,
  "refresh_token": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|access_token|string|false|none|The Access Token string|
|token_type|string|false|none|The type of token issued, typically will just be the string “bearer”|
|expires_in|integer|false|none|The duration of time for which the Access Token is granted (in seconds)|
|refresh_token|string|false|none|The Refresh Token is used by clients to obtain an Access Token when the Access Token has expired. The Refresh Token is valid for twice the duration of the Access Token|

<h2 id="tocSjwt_errors">JWT_errors</h2>

<a id="schemajwt_errors"></a>

```json
{
  "error": "string",
  "error_description": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|error|string|false|none|The error code designated for the specific error|
|error_description|string|false|none|Human-readable text providing additional information, used to assist in understanding the error that occurred|

<h2 id="tocSmedication">Medication</h2>

<a id="schemamedication"></a>

```json
{
  "id": 0,
  "name": "string",
  "rxnorm_cui": "string",
  "ndc": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|Medication ID|
|name|string|false|none|Medication name|
|rxnorm_cui|string|false|none|RxNorm Concept ID|
|ndc|string|false|none|National Drug Code|

<h2 id="tocSmedicationforms">MedicationForms</h2>

<a id="schemamedicationforms"></a>

```json
"Capsule"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Capsule|
|*anonymous*|Cream|
|*anonymous*|Drops|
|*anonymous*|Emulsion|
|*anonymous*|Inhalations|
|*anonymous*|Injection|
|*anonymous*|Lozenge|
|*anonymous*|mL|
|*anonymous*|Ointment|
|*anonymous*|Patch|
|*anonymous*|Pill|
|*anonymous*|Solution|
|*anonymous*|Suspension|
|*anonymous*|Tablet|
|*anonymous*|tsp|
|*anonymous*|Units|

<h2 id="tocSmedicationfrequencies">MedicationFrequencies</h2>

<a id="schemamedicationfrequencies"></a>

```json
"a.c. (Before meals)"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|a.c. (Before meals)|
|*anonymous*|a.m. (Morning, before noon)|
|*anonymous*|A.T.C. (Around the clock)|
|*anonymous*|ad lib. (As much as desired)|
|*anonymous*|alt. h. (Every other hour)|
|*anonymous*|b.i.d. (Twice per day)|
|*anonymous*|cf (With Food)|
|*anonymous*|e.m.p. (As directed)|
|*anonymous*|h.s. (At bedtime)|
|*anonymous*|noct. (At night)|
|*anonymous*|p.c. (After meals)|
|*anonymous*|p.m. (Evening or afternoon)|
|*anonymous*|prn (As needed)|
|*anonymous*|q.3h (Every 3 hours)|
|*anonymous*|q.4-6h (Every 4 - 6 hours)|
|*anonymous*|q.4h (Every 4 hours)|
|*anonymous*|q.5h (Every 5 hours)|
|*anonymous*|q.6h (Every 6 hours)|
|*anonymous*|q.8h (Every 8 hours)|
|*anonymous*|q.a.d (Every other day)|
|*anonymous*|q.d. (Once per day)|
|*anonymous*|q.h.s. (Every night at bedtime)|
|*anonymous*|q.i.d. (Four times per day)|
|*anonymous*|q.weekly (Weekly)|
|*anonymous*|stat (Immediately)|
|*anonymous*|t.i.d. (Three times per day)|

<h2 id="tocSmedicationroutes">MedicationRoutes</h2>

<a id="schemamedicationroutes"></a>

```json
"AAA (Apply to affected area)"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|AAA (Apply to affected area)|
|*anonymous*|AD (Right Ear)|
|*anonymous*|AS (Left Ear)|
|*anonymous*|AU (Both Ears)|
|*anonymous*|HHN (Hand held nebulizer)|
|*anonymous*|ID (Intradermal route)|
|*anonymous*|IM (Intramuscular route)|
|*anonymous*|IT (Intrathecal route)|
|*anonymous*|IV (Intravenous route)|
|*anonymous*|IVP (IV push)|
|*anonymous*|IVPB (Intravenous piggyback)|
|*anonymous*|NAS (Nasal)|
|*anonymous*|NGT (Nasogastric tube)|
|*anonymous*|NPO (Nothing by mouth)|
|*anonymous*|OD (Right eye)|
|*anonymous*|OS (Left eye)|
|*anonymous*|OU (Both eyes)|
|*anonymous*|PEG (Percutaneous gastrostomy tube)|
|*anonymous*|PO (By mouth)|
|*anonymous*|PR (By rectum)|
|*anonymous*|PV (Vaginal route)|
|*anonymous*|S & S (Swish and swallow)|
|*anonymous*|SL (Sublignual route)|
|*anonymous*|SQ (Subcutaneous route)|
|*anonymous*|TD (Transdermal)|
|*anonymous*|top (Topical)|

<h2 id="tocSmedicationunits">MedicationUnits</h2>

<a id="schemamedicationunits"></a>

```json
"grams"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|grams|
|*anonymous*|gtt|
|*anonymous*|IU|
|*anonymous*|kg|
|*anonymous*|L|
|*anonymous*|mcg|
|*anonymous*|mEq|
|*anonymous*|mg|
|*anonymous*|mg/1mL|
|*anonymous*|mg/2mL|
|*anonymous*|mg/3mL|
|*anonymous*|mg/4mL|
|*anonymous*|mg/5mL|
|*anonymous*|mL|
|*anonymous*|oz|
|*anonymous*|pt|
|*anonymous*|qt|
|*anonymous*|tbs|
|*anonymous*|tsp|

<h2 id="tocStitle">Title</h2>

<a id="schematitle"></a>

```json
"Mr."

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Mr.|
|*anonymous*|Mrs.|
|*anonymous*|Ms.|
|*anonymous*|Dr.|

<h2 id="tocSgender">Gender</h2>

<a id="schemagender"></a>

```json
"Male"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Male|
|*anonymous*|Female|

<h2 id="tocSsuffix">Suffix</h2>

<a id="schemasuffix"></a>

```json
"Jr."

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Jr.|
|*anonymous*|Sr.|
|*anonymous*|II|
|*anonymous*|III|
|*anonymous*|Esq.|

<h2 id="tocSindustry">Industry</h2>

<a id="schemaindustry"></a>

```json
"Accommodations"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Accommodations|
|*anonymous*|Accounting|
|*anonymous*|Advertising|
|*anonymous*|Aerospace|
|*anonymous*|Agriculture & Agribusiness|
|*anonymous*|Air Transportation|
|*anonymous*|Apparel & Accessories|
|*anonymous*|Auto|
|*anonymous*|Banking|
|*anonymous*|Beauty & Cosmetics|
|*anonymous*|Biotechnology|
|*anonymous*|Chemical|
|*anonymous*|Communications|
|*anonymous*|Computer|
|*anonymous*|Construction|
|*anonymous*|Consulting|
|*anonymous*|Consumer Products|
|*anonymous*|Education|
|*anonymous*|Electronics|
|*anonymous*|Employment|
|*anonymous*|Energy|
|*anonymous*|Entertainment & Recreation|
|*anonymous*|Fashion|
|*anonymous*|Financial Services|
|*anonymous*|Food & Beverage|
|*anonymous*|Health|
|*anonymous*|Healthcare|
|*anonymous*|Information Technology|
|*anonymous*|Insurance|
|*anonymous*|Journalism & News|
|*anonymous*|Legal Services|
|*anonymous*|Manufacturing|
|*anonymous*|Media & Broadcasting|
|*anonymous*|Medical Devices & Supplies|
|*anonymous*|Motion Pictures & Video|
|*anonymous*|Music|
|*anonymous*|Pharmaceutical|
|*anonymous*|Public Administration|
|*anonymous*|Public Relations|
|*anonymous*|Publishing|
|*anonymous*|Real Estate|
|*anonymous*|Retail|
|*anonymous*|Service|
|*anonymous*|Sports|
|*anonymous*|Technology|
|*anonymous*|Telecommunications|
|*anonymous*|Tourism|
|*anonymous*|Transportation|
|*anonymous*|Travel|
|*anonymous*|Utilities|
|*anonymous*|Video Game|
|*anonymous*|Web Services|

<h2 id="tocSrelationships">Relationships</h2>

<a id="schemarelationships"></a>

```json
"Child"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Child|
|*anonymous*|Father|
|*anonymous*|Grandparent|
|*anonymous*|Mother|
|*anonymous*|Other|
|*anonymous*|Sibling|
|*anonymous*|Spouse|

<h2 id="tocSmaritalstatus">MaritalStatus</h2>

<a id="schemamaritalstatus"></a>

```json
"Married"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Married|
|*anonymous*|Single|
|*anonymous*|Divorced|
|*anonymous*|Widowed|
|*anonymous*|Separated|
|*anonymous*|Domestic Partner|

<h2 id="tocSrace">Race</h2>

<a id="schemarace"></a>

```json
"American Indian/Alaska Native"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|American Indian/Alaska Native|
|*anonymous*|Asian|
|*anonymous*|Black/African American|
|*anonymous*|Caucasian/White|
|*anonymous*|Multi-Racial|
|*anonymous*|Native Hawaiian/Other Pacific Islander|
|*anonymous*|Other|
|*anonymous*|Unknown|
|*anonymous*|Declined To Specify|

<h2 id="tocSethnicity">Ethnicity</h2>

<a id="schemaethnicity"></a>

```json
"Hispanic or Latino"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Hispanic or Latino|
|*anonymous*|Not Hispanic or Latino|
|*anonymous*|Unknown|
|*anonymous*|Declined To Specify|

<h2 id="tocSpatient">Patient</h2>

<a id="schemapatient"></a>

```json
{
  "patient_id": 0,
  "user_id": 0,
  "uuid": "string",
  "organizations": [
    {
      "id": 0,
      "name": "string",
      "code": "string"
    }
  ],
  "title": "Mr.",
  "first_name": "string",
  "middle_name": "string",
  "last_name": "string",
  "suffix": "Jr.",
  "preferred_name": "string",
  "date_of_birth": "2019-06-18",
  "gender": "Male",
  "source_organization_id": 0,
  "ssn": "string",
  "marital_status": "Married",
  "blood_type": "A Negative",
  "organ_donor": false,
  "street": "string",
  "city": "string",
  "state": "string",
  "postal_code": "string",
  "country_code": "USA",
  "phone_home": "string",
  "phone_home_disconnected": false,
  "phone_cell": "string",
  "phone_cell_disconnected": false,
  "email": "user@example.com",
  "employer": {
    "name": "string",
    "street": "string",
    "city": "string",
    "state": "string",
    "postal_code": "string",
    "occupation": "string",
    "industry": "string"
  },
  "language_id": "string",
  "interpreter": false,
  "ethnicity": "Hispanic or Latino",
  "race": "American Indian/Alaska Native",
  "emergency": [
    {
      "name": "string",
      "phone": "string",
      "relation": "string"
    }
  ],
  "caregiver": [
    {
      "name": "string",
      "phone": "string",
      "relation": "string",
      "power_of_attorney": true
    }
  ],
  "deceased": false,
  "deceased_reason": "string",
  "deceased_date": "2019-06-18",
  "created": {
    "date": "2019-06-18T20:09:43Z",
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|patient_id|integer|false|none|none|
|user_id|integer|false|none|none|
|uuid|string|false|none|none|
|organizations|[[PatientOrganizations](#schemapatientorganizations)]|false|none|none|
|title|string|false|none|none|
|first_name|string|false|none|none|
|middle_name|string|false|none|none|
|last_name|string|false|none|none|
|suffix|string|false|none|none|
|preferred_name|string|false|none|none|
|date_of_birth|string(date)|false|none|none|
|gender|string|false|none|none|
|source_organization_id|integer|false|none|none|
|ssn|string|false|none|none|
|marital_status|string|false|none|none|
|blood_type|string|false|none|none|
|organ_donor|boolean|false|none|none|
|street|string|false|none|none|
|city|string|false|none|none|
|state|string|false|none|none|
|postal_code|string|false|none|none|
|country_code|string|false|none|none|
|phone_home|string|false|none|none|
|phone_home_disconnected|boolean|false|none|none|
|phone_cell|string|false|none|none|
|phone_cell_disconnected|boolean|false|none|none|
|email|string(email)|false|none|none|
|employer|[EmployerObject](#schemaemployerobject)|false|none|Patient Employer information|
|language_id|string|false|none|none|
|interpreter|boolean|false|none|none|
|ethnicity|string|false|none|none|
|race|string|false|none|none|
|emergency|[[PatientEmergencyObject](#schemapatientemergencyobject)]|false|none|none|
|caregiver|[[PatientCaregiverObject](#schemapatientcaregiverobject)]|false|none|none|
|deceased|boolean|false|none|none|
|deceased_reason|string|false|none|none|
|deceased_date|string(date)|false|none|none|
|created|[CreatedObject](#schemacreatedobject)|false|none|Information on the individual who created the record|

#### Enumerated Values

|Property|Value|
|---|---|
|title|Mr.|
|title|Mrs.|
|title|Ms.|
|title|Dr.|
|suffix|Jr.|
|suffix|Sr.|
|suffix|II|
|suffix|III|
|suffix|Esq.|
|gender|Male|
|gender|Female|
|marital_status|Married|
|marital_status|Single|
|marital_status|Divorced|
|marital_status|Widowed|
|marital_status|Separated|
|marital_status|Domestic Partner|
|blood_type|A Negative|
|blood_type|A Positive|
|blood_type|AB Negative|
|blood_type|AB Positive|
|blood_type|B Negative|
|blood_type|B Positive|
|blood_type|O Negative|
|blood_type|O Positive|
|ethnicity|Hispanic or Latino|
|ethnicity|Not Hispanic or Latino|
|ethnicity|Unknown|
|ethnicity|Declined To Specify|
|race|American Indian/Alaska Native|
|race|Asian|
|race|Black/African American|
|race|Caucasian/White|
|race|Multi-Racial|
|race|Native Hawaiian/Other Pacific Islander|
|race|Other|
|race|Unknown|
|race|Declined To Specify|

<h2 id="tocSpatientmedication">PatientMedication</h2>

<a id="schemapatientmedication"></a>

```json
{
  "id": "string",
  "rxImage": "string",
  "title": "string",
  "desc": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|INXITE medication ID|
|rxImage|string|false|none|URL to medication image|
|title|string|false|none|Medication Name|
|desc|string|false|none|Default Medication Description|

<h2 id="tocSpatientmedicationdetails">PatientMedicationDetails</h2>

<a id="schemapatientmedicationdetails"></a>

```json
{
  "drugInfo": {
    "brandName": "string",
    "description": "string",
    "genericName": "string"
  },
  "drugs": [
    {
      "pharmacy": {
        "name": "string",
        "streetAddress": "string",
        "city": "string",
        "state": "string",
        "postal_code": "string",
        "latitude": 0,
        "longitude": 0,
        "hoursOfOperation": "string",
        "phone": "string",
        "npi": "string",
        "distance": "string",
        "listingSlug": "string",
        "pharmacyLogo": {
          "imgUrl": "string",
          "imgStyle": "string",
          "brand": "string",
          "url": "string"
        }
      },
      "drug": {
        "ndcCode": 0,
        "brandGenericIndicator": "string",
        "gsn": "string",
        "drugRanking": "string",
        "quantity": "string",
        "quantityRanking": "string",
        "labelName": "string"
      },
      "pricing": {
        "price": "string",
        "discount": 0,
        "group": "string",
        "bin": "string",
        "pcn": "string",
        "couponCode": "string"
      }
    }
  ],
  "forms": {
    "form": "string",
    "gsn": 0,
    "isSelected": true,
    "ranking": "string"
  },
  "names": [
    {
      "drugName": "string",
      "brandGenericIndicator": "string",
      "isSelected": true
    }
  ],
  "quantities": [
    {
      "quantity": 0,
      "quantityUom": "string",
      "gsn": 0,
      "isSelected": true,
      "ranking": 0
    }
  ],
  "strengths": [
    {
      "strength": 0,
      "gsn": 0,
      "isSelected": true,
      "ranking": 0
    }
  ],
  "meta": {
    "brandName": "string",
    "gsn": 0,
    "genericName": "string",
    "ndc": "string",
    "drugDescription": 0,
    "image": [
      "string"
    ],
    "lowPrice": "string",
    "highPrice": "string"
  },
  "drugInfoDetails": {
    "brandName": "string",
    "genericName": "string",
    "drugDescription": "string",
    "administerInstructions": "string",
    "contraindications": "string",
    "disclaimer": "string",
    "interactions": "string",
    "missedDoseInfo": "string",
    "monitorReactions": "string",
    "sideEffects": "string",
    "storageInfo": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|drugInfo|object|false|none|none|
|» brandName|string|false|none|Brand name of the medication|
|» description|string|false|none|What the medication does|
|» genericName|string|false|none|Generic name of the medication|
|drugs|[object]|false|none|none|
|» pharmacy|object|false|none|none|
|»» name|string|false|none|Name of the pharmacy|
|»» streetAddress|string|false|none|Street address of the pharmacy|
|»» city|string|false|none|Name of the pharmacy|
|»» state|string|false|none|Street address of the pharmacy|
|»» postal_code|string|false|none|Name of the pharmacy|
|»» latitude|integer|false|none|Street address of the pharmacy|
|»» longitude|integer|false|none|Name of the pharmacy|
|»» hoursOfOperation|string|false|none|Street address of the pharmacy|
|»» phone|string|false|none|Name of the pharmacy|
|»» npi|string|false|none|Street address of the pharmacy|
|»» distance|string|false|none|Name of the pharmacy|
|»» listingSlug|string|false|none|Street address of the pharmacy|
|»» pharmacyLogo|object|false|none|none|
|»»» imgUrl|string|false|none|Pharmacy Logo|
|»»» imgStyle|string|false|none|Pharmacy Logo recommended styling|
|»»» brand|string|false|none|Pharmacy Logo Name|
|»»» url|string|false|none|Pharmacy Url location|
|»» drug|object|false|none|none|
|»»» ndcCode|integer|false|none|Drug's NDC code|
|»»» brandGenericIndicator|string|false|none|Medication Type|
|»»» gsn|string|false|none|current filter state of medication|
|»»» drugRanking|string|false|none|position of drug options|
|»»» quantity|string|false|none|Medication quantity options|
|»»» quantityRanking|string|false|none|Current quantity option|
|»»» labelName|string|false|none|Filtered medication label|
|»» pricing|object|false|none|none|
|»»» price|string|false|none|Price from discount|
|»»» discount|integer|false|none|amount discounted from price|
|»»» group|string|false|none|medication routing information|
|»»» bin|string|false|none|medication routing information|
|»»» pcn|string|false|none|3rd party company code|
|»»» couponCode|string|false|none|pharmacy discount coupon code|
|»» forms|object|false|none|none|
|»»» form|string|false|none|type of medication|
|»»» gsn|integer|false|none|filter option|
|»»» isSelected|boolean|false|none|none|
|»»» ranking|string|false|none|filter option position|
|»» names|[object]|false|none|none|
|»»» drugName|string|false|none|medication name option|
|»»» brandGenericIndicator|string|false|none|brand category|
|»»» isSelected|boolean|false|none|none|
|»» quantities|[object]|false|none|none|
|»»» quantity|integer|false|none|amount option|
|»»» quantityUom|string|false|none|quantity form type|
|»»» gsn|integer|false|none|filter option value|
|»»» isSelected|boolean|false|none|none|
|»»» ranking|integer|false|none|filter option position|
|»» strengths|[object]|false|none|none|
|»»» strength|integer|false|none|amount option|
|»»» gsn|integer|false|none|filter option value|
|»»» isSelected|boolean|false|none|none|
|»»» ranking|integer|false|none|filter option position|
|»» meta|object|false|none|none|
|»»» brandName|string|false|none|brand name of the medication|
|»»» gsn|integer|false|none|filter option|
|»»» genericName|string|false|none|generic name of the medication|
|»»» ndc|string|false|none|mational drug code directory value|
|»»» drugDescription|integer|false|none|medication intention|
|»»» image|[string]|false|none|none|
|»»» lowPrice|string|false|none|lowest pricing option found|
|»»» highPrice|string|false|none|highest pricing option found|
|»» drugInfoDetails|object|false|none|none|
|»»» brandName|string|false|none|brand name of the medication|
|»»» genericName|string|false|none|generic name of the medication|
|»»» drugDescription|string|false|none|medication intention|
|»»» administerInstructions|string|false|none|drug usage instructions|
|»»» contraindications|string|false|none|drug precautions|
|»»» disclaimer|string|false|none|disclaimer summary|
|»»» interactions|string|false|none|drug interactions|
|»»» missedDoseInfo|string|false|none|missed dose assistance|
|»»» monitorReactions|string|false|none|monitor reactions of medications|
|»»» sideEffects|string|false|none|possible side effects from taking medication|
|»»» storageInfo|string|false|none|medicine storage information|

<h2 id="tocSpatientproducts">PatientProducts</h2>

<a id="schemapatientproducts"></a>

```json
{
  "condition": [
    {
      "id": 0,
      "partner_id": 0,
      "title": "string",
      "slug": "string",
      "offsite_product": 0,
      "product_url": "string",
      "category_id": 0,
      "description": "string",
      "featured_image": "string",
      "price": "string",
      "compare_at_price": "string",
      "enabled": 0,
      "created_at": "string",
      "updated_at": "string",
      "deleted_at": "string",
      "images": [
        {
          "id": 0,
          "partner_product_id": 0,
          "url": "string",
          "created_at": "string",
          "updated_at": "string"
        }
      ]
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|condition|[object]|false|none|none|
|» id|integer|false|none|product id|
|» partner_id|integer|false|none|id of the 3rd party partner|
|» title|string|false|none|product title|
|» slug|string|false|none|keyword slug|
|» offsite_product|integer|false|none|internal or external product|
|» product_url|string|false|none|url to product page|
|» category_id|integer|false|none|product category id|
|» description|string|false|none|product description|
|» featured_image|string|false|none|main image of product|
|» price|string|false|none|current product price|
|» compare_at_price|string|false|none|original product page|
|» enabled|integer|false|none|product active or inactive|
|» created_at|string|false|none|product creation date|
|» updated_at|string|false|none|product last updated date|
|» deleted_at|string|false|none|product deletion date|
|» images|[object]|false|none|none|
|»» id|integer|false|none|product image id|
|»» partner_product_id|integer|false|none|partners product id|
|»» url|string|false|none|url to product image|
|»» created_at|string|false|none|product image creation date|
|»» updated_at|string|false|none|product image last updated date|

<h2 id="tocSpatientproductcategories">PatientProductCategories</h2>

<a id="schemapatientproductcategories"></a>

```json
{
  "id": "string",
  "name": "string",
  "slug": "string",
  "created_at": "string",
  "updated_at": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|category id|
|name|string|false|none|category label|
|slug|string|false|none|category keywords|
|created_at|string|false|none|creation date of this category|
|updated_at|string|false|none|last date the category was updated|

<h2 id="tocSpatientorganizations">PatientOrganizations</h2>

<a id="schemapatientorganizations"></a>

```json
{
  "id": 0,
  "name": "string",
  "code": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|Organization ID|
|name|string|false|none|Organization Name|
|code|string|false|none|Organization Code|

<h2 id="tocSsoarassessment">SoarAssessment</h2>

<a id="schemasoarassessment"></a>

```json
{
  "patient_id": 0,
  "date_time": "2019-06-18T20:09:43Z"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|patient_id|integer|false|none|Patient ID|
|date_time|string(date-time)|false|none|The date and time that the assessment was completed|

<h2 id="tocSsoarassessmentcategoryscore">SoarAssessmentCategoryScore</h2>

<a id="schemasoarassessmentcategoryscore"></a>

```json
{
  "risk": "L",
  "score": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|risk|string|false|none|none|
|score|integer|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|risk|L|
|risk|M|
|risk|H|

<h2 id="tocSspecialty">Specialty</h2>

<a id="schemaspecialty"></a>

```json
{
  "id": 0,
  "name": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|Specialty ID|
|name|string|false|none|Name of specialty|

<h2 id="tocSupdatedobject">UpdatedObject</h2>

<a id="schemaupdatedobject"></a>

```json
{
  "date": "2019-06-18T20:09:43Z",
  "first_name": "string",
  "last_name": "string",
  "user_id": 0
}

```

*Information on the individual who last updated the record*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|date|string(date-time)|false|none|Date and time of the most recent record update|
|first_name|string|false|none|First name of individual who last updated the record|
|last_name|string|false|none|Last name of individual who last updated the record|
|user_id|integer|false|none|User ID for individual who last updated the record|

<h2 id="tocSnotification">Notification</h2>

<a id="schemanotification"></a>

```json
{
  "id": 0,
  "patient_id": 0,
  "type": "string",
  "action": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|Identifier|
|patient_id|integer|false|none|Patient Id|
|type|string|false|none|The type of notification (allergy, medication, etc.)|
|action|string|false|none|The action completed (added, updated, etc.)|

<h2 id="tocSorganization">Organization</h2>

<a id="schemaorganization"></a>

```json
{
  "id": 0,
  "name": "string",
  "code": "string",
  "street": "string",
  "city": "string",
  "state": "string",
  "county": "string",
  "postal_code": "string",
  "country_code": "string",
  "phone": "string",
  "fax": "string",
  "email": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|Organization Id|
|name|string|false|none|Organization name|
|code|string|false|none|Organization code|
|street|string|false|none|Organization street|
|city|string|false|none|Organization city|
|state|string|false|none|Organization state like OH, NY|
|county|string|false|none|Organization county|
|postal_code|string|false|none|Organization 5 digit postal code|
|country_code|string|false|none|Organization country code USA|
|phone|string|false|none|Organization contact number|
|fax|string|false|none|Organization fax number|
|email|string|false|none|Organization email|

<h2 id="tocSshare">Share</h2>

<a id="schemashare"></a>

```json
{
  "id": 0,
  "patient_id": 0,
  "name": "string",
  "hash": "string",
  "created": {
    "date": "2019-06-18T20:09:43Z",
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  },
  "anonymous": true,
  "active": true,
  "expiration_date": "2019-06-18T20:09:43Z",
  "share_url": "string",
  "image_url": "string",
  "image": "string",
  "options": {
    "data": [
      "allergies"
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|Identifier|
|patient_id|integer|false|none|Patient Id|
|name|string|false|none|Share document name|
|hash|string|false|none|Unique Identifier for a share|
|created|[CreatedObject](#schemacreatedobject)|false|none|Information on the individual who created the record|
|anonymous|boolean|false|none|Anonymous access|
|active|boolean|false|none|Active|
|expiration_date|string(date-time)|false|none|Share expiration date and time|
|share_url|string|false|none|Direct share url|
|image_url|string|false|none|Share QR code image url|
|image|string|false|none|Share QR code image|
|options|object|false|none|Data object|
|» data|[string]|false|none|Data elements|

<h2 id="tocSsharerequest">ShareRequest</h2>

<a id="schemasharerequest"></a>

```json
{
  "name": "string",
  "request_status": "declined",
  "share_status": true,
  "share_hash": "string",
  "request_id": "string",
  "share_direct_image_url": "string",
  "expiration_date": "2019-06-18T20:09:43Z",
  "share": {
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  },
  "request": {
    "organization": "string",
    "phone": "string",
    "email": "string",
    "postal_code": "string",
    "access_type": "email",
    "created": {
      "date": "2019-06-18T20:09:43Z",
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    },
    "updated": {
      "date": "2019-06-18T20:09:43Z",
      "first_name": "string",
      "last_name": "string",
      "user_id": 0
    },
    "data": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|false|none|Share document name|
|request_status|string|false|none|Request status|
|share_status|boolean|false|none|Active/Inactive|
|share_hash|string|false|none|Unique identifier for a share|
|request_id|string|false|none|Unique identifier/hash for a request|
|share_direct_image_url|string|false|none|Share QR code image url|
|expiration_date|string(date-time)|false|none|Share expiration date and time|
|share|[ShareCreatedObject](#schemasharecreatedobject)|false|none|Information on the individual who created the share|
|request|[ShareRequesterCreatedObject](#schemasharerequestercreatedobject)|false|none|Information on the individual who requested the access|

#### Enumerated Values

|Property|Value|
|---|---|
|request_status|declined|
|request_status|pending|
|request_status|approved|

<h2 id="tocSsharecreatedobject">ShareCreatedObject</h2>

<a id="schemasharecreatedobject"></a>

```json
{
  "first_name": "string",
  "last_name": "string",
  "user_id": 0
}

```

*Information on the individual who created the share*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|first_name|string|false|none|First name of individual who created the record|
|last_name|string|false|none|Last name of individual who created the record|
|user_id|integer|false|none|User ID for individual who created the record|

<h2 id="tocSsharerequestercreatedobject">ShareRequesterCreatedObject</h2>

<a id="schemasharerequestercreatedobject"></a>

```json
{
  "organization": "string",
  "phone": "string",
  "email": "string",
  "postal_code": "string",
  "access_type": "email",
  "created": {
    "date": "2019-06-18T20:09:43Z",
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  },
  "updated": {
    "date": "2019-06-18T20:09:43Z",
    "first_name": "string",
    "last_name": "string",
    "user_id": 0
  },
  "data": "string"
}

```

*Information on the individual who requested the access*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|organization|string|false|none|Organization name of the individual who requested the access|
|phone|string|false|none|Phone number of the individual who requested the access|
|email|string|false|none|Email address of the individual who requested the access|
|postal_code|string|false|none|Postal code of the individual who requested the access|
|access_type|string|false|none|Mechanism used to send the share|
|created|[CreatedObject](#schemacreatedobject)|false|none|Information on the individual who created the record|
|updated|[UpdatedObject](#schemaupdatedobject)|false|none|Information on the individual who last updated the record|
|data|string|false|none|Data is an object, Object can be available only if request_status is approved|

#### Enumerated Values

|Property|Value|
|---|---|
|access_type|email|
|access_type|mms|
|access_type|null|

<h2 id="tocSlanguageobject">LanguageObject</h2>

<a id="schemalanguageobject"></a>

```json
{
  "name": "string",
  "id": "string"
}

```

*Information on language*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|false|none|Name of the language|
|id|string|false|none|Lanuage ID|

<script type="application/ld+json">
{
  "@context": "http://schema.org/",
  "@type": "WebAPI",
  "description": "This documentation is for the INXITE Platform API.",



  "name": "INXITE API"
}
</script>
