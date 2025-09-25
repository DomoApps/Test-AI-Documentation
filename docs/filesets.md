# Product API Template

> **Note:** This is a template for generating API documentation from Swagger YAML files. Replace placeholders with actual values from the YAML input.

---  

# FileSets API

> **Description:** Jupyter and AI Projects

---  

## Create a new FileSet

**Method:** `POST`  
**Endpoint:** `/api/files/v1/filesets`

**Path Parameters:**

_None_

**Query Parameters:**

_None_

**Request Body Parameters:**

| Parameter    | Type    | Required | Description                                 |
|--------------|---------|----------|---------------------------------------------|
| name         | string  | true     | The name for the file set.                  |
| description  | string  | false    | A description for the file set.             |
| connector    | string  | false    | The connector that powers the file set.     |
| aiEnabled    | boolean | false    | Indicates whether AI features are enabled for the file set. |

<!--  
type: tab  
title: Javascript  
-->  

```javascript
const requestBody = {
  name: "New FileSet",
  description: "This is a new FileSet",
  connector: "ExampleConnector",
  aiEnabled: true
};

fetch('/api/files/v1/filesets', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify(requestBody)
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
````

<!--  
type: tab  
title: Python  
-->  

```python
import requests
import json

url = 'https://example.com/api/files/v1/filesets'

payload = {
    "name": "New FileSet",
    "description": "This is a new FileSet",
    "connector": "ExampleConnector",
    "aiEnabled": True
}

headers = {'Content-Type': 'application/json'}

response = requests.post(url, headers=headers, data=json.dumps(payload))
print(response.json())
```

<!-- type: tab-end -->

---

**Response:**

```json
{
  "id": "e49f188e-be98-451d-ba0f-ada1157bb656",
  "name": "Policies (2025)",
  "description": "Location for all new and updated policies for FY2025",
  "aiEnabled": false,
  "batchType": "INCREMENTAL",
  "connector": "DOMO",
  "created": "2025-07-28T20:17:43.958479Z",
  "createdBy": 27,
  "updated": "2025-07-28T20:17:43.958479Z",
  "updatedBy": 27,
  "owner": "27",
  "accountId": 0,
  "connectorContext": null,
  "permission": "OWNER",
  "size": 0,
  "fileCount": 0
}
```

---  

## Get a FileSet by ID

**Method:** `GET`  
**Endpoint:** `/api/files/v1/filesets/{fileSetId}`

**Path Parameters:**

| Parameter | Type   | Required | Description                        |
|-----------|--------|----------|------------------------------------|
| fileSetId | string | true     | The ID of the FileSet to retrieve. |

**Query Parameters:**

_None_

**Request Body Parameters:**

_None_

<!--  
type: tab  
title: Javascript  
-->  

```javascript
const fileSetId = 'e49f188e-be98-451d-ba0f-ada1157bb656';

