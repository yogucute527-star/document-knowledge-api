# REST API + JSON

## API Overview

The **Document Knowledge API** demonstrates how different HTTP methods are used in a REST API. It provides multiple REST API endpoints that allow developers to **create, retrieve, update, and delete technical documents**.

The API is designed to help applications and developer tools access and manage technical documentation through standard HTTP requests and JSON responses.

## API Reference

The **API Reference** documents the available HTTP methods, endpoints, parameters, headers, request and response formats, and common status codes to help developers understand how to use each endpoint correctly.

## Authentication

The **Document Knowledge API** uses **Bearer Token authentication** to authenticate API requests. Developers must include a valid API token in the **Authorization** header when making authenticated requests.

`Authorization: Bearer <your-api-token>`

## Endpoints

The **Document Knowledge API** allows developers to **create, retrieve, update, and delete technical documents** using the following HTTP methods and endpoints:

- `GET /documents`
- `POST /documents`
- `GET /documents/{document_id}`
- `PUT /documents/{document_id}`
- `DELETE /documents/{document_id}`

## Request & Response Examples

Here are complete API request and response examples for the main endpoints, including the HTTP method, endpoint, headers, JSON request body, status code, and JSON response body.

### GET — Retrieve a Document

#### Request

`GET /documents/DOC-101`

`Authorization: Bearer <your-api-token>`

`Accept: application/json`

#### Response

`HTTP/1.1 200 OK`

`Content-Type: application/json`

#### JSON Response Body

```json
{
  "id": "DOC-101",
  "title": "REST API Guide",
  "status": "published"
}
```

### POST — Create a Document

#### Request

`POST /documents`

`Authorization: Bearer <your-api-token>`

`Content-Type: application/json`

`Accept: application/json`

#### Request Body

```json
{
  "title": "API Document"
}
```

#### Response

`HTTP/1.1 201 Created`

`Content-Type: application/json`

#### JSON Response Body

```json
{
  "id": "DOC-102",
  "title": "API Document",
  "status": "created"
}
```

### PUT — Update a Document

#### Request

`PUT /documents/DOC-101`

`Authorization: Bearer <your-api-token>`

`Content-Type: application/json`

`Accept: application/json`

#### Request Body

```json
{
  "title": "Knowledge Document"
}
```

#### Response

`HTTP/1.1 200 OK`

`Content-Type: application/json`

#### JSON Response Body

```json
{
  "id": "DOC-101",
  "title": "Knowledge Document",
  "status": "updated"
}
```

### DELETE — Delete a Document

#### Request

`DELETE /documents/DOC-102`

`Authorization: Bearer <your-api-token>`

`Accept: application/json`

#### Response

`HTTP/1.1 200 OK`

`Content-Type: application/json`

#### JSON Response Body

```json
{
  "id": "DOC-102",
  "title": "API Document",
  "status": "deleted"
}
```

## Errors

The **Document Knowledge API** uses HTTP status codes to indicate errors that may occur when processing API requests. The following table describes common error codes and provides basic troubleshooting guidance.

| Status Code | Error | Description | Resolution |
|---|---|---|---|
| **400** | Bad Request | The request is invalid or contains missing or incorrect data. | Check the request parameters and JSON body for missing or invalid values. |
| **401** | Unauthorized | The request is invalid or contains missing or incorrect data. | Check the **Authorization** header and provide a valid API token. |
| **403** | Forbidden | The authenticated user does not have permission to perform the requested operation. | Verify that the user has the required permissions. |
| **404** | Not Found | The requested resource or endpoint could not be found. | Check the endpoint URL and document ID. |
| **500** | Internal Server Error | The server encountered an unexpected problem while processing the request. | Retry the request later. If the problem persists, contact the API administrator. |
