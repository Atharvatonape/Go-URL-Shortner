
# Go URL Link Shortener API

## Overview
The Go URL Link Shortener API is a web service that allows users to shorten long URLs and retrieve them later using their corresponding short URLs. This project is designed for educational purposes to demonstrate how to create an efficient REST API in Go, interface with MongoDB, and follow best practices in web service development.

## Features
- Shorten long URLs using a simple POST request.
- Redirect to the original URL using a short URL.
- Includes API routes for creating and consuming short URLs.
- Efficient MongoDB integration using the `mgo` library.
- Routing and HTTP handling with Gorilla Mux.

## Project Structure
```
|-- PyTestClient
    |-- myrequests.py
|-- README.md
|-- GoLinkShortener
    |-- handlers.go
    |-- dbLayer.go
    |-- LinkShortner.go
    |-- routes.go
    |-- router.go
|-- structure.txt
```

### File Descriptions
- **PyTestClient/myrequests.py**: Python script to test the API with a POST request.
- **GoLinkShortener/handlers.go**: Contains the API's core handlers for creating and consuming short URLs.
- **GoLinkShortener/dbLayer.go**: Database layer that interfaces with MongoDB.
- **GoLinkShortener/LinkShortner.go**: Entry point for the API server.
- **GoLinkShortener/routes.go**: Defines the API routes and their corresponding handlers.
- **GoLinkShortener/router.go**: Implements the routing logic using Gorilla Mux.
- **README.md**: Documentation for the project.
- **structure.txt**: Details the directory structure and file content for reference.

## Prerequisites
- [Go](https://go.dev/) installed on your system.
- [MongoDB](https://www.mongodb.com/) running locally or accessible remotely.
- [Gorilla Mux](https://www.gorillatoolkit.org/pkg/mux) Go package.
- [mgo](https://labix.org/mgo) Go package for MongoDB interaction.

## Installation
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd GoLinkShortener
   ```
2. Install dependencies:
   ```bash
   go get -u github.com/gorilla/mux
   go get -u gopkg.in/mgo.v2
   ```
3. Ensure MongoDB is running locally or update the connection string in `dbLayer.go` if using a remote instance.

## Running the API
1. Start the Go server:
   ```bash
   go run LinkShortner.go
   ```
   The server will start on `http://localhost:5100`.

2. Use the provided Python script or any REST client to test the API.

## API Endpoints
### 1. Create Short URL
- **Endpoint**: `/Create`
- **Method**: POST
- **Request Body**:
  ```json
  {
    "shorturl": "<short-url>",
    "longurl": "<long-url>"
  }
  ```
- **Response**:
  ```json
  {
    "statusmessage": "Ok"
  }
  ```

### 2. Get Original URL
- **Endpoint**: `/{shorturl}`
- **Method**: GET
- **Description**: Redirects to the original long URL if the short URL exists.

### 3. API Root
- **Endpoint**: `/`
- **Method**: GET
- **Response**: Describes how to use the API.

## Example Usage
### Using the Python Test Client
Run the Python script located in `PyTestClient/myrequests.py`:
```bash
python myrequests.py
```
Example output:
```
Status code received: 200 response body: {"statusmessage":"Ok"}
```

## Project Highlights
- Utilizes a unique MongoDB index to prevent duplicate short URLs.
- Demonstrates efficient session handling with MongoDB's socket pooling.
- Provides clear and modular code structure for easy extensibility.
- Error handling included for robust API behavior.

## Contributions
Contributions are welcome! Please open an issue or submit a pull request for improvements or bug fixes.

## License
This project is provided as-is for educational purposes and does not include a specific license. Please contact the author for any commercial use.

## Author
Written and authored by **Atharva Tonape**.

---

