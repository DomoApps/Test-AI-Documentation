# Product API Template

> **Note:** This is a template for generating API documentation from Swagger YAML files. Replace placeholders with actual values from the YAML input.

---

# Domo AI API

> **Description:** Jupyter and AI Projects

---

## Text Summarization

**Method:** `post`  
**Endpoint:** `/api/ai/v1/text/summarize`

**Path Parameters:**

_None_

**Query Parameters:**

_None_

**Request Body Parameters:**

| Parameter         | Type   | Required | Description                                                            |
|-------------------|--------|----------|------------------------------------------------------------------------|
| input             | string | true     | Text information to be summarized.                                     |
| outputWordLength  | object | false    | Defines a size boundary to limit the length of the output summary, based on number of words. |

<!--
type: tab
title: Javascript
-->

```javascript
fetch('/api/ai/v1/text/summarize', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    input: "Your text here",
    outputWordLength: {"min": 50, "max": 100}
  })
})
.then(response => response.json())
.then(data => console.log(data));
```

<!--
type: tab
title: Python
-->

```python
import requests

url = '/api/ai/v1/text/summarize'
payload = {
    "input": "Your text here",
    "outputWordLength": {"min": 50, "max": 100}
}
headers = {'Content-Type': 'application/json'}

response = requests.post(url, json=payload, headers=headers)
print(response.json())
```

<!-- type: tab-end -->

---

**Response:**

```json
{
  "description": "Text Summarization Response",
  "output": "Vibrant, densely populated commercial and cultural hub in Northern California."
}
```

---

## Text-to-SQL

**Method:** `post`  
**Endpoint:** `/api/ai/v1/text/sql`

**Path Parameters:**

_None_

**Query Parameters:**

_None_

**Request Body Parameters:**

| Parameter           | Type   | Required | Description |
|---------------------|--------|----------|-------------|
| dataSourceSchemas   | array  | true     | The data source schemas and metadata to be included in the Text-to-SQL task prompt to generate SQL. |

<!--
type: tab
title: Javascript
-->

```javascript
fetch('/api/ai/v1/text/sql', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    dataSourceSchemas: ["schema1", "schema2"]
  })
})
.then(response => response.json())
.then(data => console.log(data));
```

<!--
type: tab
title: Python
-->

```python
import requests

url = '/api/ai/v1/text/sql'
payload = {
    "dataSourceSchemas": ["schema1", "schema2"]
}
headers = {'Content-Type': 'application/json'}

response = requests.post(url, json=payload, headers=headers)
print(response.json())
```

<!-- type: tab-end -->

---

**Response:**

```json
{
  "description": "Text-to-SQL Response",
  "output": "SELECT region, SUM(amount) AS total_sales FROM `Store Sales` GROUP BY region"
}
```

---

## Text Generation

**Method:** `post`  
**Endpoint:** `/api/ai/v1/text/generation`

**Path Parameters:**

_None_

**Query Parameters:**

_None_

**Request Body Parameters:**

| Parameter         | Type   | Required | Description |
|-------------------|--------|----------|-------------|
| input             | string | true     | Text information to be summarized. |

<!--
type: tab
title: Javascript
-->

```javascript
fetch('/api/ai/v1/text/generation', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    input: "Your prompt here"
  })
})
.then(response => response.json())
.then(data => console.log(data));
```

<!--
type: tab
title: Python
-->

```python
import requests

url = '/api/ai/v1/text/generation'
payload = {
    "input": "Your prompt here"
}
headers = {'Content-Type': 'application/json'}

response = requests.post(url, json=payload, headers=headers)
print(response.json())
```

<!-- type: tab-end -->

---

**Response:**

```json
{
  "description": "Text Generation Response",
  "output": "The sky is blue because of Rayleigh scattering."
}
```

---

## Text-to-BeastMode

**Method:** `post`  
**Endpoint:** `/api/ai/v1/text/beastmode`

**Path Parameters:**

_None_

**Query Parameters:**

_None_

**Request Body Parameters:**

| Parameter           | Type   | Required | Description |
|---------------------|--------|----------|-------------|
| dataSourceSchema    | object | true     | The data source schema and metadata to be included in the Text-to-Beast-Mode task prompt to generate a SQL Calculation. |

<!--
type: tab
title: Javascript
-->

```javascript
fetch('/api/ai/v1/text/beastmode', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    dataSourceSchema: {"schemaKey": "schemaValue"}
  })
})
.then(response => response.json())
.then(data => console.log(data));
```

<!--
type: tab
title: Python
-->

```python
import requests

url = '/api/ai/v1/text/beastmode'
payload = {
    "dataSourceSchema": {"schemaKey": "schemaValue"}
}
headers = {'Content-Type': 'application/json'}

response = requests.post(url, json=payload, headers=headers)
print(response.json())
```

<!-- type: tab-end -->

---

**Response:**

```json
{
  "description": "Text-to-Beast-Mode Response",
  "output": "COUNT(DISTINCT `product`)"
}
```

---

## Tool Calling

**Method:** `post`  
**Endpoint:** `/api/ai/v1/messages/tools`

