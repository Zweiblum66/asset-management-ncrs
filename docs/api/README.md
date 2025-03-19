# API Documentation

This directory contains the API documentation for the Asset Management and NCRS System.

## API Design Principles

Our APIs follow these design principles:

1. **RESTful Design**: Resources are identified by URLs, and standard HTTP methods are used for operations.
2. **JSON Format**: All APIs use JSON for request and response payloads.
3. **Versioning**: APIs are versioned to ensure backward compatibility.
4. **Authentication**: APIs require authentication via JWT tokens.
5. **Comprehensive Error Handling**: APIs return consistent error formats with appropriate HTTP status codes.
6. **Pagination**: Collection endpoints support pagination.
7. **Filtering and Sorting**: Collection endpoints support filtering and sorting.
8. **HATEOAS**: APIs include hypermedia links where appropriate.

## API Documentation Format

We use OpenAPI 3.0 (Swagger) for API documentation. The documentation is generated from code and available at the following endpoints in development:

- API Gateway: http://localhost:8080/api-docs
- Auth Service: http://localhost:8081/api-docs
- Asset Service: http://localhost:8082/api-docs
- Metadata Service: http://localhost:8083/api-docs
- Search Service: http://localhost:8084/api-docs

## API Endpoints

### Authentication and Authorization

- **POST /api/auth/login**: Authenticate a user and get a JWT token
- **POST /api/auth/refresh**: Refresh an expired JWT token
- **GET /api/auth/me**: Get the authenticated user's profile

### Asset Management

- **GET /api/assets**: List assets with pagination and filtering
- **POST /api/assets**: Create a new asset
- **GET /api/assets/{id}**: Get a specific asset
- **PUT /api/assets/{id}**: Update a specific asset
- **DELETE /api/assets/{id}**: Delete a specific asset
- **POST /api/assets/{id}/upload**: Upload a file for an asset
- **GET /api/assets/{id}/download**: Download the file for an asset

### Metadata Management

- **GET /api/metadata**: List metadata schemas
- **POST /api/metadata**: Create a new metadata schema
- **GET /api/metadata/{id}**: Get a specific metadata schema
- **PUT /api/metadata/{id}**: Update a specific metadata schema
- **DELETE /api/metadata/{id}**: Delete a specific metadata schema
- **GET /api/assets/{id}/metadata**: Get metadata for a specific asset
- **PUT /api/assets/{id}/metadata**: Update metadata for a specific asset

### Search

- **GET /api/search**: Search assets by various criteria
- **GET /api/search/suggest**: Get search suggestions
- **POST /api/search/advanced**: Perform advanced search

### Workflow Management

- **GET /api/workflows**: List workflow definitions
- **POST /api/workflows**: Create a new workflow definition
- **GET /api/workflows/{id}**: Get a specific workflow definition
- **PUT /api/workflows/{id}**: Update a specific workflow definition
- **DELETE /api/workflows/{id}**: Delete a specific workflow definition
- **GET /api/assets/{id}/workflows**: Get workflows for a specific asset
- **POST /api/assets/{id}/workflows**: Start a workflow for a specific asset
- **GET /api/tasks**: List tasks assigned to the current user
- **PUT /api/tasks/{id}**: Update a task status

### Distribution

- **GET /api/playlists**: List playlists
- **POST /api/playlists**: Create a new playlist
- **GET /api/playlists/{id}**: Get a specific playlist
- **PUT /api/playlists/{id}**: Update a specific playlist
- **DELETE /api/playlists/{id}**: Delete a specific playlist
- **POST /api/playlists/{id}/publish**: Publish a playlist to a destination

## Authentication

All API endpoints except for login and public endpoints require authentication. The authentication mechanism uses JWT tokens passed in the Authorization header:

```
Authorization: Bearer <token>
```

## Error Handling

API errors are returned in a consistent format:

```json
{
  "error": {
    "code": "ERROR_CODE",
    "message": "Human-readable error message",
    "details": {
      "field1": "Error for field1",
      "field2": "Error for field2"
    }
  }
}
```

## Pagination

Endpoints that return collections support pagination with the following query parameters:

- `page`: Page number (starting from 1)
- `limit`: Number of items per page
- `sort`: Field to sort by
- `order`: Sort order (`asc` or `desc`)

Response format for paginated collections:

```json
{
  "data": [
    // array of items
  ],
  "pagination": {
    "page": 1,
    "limit": 10,
    "totalItems": 42,
    "totalPages": 5
  }
}
```

## Cross-Origin Resource Sharing (CORS)

The API Gateway supports CORS to allow cross-origin requests from the frontend application. 