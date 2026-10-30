# AI API Integration

## AI API Overview

The **Document Knowledge AI API** allows applications to communicate with an AI model and use its capabilities, such as generating, summarizing, and analyzing content.

An application sends a request to the AI API containing the required authentication, HTTP method, endpoint, input or prompt, and optional parameters. The AI API processes the request using the AI model and returns the generated result to the application.

### Basic Flow

Application

↓

AI API Request

↓

AI Model

↓

AI API Response

↓

Application

The AI API uses standard HTTP requests and responses to communicate between the application and the AI service.

## Authentication

The **Document Knowledge AI API** needs to know who is making an API request and whether the application is authorized to use the API. The application therefore sends authentication credentials with the request so the API provider can verify the caller and process the request.

The AI API uses an API key for authentication. An API key is a secret credential that identifies and authenticates the application or user making the API request.

### Authorization Header

The API key is sent in the **Authorization** header:

`Authorization: Bearer <your-api-key>`

Replace **`<your-api-key>`** with a valid API key provided by the API provider.

**Security:** Never expose a real API key in source code, public documentation, screenshots, or public repositories.

## Request Response

### AI API Request

A **Document Knowledge AI API request** sends input or prompt data to the AI API for processing. The request can include authentication, headers, and a request body containing the prompt and other input parameters.

#### Example

`POST /ai/generate`

`Authorization: Bearer <your-api-key>`

`Content-Type: application/json`

```json
{
  "prompt": "Explain REST APIs in simple terms."
}
```

### AI API Response

The **Document Knowledge AI API response** contains the result returned after the API processes the request.

#### Example

`200 OK`

`Content-Type: application/json`

```json
{
  "response": "A REST API allows software applications to communicate..."
}
```

## Prompt Parameters

### Prompt

A prompt is the input or instruction provided to the AI model that defines what the model should do.

For example:

```json
{
  "prompt": "Explain REST APIs in simple terms."
}
```

### Parameters

Parameters are settings sent with a **Document Knowledge AI API request** that control how the request is processed or how the model generates its response.

For example:

```json
{
  "prompt": "Explain REST APIs in simple terms.",
  "temperature": 0.2,
  "max_tokens": 150
}
```

In this example:

| Parameter | Description |
|---|---|
| `temperature` | Controls the variability of the generated response. |
| `max_tokens` | Limits the amount of generated output. |

## Structured Output

Structured output allows a **Document Knowledge AI API** to return responses in a defined and predictable format. This makes the response easier for applications to read, process, and use in automated workflows.

For example, an application can request an AI response using specific fields:

```json
{
  "issue": "Customer cannot access their account.",
  "priority": "high"
}
```

The defined structure allows the application to reliably access fields such as **`issue`** and **`priority`** instead of interpreting free-form text.

## Integration Guide

The **Document Knowledge AI API** can be integrated into an application by sending an authenticated HTTP request containing the required prompt and optional parameters.

### Integration Flow

Application

↓

Authenticate request

↓

Send AI API request

↓

AI model processes the request

↓

Receive AI API response

↓

Application uses the generated result

### Example Request

`POST /ai/generate`

`Authorization: Bearer <your-api-key>`

`Content-Type: application/json`

```json
{
  "prompt": "Summarize this document in 3 bullet points.",
  "temperature": 0.2,
  "max_tokens": 150
}
```

### Example Response

`200 OK`

`Content-Type: application/json`

```json
{
  "response": [
    "Point one...",
    "Point two...",
    "Point three..."
  ]
}
```

The application can process the returned response and use the generated content in its workflow.