**Path Parameters:**

_None_

**Query Parameters:**

_None_

**Request Body Parameters:**

| Parameter         | Type   | Required | Description |
|-------------------|--------|----------|-------------|
| tools             | array  | true     | The list of tools the model can call. |

<!--
type: tab
title: Javascript
-->

```javascript
fetch('/api/ai/v1/messages/tools', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    tools: ["tool1", "tool2"]
  })
})
.then(response => response.json())
.then(data => console.log(data));
```

<!--
type: tab
title: Python
-->

```python
import requests

url = '/api/ai/v1/messages/tools'
payload = {
    "tools": ["tool1", "tool2"]
}
headers = {'Content-Type': 'application/json'}

response = requests.post(url, json=payload, headers=headers)
print(response.json())
```

<!-- type: tab-end -->

---

**Response:**

```json
{
  "description": "Tool Calling Response",
  "output": "Certainly! I'd be happy to help you find a blue coat."
}
```

---

## Chat Messages

**Method:** `post`  
**Endpoint:** `/api/ai/v1/messages/chat`

**Path Parameters:**

_None_

**Query Parameters:**

_None_

**Request Body Parameters:**

| Parameter         | Type   | Required | Description |
|-------------------|--------|----------|-------------|
| input             | string | true     | Text information to be summarized. |

<!--
type: tab
title: Javascript
-->

```javascript
fetch('/api/ai/v1/messages/chat', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    input: "Your chat message here"
  })
})
.then(response => response.json())
.then(data => console.log(data));
```

<!--
type: tab
title: Python
-->

```python
import requests

url = '/api/ai/v1/messages/chat'
payload = {
    "input": "Your chat message here"
}
headers = {'Content-Type': 'application/json'}

response = requests.post(url, json=payload, headers=headers)
print(response.json())
```

<!-- type: tab-end -->

---

**Response:**

```json
{
  "description": "Chat Messages Response",
  "output": "The sky appears blue due to a phenomenon called Rayleigh scattering."
}
```

---

## Image to Text

**Method:** `post`  
**Endpoint:** `/api/ai/v1/image/text`

**Path Parameters:**

_None_

**Query Parameters:**

_None_

**Request Body Parameters:**

| Parameter | Type   | Required | Description  |
|-----------|--------|----------|--------------|
| image     | object | true     | The image to analyze and extract text from. |

<!--
type: tab
title: Javascript
-->

```javascript
fetch('/api/ai/v1/image/text', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    image: {"imageKey": "imageValue"}
  })
})
.then(response => response.json())
.then(data => console.log(data));
```

<!--
type: tab
title: Python
-->

```python
import requests

url = '/api/ai/v1/image/text'
payload = {
    "image": {"imageKey": "imageValue"}
}
headers = {'Content-Type': 'application/json'}

response = requests.post(url, json=payload, headers=headers)
print(response.json())
```

<!-- type: tab-end -->

---

**Response:**

```json
{
  "description": "Image to Text Response",
  "output": "This image shows a small red square on a white background."
}
```

---

## Text Embeddings

**Method:** `post`  
**Endpoint:** `/api/ai/v1/embedding/text`

**Path Parameters:**

_None_

**Query Parameters:**

_None_

**Request Body Parameters:**

| Parameter         | Type   | Required | Description |
|-------------------|--------|----------|-------------|
| input             | string | true     | Text information to be summarized. |

<!--
type: tab
title: Javascript
-->

```javascript
fetch('/api/ai/v1/embedding/text', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    input: "Your text here"
  })
})
.then(response => response.json())
.then(data => console.log(data));
```

<!--
type: tab
title: Python
-->

```python
import requests

url = '/api/ai/v1/embedding/text'
payload = {
    "input": "Your text here"
}
headers = {'Content-Type': 'application/json'}

response = requests.post(url, json=payload, headers=headers)
print(response.json())
```

<!-- type: tab-end -->

---

**Response:**

```json
{
  "description": "Embedding Response",
  "output": "[[0.1, 0.2, 0.3, 0.4, 0.5]]"
}
```

---

## Image Embeddings

**Method:** `post`  
**Endpoint:** `/api/ai/v1/embedding/image`

**Path Parameters:**

_None_

**Query Parameters:**

_None_

**Request Body Parameters:**

| Parameter | Type   | Required | Description  |
|-----------|--------|----------|--------------|
| image     | object | true     | The image to analyze and extract text from. |

<!--
type: tab
title: Javascript
-->

```javascript
fetch('/api/ai/v1/embedding/image', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    image: {"imageKey": "imageValue"}
  })
})
.then(response => response.json())
.then(data => console.log(data));
```

<!--
type: tab
title: Python
-->

```python
import requests

url = '/api/ai/v1/embedding/image'
payload = {
    "image": {"imageKey": "imageValue"}
}
headers = {'Content-Type': 'application/json'}

response = requests.post(url, json=payload, headers=headers)
print(response.json())
```

<!-- type: tab-end -->

---

**Response:**

```json
{
  "description": "Embedding Response",
  "output": "[[0.1, 0.2, 0.3, 0.4, 0.5]]"
}
```

---