fetch(`/api/files/v1/filesets/${fileSetId}`, {
  method: 'GET',
  headers: {
    'Content-Type': 'application/json'
  }
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```

<!--  
type: tab  
title: Python  
-->  

```python
import requests

fileSetId = 'e49f188e-be98-451d-ba0f-ada1157bb656'
url = f'https://example.com/api/files/v1/filesets/{fileSetId}'

response = requests.get(url)
print(response.json())
```

<!-- type: tab-end -->

---

**Response:**

```json
{
  "id": "e49f188e-be98-451d-ba0f-ada1157bb656",
  "name": "Policies (2025)",
  "description": "Location for all new and updated policies for FY2025",
  "aiEnabled": false,
  "batchType": "INCREMENTAL",
  "connector": "DOMO",
  "created": "2025-07-28T20:17:43.958479Z",
  "createdBy": 27,
  "updated": "2025-07-28T20:17:43.958479Z",
  "updatedBy": 27,
  "owner": "27",
  "accountId": 0,
  "connectorContext": null,
  "permission": "OWNER",
  "size": 0,
  "fileCount": 0
}
```

---  

## Update FileSet Access Permissions

**Method:** `POST`  
**Endpoint:** `/api/files/v1/filesets/{fileSetId}/access`

**Path Parameters:**

| Parameter | Type   | Required | Description                                                        |
|-----------|--------|----------|--------------------------------------------------------------------|
| fileSetId | string | true     | The ID of the FileSet for which to update access permissions.      |

**Query Parameters:**

_None_

**Request Body Parameters:**

| Parameter      | Type   | Required | Description                                       |
|----------------|--------|----------|---------------------------------------------------|
| fileSetAccess  | array  | true     | The access permissions for the file set.         |

<!--  
type: tab  
title: Javascript  
-->  

```javascript
const fileSetId = 'e49f188e-be98-451d-ba0f-ada1157bb656';
const requestBody = {
  fileSetAccess: [
    {
      entityId: 42,
      entityType: 'GROUP',
      permission: 'EDIT'
    },
    {
      entityId: 27,
      entityType: 'USER',
      permission: 'OWNER'
    }
  ]
};

fetch(`/api/files/v1/filesets/${fileSetId}/access`, {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify(requestBody)
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```

<!--  
type: tab  
title: Python  
-->  

```python
import requests
import json

fileSetId = 'e49f188e-be98-451d-ba0f-ada1157bb656'
url = f'https://example.com/api/files/v1/filesets/{fileSetId}/access'

payload = {
    "fileSetAccess": [
        {
            "entityId": 42,
            "entityType": "GROUP",
            "permission": "EDIT"
        },
        {
            "entityId": 27,
            "entityType": "USER",
            "permission": "OWNER"
        }
    ]
}

headers = {'Content-Type': 'application/json'}

response = requests.post(url, headers=headers, data=json.dumps(payload))
print(response.json())
```

<!-- type: tab-end -->

---

**Response:**

```json
{
  "fileSetId": "e49f188e-be98-451d-ba0f-ada1157bb656",
  "fileSetAccess": [
    {
      "entityId": 42,
      "entityType": "GROUP",
      "permission": "EDIT"
    },
    {
      "entityId": 27,
      "entityType": "USER",
      "permission": "OWNER"
    }
  ]
}
```

---  

## List Files and Directories for a FileSet

**Method:** `POST`  
**Endpoint:** `/api/files/v1/filesets/{fileSetId}/files/search`

**Path Parameters:**

| Parameter | Type   | Required | Description                                 |
|-----------|--------|----------|---------------------------------------------|
| fileSetId | string | true     | The ID of the FileSet to search within.     |

**Query Parameters:**

| Parameter | Type     | Required | Description                                            |
|-----------|----------|----------|--------------------------------------------------------|
| directoryPath     | string   | false    | The path to the directory within the FileSet, if applicable. |
| immediateChildren | boolean  | false    | Whether to list only immediate children of the specified directory.     |
| limit             | integer  | false    | The maximum number of Files to return.                          |
| next              | string   | false    | The pagination token for the next set of results.               |

**Request Body Parameters:**

| Parameter   | Type  | Required | Description                                     |
|-------------|-------|----------|-------------------------------------------------|
| fieldSort   | array | false    | A list of field sort criteria to apply to the search.| 
| filters     | array | false    | A list of filters to apply to the search.        |
| dateFilters | array | false    | A list of date filters to apply to the search.   |

<!--  
type: tab  
title: Javascript  
-->  

```javascript
const fileSetId = 'e49f188e-be98-451d-ba0f-ada1157bb656';
const searchParams = {
  directoryPath: 'sample/directory/path',
  immediateChildren: false,
  limit: 10,
  next: 'pagination_token'
};
const requestBody = {
  fieldSort: [],
  filters: [],
  dateFilters: []
};

fetch(`/api/files/v1/filesets/${fileSetId}/files/search?${new URLSearchParams(searchParams)}`, {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify(requestBody)
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```

<!--  
type: tab  
title: Python  
-->  

```python
import requests
import json

fileSetId = 'e49f188e-be98-451d-ba0f-ada1157bb656'
url = f'https://example.com/api/files/v1/filesets/{fileSetId}/files/search'

queryParams = {
    "directoryPath": "sample/directory/path",
    "immediateChildren": False,
    "limit": 10,
    "next": "pagination_token"
}

payload = {
    "fieldSort": [],
    "filters": [],
    "dateFilters": []
}

headers = {'Content-Type': 'application/json'}

response = requests.post(url, headers=headers, params=queryParams, data=json.dumps(payload))
print(response.json())
```

<!-- type: tab-end -->

---

**Response:**

```json
{
  "files": [
    {
      "id": "7150e608-c3a9-4b40-ac2d-eb182cc98c6f",
      "path": "sample/directory/path/PaidTimeOffPolicy.pdf",
      "name": "PaidTimeOffPolicy.pdf",
      "fileType": "DOCUMENT",
      "contentType": "application/pdf",
      "size": 69502,
      "hash": "ce0da94c741125c597cf3d54a3202cebdc16d7fe1074698219f724654595221c",
      "hashAlgorithm": "SHA_256_HEX",
      "downloadUrl": "",
      "created": "2025-07-28T21:47:39.814456Z",
      "createdBy": 27,
      "connectorKey": null,
      "indexStatus": null,
      "indexReason": null
    }
  ],
  "pageContext": {
    "next": "eyJpZCI6ImJiZjU3MDVkLWU1ZjQtNGRkMy1hMTUyLTgzNzdhNTYwYzY0YiIsInBhdGgiOiJzYW1wbGUvZGlyZWN0b3J5L3BhdGgiLCJuYW1lIjoicGF0aCIsInNpemUiOm51bGwsImNyZWF0ZWQiOiIyMDI1LTA3LTI5VDE4OjA3OjI2Ljc2MzE5M1oifQ=="
  }
}
```

---  

## Submit a part of a file for upload.

**Method:** `POST`  
**Endpoint:** `/api/files/v1/filesets/{fileSetId}/files/multipart/{fileId}/part/{partNumber}`

**Path Parameters:**

| Parameter  | Type   | Required | Description                                                |
|------------|--------|----------|------------------------------------------------------------|
| fileSetId  | string | true     | The ID of the FileSet in which to the file is being uploaded.|
| fileId     | string | true     | The ID of the file being uploaded in parts.               |
| partNumber | integer| true     | The part number of this file segment. Must be non-negative.|

**Query Parameters:**

_None_

**Request Body Parameters:**

| Parameter | Type   | Required | Description                                                |
|-----------|--------|----------|------------------------------------------------------------|
| part      | string | true     | The full path destination for the file once the upload is complete. |

<!--  
type: tab  
title: Javascript  
-->  

```javascript
const fileSetId = 'e49f188e-be98-451d-ba0f-ada1157bb656';
const fileId = 'df5fd883-e5cb-4cbb-a158-0e9ff1d37097';
const partNumber = 1;
const requestBody = {
  part: 'sample/directory/path/PaidTimeOffPolicy.pdf'
};

fetch(`/api/files/v1/filesets/${fileSetId}/files/multipart/${fileId}/part/${partNumber}`, {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify(requestBody)
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```

<!--  
type: tab  
title: Python  
-->  

```python
import requests
import json

fileSetId = 'e49f188e-be98-451d-ba0f-ada1157bb656'
fileId = 'df5fd883-e5cb-4cbb-a158-0e9ff1d37097'
partNumber = 1
url = f'https://example.com/api/files/v1/filesets/{fileSetId}/files/multipart/{fileId}/part/{partNumber}'

payload = {
    "part": "sample/directory/path/PaidTimeOffPolicy.pdf"
}

headers = {'Content-Type': 'application/json'}

response = requests.post(url, headers=headers, data=json.dumps(payload))
print(response.json())
```

<!-- type: tab-end -->

---

**Response:**

```json
{
  "file": {
    "id": "df5fd883-e5cb-4cbb-a158-0e9ff1d37097",
    "path": "sample/directory/path/PaidTimeOffPolicy.pdf",
    "name": "PaidTimeOffPolicy.pdf",
    "fileType": "DOCUMENT",
    "contentType": "application/pdf",
    "size": 69502,
    "hash": null,
    "hashAlgorithm": "SHA_256_HEX",
    "downloadUrl": null,
    "created": "2025-08-25T16:05:56.676114Z",
    "createdBy": 27,
    "connectorKey": null,
    "indexStatus": null,
    "indexReason": null
  },
  "status": "PROCESSING"
}
```

---