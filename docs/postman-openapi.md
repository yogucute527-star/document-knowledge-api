# Postman + OpenAPI

## Postman Collection

This Postman collection groups the API requests for the **Document Knowledge API** in one place for easier organization, reuse, and testing.

The **Document Knowledge API** collection contains the following related API requests:

- `GET /documents`
- `GET /documents/{document_id}`
- `POST /documents`
- `PUT /documents/{document_id}`
- `DELETE /documents/{document_id}`

## OpenAPI Specification

The OpenAPI specification for the **Document Knowledge API** documents the API endpoints and defines how developers can interact with those endpoints.

### Example

```yaml
paths:
  /documents/{document_id}:
    get:
      summary: Retrieve a document
      parameters:
        - name: document_id
          in: path
          required: true
          schema:
            type: string
      responses:
        '200':
          description: Document retrieved successfully
        '404':
          description: Document not found
```

### OpenAPI Elements

| Element | Purpose |
|---|---|
| `paths` | Defines the API endpoints. |
| `/documents/{document_id}` | Defines the endpoint for accessing a specific document. |
| `get` | Defines the GET operation for the endpoint. |
| `summary` | Provides a short description of the operation. |
| `parameters` | Defines the parameters accepted by the operation. |
| `document_id` | The name of the path parameter. |
| `in: path` | Specifies that `document_id` is part of the URL path. |
| `required: true` | Indicates that the parameter is required. |
| `schema` | Defines the parameter's data structure or type. |
| `type: string` | Specifies that `document_id` accepts a string value. |
| `responses` | Defines the possible API responses. |
| `200` | Document was retrieved successfully. |
| `404` | The requested document was not found. |

## API Testing Documentation

API testing of the **Document Knowledge API** checks whether the API returns the expected response. It verifies whether a response is returned, whether the status code is correct, whether the returned data is correct, and whether the API behaves correctly when invalid data is provided.

Here are the API tests and their results:

| Test | Expected | Actual | Result |
|---|---:|---:|---|
| GET existing document | 200 | 200 | Pass |
| GET invalid document | 404 | 404 | Pass |
| POST valid document | 201 | 201 | Pass |
