#Dev 

## What is an API?
- **API (Application Programming Interface)**: A set of rules that allows one piece of software application to talk to another.
- **Types**: Web APIs, Library APIs, OS APIs, etc.
- **Web API**: Facilitates interaction over the web (HTTP/HTTPS).

## REST API

### Key Concepts
- **REST (Representational State Transfer)**: An architectural style for designing networked applications.
- **Stateless**: Each request from client to server must contain all the information needed to understand and process the request.
- **Resource**: Objects or data represented as URLs (Uniform Resource Locators).
- **Methods (HTTP Verbs)**:
  - **GET**: Retrieve a resource.
  - **POST**: Create a new resource.
  - **PUT**: Update an existing resource.
  - **DELETE**: Delete a resource.
  - **PATCH**: Partially update a resource.

#### Common Headers
- **Content-Type**: The media type of the resource (e.g., `application/json`).
- **Authorization**: Credentials for authentication (e.g., `Bearer token`).
- **Accept**: The media type that is acceptable for the response.

#### Status Codes
- **200 OK**: The request succeeded.
- **201 Created**: The resource was successfully created.
- **204 No Content**: The request succeeded, but no content is returned.
- **400 Bad Request**: The request was invalid.
- **401 Unauthorized**: Authentication is required.
- **403 Forbidden**: The server understood the request but refuses to authorize it.
- **404 Not Found**: The resource could not be found.
- **500 Internal Server Error**: An error occurred on the server.

#### Example: REST API Request
```http
GET /api/books HTTP/1.1
Host: example.com
Authorization: Bearer YOUR_ACCESS_TOKEN
Accept: application/json
```

#### Example: REST API Response
```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "id": 1,
        "title": "1984",
        "author": "George Orwell"
    },
    {
        "id": 2,
        "title": "To Kill a Mockingbird",
        "author": "Harper Lee"
    }
]
```

## SOAP API

#### Key Concepts
- **SOAP (Simple Object Access Protocol)**: A protocol for exchanging structured information in web services.
- **XML-based**: Messages are formatted in XML.
- **Envelope**: The root element of a SOAP message, containing a header and body.

#### Common Headers
- **Content-Type**: `text/xml; charset=utf-8`
- **SOAPAction**: Indicates the intent of the SOAP HTTP request.

#### Status Codes
- **200 OK**: The request succeeded.
- **500 Internal Server Error**: An error occurred on the server.

#### Example: SOAP Request
```xml
POST /calculator.asmx HTTP/1.1
Host: www.dneonline.com
Content-Type: text/xml; charset=utf-8
SOAPAction: "http://tempuri.org/Add"

<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <Add xmlns="http://tempuri.org/">
      <intA>5</intA>
      <intB>3</intB>
    </Add>
  </soap:Body>
</soap:Envelope>
```

#### Example: SOAP Response
```xml
HTTP/1.1 200 OK
Content-Type: text/xml; charset=utf-8

<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <AddResponse xmlns="http://tempuri.org/">
      <AddResult>8</AddResult>
    </AddResponse>
  </soap:Body>
</soap:Envelope>
```

## Best Practices

### REST API Best Practices
1. **Use Nouns for Resources**: Resource names should be nouns and not verbs (e.g., `/users` not `/getUsers`).
2. **Use HTTP Methods Appropriately**: Map CRUD operations to HTTP methods (GET, POST, PUT, DELETE).
3. **Versioning**: Use versioning in your API (e.g., `/v1/users`).
4. **Pagination**: Implement pagination for large datasets.
5. **Error Handling**: Provide meaningful error messages and status codes.
6. **Security**: Use HTTPS and proper authentication methods (OAuth, API keys).

#### SOAP API Best Practices
1. **Use WS-Security**: Implement WS-Security for secure communication.
2. **WSDL**: Always provide a WSDL file for service definition.
3. **Error Handling**: Use SOAP Fault for error messages.
4. **Versioning**: Use namespaces to manage different versions of the service.
MM