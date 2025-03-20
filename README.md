# Liveasy Load API Project

## Overview
This project is a backend application developed to manage and track loads efficiently. Built using **Spring Boot** and **PostgreSQL**, it provides a set of RESTful APIs for CRUD operations to handle load data.

## Features
- **Create, Read, Update, Delete (CRUD) Operations** on loads.
- **Database Integration** using PostgreSQL.
- Structured and scalable backend design.
- Ready for future enhancements like error handling, validation, and logging.

## Technologies Used
- **Spring Boot**: For building backend RESTful services.
- **PostgreSQL**: Relational database for structured data storage.
- **Hibernate (JPA)**: ORM framework for seamless database interaction.
- **Postman**: For API testing during development.

## API Endpoints

### POST `/load`
- **Description**: Create a new load entry.
- **Payload Example**:
  ```json
  {
    "facility": {
      "loadingPoint": "delhi",
      "unloadingPoint": "jaipur",
      "loadingDate": "2025-03-20",
      "unloadingDate": "2025-03-21"
    },
    "productType": "chemicals",
    "truckType": "canter",
    "noOfTrucks": 1,
    "weight": 100.0,
    "comment": "Test load",
    "shipperId": "shipper:12345",
    "date": "2025-03-20"
  }
  ```
- **Response**:
  ```json
  {
    "loadId": "load:<UUID>",
    "facility": {
      "loadingPoint": "delhi",
      "unloadingPoint": "jaipur",
      "loadingDate": "2025-03-20",
      "unloadingDate": "2025-03-21"
    },
    "productType": "chemicals",
    "truckType": "canter",
    "noOfTrucks": 1,
    "weight": 100.0,
    "comment": "Test load",
    "shipperId": "shipper:12345",
    "date": "2025-03-20"
  }
  ```

### GET `/load`
- **Description**: Retrieve all loads or filter loads by specific query parameters.
- **Query Parameters** (Optional):
  - `shipperId`
  - `truckType`
  - `productType`
  - `loadingPoint`
  - `unloadingPoint`
- **Response**:
  Returns a list of loads matching the query parameters, or all loads if no filters are applied.

### GET `/ShipperId/{ShipperId}`
- **Description**: Retrieve loads associated with a specific shipper ID.
- **Response**:
  ```json
  [
    {
      "loadId": "load:<UUID>",
      "facility": {
        "loadingPoint": "delhi",
        "unloadingPoint": "jaipur",
        "loadingDate": "2025-03-20",
        "unloadingDate": "2025-03-21"
      },
      "productType": "chemicals",
      "truckType": "canter",
      "noOfTrucks": 1,
      "weight": 100.0,
      "comment": "Test load",
      "shipperId": "shipper:12345",
      "date": "2025-03-20"
    }
  ]
  ```

### GET `/loadId/{loadId}`
- **Description**: Retrieve details of a specific load by `loadId`.
- **Response**:
  ```json
  {
    "loadId": "load:<UUID>",
    "facility": {
      "loadingPoint": "delhi",
      "unloadingPoint": "jaipur",
      "loadingDate": "2025-03-20",
      "unloadingDate": "2025-03-21"
    },
    "productType": "chemicals",
    "truckType": "canter",
    "noOfTrucks": 1,
    "weight": 100.0,
    "comment": "Test load",
    "shipperId": "shipper:12345",
    "date": "2025-03-20"
  }
  ```

### PUT `/load/{loadId}`
- **Description**: Update the details of an existing load.
- **Payload Example**:
  ```json
  {
    "facility": {
      "loadingPoint": "delhi",
      "unloadingPoint": "agra",
      "loadingDate": "2025-03-22",
      "unloadingDate": "2025-03-23"
    },
    "productType": "pharmaceuticals",
    "truckType": "container",
    "noOfTrucks": 2,
    "weight": 200.0,
    "comment": "Updated load",
    "shipperId": "shipper:12345",
    "date": "2025-03-22"
  }
  ```
- **Response**:
  Returns the updated load details.

### DELETE `/load/{loadId}`
- **Description**: Delete a specific load using `loadId`.
- **Response**:
  - HTTP Status Code: 204 (No Content)

## Project Setup

### Prerequisites
- Install [Java 17](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html)
- Install [PostgreSQL](https://www.postgresql.org/)
- Install [Maven](https://maven.apache.org/)

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/MohanPrasadKandru99/liveasy_assessment.git
   ```

2. Navigate to the project directory:
   ```bash
   cd liveasy_assessment
   ```

3. Configure the database connection in `application.properties`:
   ```properties
   spring.datasource.url=jdbc:postgresql://localhost:5432/liveasy
   spring.datasource.username=your_username
   spring.datasource.password=your_password
   spring.jpa.hibernate.ddl-auto=update
   ```

4. Run the application:
   ```bash
   ./mvnw spring-boot:run
   ```

## Testing the APIs
Use **Postman** or **cURL** to test the endpoints:

### Example cURL Commands:
- **POST `/load`**:
  ```bash
  curl -X POST http://localhost:8080/load \
  -H "Content-Type: application/json" \
  -d '{"facility":{"loadingPoint":"delhi","unloadingPoint":"jaipur","loadingDate":"2025-03-20","unloadingDate":"2025-03-21"},"productType":"chemicals","truckType":"canter","noOfTrucks":1,"weight":100.0,"comment":"Test load","shipperId":"shipper:12345","date":"2025-03-20"}'
  ```

- **GET `/load`**:
  ```bash
  curl http://localhost:8080/load
  ```
