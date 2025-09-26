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

| Parameter   | Type    | Required | Description                                   |
|-------------|---------|----------|-----------------------------------------------|
| name        | string  | true     | The name for the file set.                    |
| description | string  | false    | A description for the file set.               |
| connector   | string  | false    | The connector that powers the file set.       |
| aiEnabled   | boolean | false    | Indicates whether AI features are enabled for the file set. |

<!--
type: tab
title: Javascript
-->

```javascript
const requestBody = {
  name: "New FileSet",
  description: "Description for the new FileSet",
  connector: "DOMO",
  aiEnabled: false
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
```

<!--
type: tab
title: Python
-->

```python
import requests

url = "/api/files/v1/filesets"
data = {
    "name": "New FileSet",
    "description": "Description for the new FileSet",
    "connector": "DOMO",
    "aiEnabled": False
}

response = requests.post(url, json=data)
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
  "connector": "DOMO"
}
```

---

## Get a FileSet by ID

**Method:** `GET`  
**Endpoint:** `/api/files/v1/filesets/{fileSetId}`

**Path Parameters:**

| Parameter  | Type   | Required | Description                   |
|------------|--------|----------|-------------------------------|
| fileSetId  | string | true     | The ID of the FileSet to retrieve. |

**Query Parameters:**

_None_

**Request Body Parameters:**

_None_

<!--
type: tab
title: Javascript
-->

```javascript
const fileSetId = "e49f188e-be98-451d-ba0f-ada1157bb656";

fetch(`/api/files/v1/filesets/${fileSetId}`, {
  method: 'GET',
  headers: {
    'Accept': 'application/json'
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

file_set_id = "e49f188e-be98-451d-ba0f-ada1157bb656"
url = f"/api/files/v1/filesets/{file_set_id}"

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
  "connector": "DOMO"
}
```

---

## List Files and Directories for a FileSet

**Method:** `POST`  
**Endpoint:** `/api/files/v1/filesets/{fileSetId}/files/search`

**Path Parameters:**

| Parameter  | Type   | Required | Description                      |
|------------|--------|----------|----------------------------------|
| fileSetId  | string | true     | The ID of the FileSet to search within. |

**Query Parameters:**

| Parameter       | Type     | Required | Description                                            |
|-----------------|----------|----------|--------------------------------------------------------|
| directoryPath   | string   | false    | The path to the directory within the FileSet, if applicable. |
| immediateChildren | boolean | false    | Whether to list only immediate children of the specified directory. |
| limit           | integer  | false    | The maximum number of Files to return.                 |
| next            | string   | false    | The pagination token for the next set of results.      |

**Request Body Parameters:**

_None_

<!--
type: tab
title: Javascript
-->

```javascript
const fileSetId = "e49f188e-be98-451d-ba0f-ada1157bb656";
const searchParams = new URLSearchParams({
  "directoryPath": "sample/directory/path",
  "immediateChildren": true,
  "limit": 100
});

fetch(`/api/files/v1/filesets/${fileSetId}/files/search?${searchParams}`, {
  method: 'POST',
  headers: {
    'Accept': 'application/json'
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

file_set_id = "e49f188e-be98-451d-ba0f-ada1157bb656"
params = {
    "directoryPath": "sample/directory/path",
    "immediateChildren": True,
    "limit": 100
}

url = f"/api/files/v1/filesets/{file_set_id}/files/search"
response = requests.post(url, params=params)
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
      "size": 69502
    }
  ],
  "pageContext": {
    "next": "eyJpZCI6ImJiZjU3MDVkLWU1ZjQtNGRkMy1hMTUyLTgzNzdhNTYwYzY0YiIsInBhdGgiOiJzYW1wbGUvZGlyZWN0b3J5L3BhdGgiLCJuYW1lIjoicGF0aCIsInNpemUiOm51bGwsImNyZWF0ZWQiOiIyMDI1LTA3LTI5VDE4OjA3OjI2Ljc2MzE5M1oifQ=="
  }
}
```

---

## Finalize a split file upload

**Method:** `POST`  
**Endpoint:** `/api/files/v1/filesets/{fileSetId}/files/multipart/{fileId}/finalize`

**Path Parameters:**

| Parameter  | Type   | Required | Description                      |
|------------|--------|----------|----------------------------------|
| fileSetId  | string | true     | The ID of the FileSet in which the file has been uploaded. |
| fileId     | string | true     | The ID of the file whose parts have been uploaded. |

**Query Parameters:**

_None_

**Request Body Parameters:**

_None_

<!--
type: tab
title: Javascript
-->

```javascript
const fileSetId = "e49f188e-be98-451d-ba0f-ada1157bb656";
const fileId = "df5fd883-e5cb-4cbb-a158-0e9ff1d37097";

fetch(`/api/files/v1/filesets/${fileSetId}/files/multipart/${fileId}/finalize`, {
  method: 'POST',
  headers: {
    'Accept': 'application/json'
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

file_set_id = "e49f188e-be98-451d-ba0f-ada1157bb656"
file_id = "df5fd883-e5cb-4cbb-a158-0e9ff1d37097"
url = f"/api/files/v1/filesets/{file_set_id}/files/multipart/{file_id}/finalize"

response = requests.post(url)
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
    "size": 69502
  },
  "status": "SUCCESS"
}
```