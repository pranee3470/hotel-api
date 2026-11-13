# Hotel Management & Rating API

A RESTful backend application built with **Java 17**, **Spring Boot**, **Spring Data JPA**, and **H2**. It provides APIs to manage cities and hotels and retrieve rating summaries for hotels in a city.

## Features

- Create and retrieve cities.
- Create and retrieve hotels.
- Associate hotels with cities.
- Calculate the number of hotel ratings and average rating for a city.
- Provide health and readiness endpoints.
- Persist application data using an embedded H2 database.

## Tech Stack

- Java 17
- Spring Boot 3.1.4
- Spring Web
- Spring Data JPA / Hibernate
- H2 Database
- Maven
- JUnit 5 / Spring Boot Test

## Project Structure

```text
src/main/java/com/booking/recruitment/hotel/
├── controller/       # REST API controllers
├── dto/              # Response DTOs
├── exception/        # Custom exceptions
├── model/            # City and Hotel entities
├── repository/       # Spring Data JPA repositories
├── service/          # Service interfaces
│   └── impl/         # Service implementations
└── Application.java  # Spring Boot entry point
```

## Getting Started

### Prerequisites

- JDK 17
- Maven 3.6+ (or use the Maven wrapper if one is added to the project)

Check your installations:

```bash
java -version
mvn -version
```

### Run the application

Clone the repository and move into the project directory:

```bash
git clone <YOUR_REPOSITORY_URL>
cd <YOUR_PROJECT_DIRECTORY>
```

Build and run the tests:

```bash
mvn clean test
```

Start the application:

```bash
mvn spring-boot:run
```

The API runs at:

```text
http://localhost:8000
```

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/health` | Health check |
| GET | `/ready` | Readiness check |
| GET | `/city` | Retrieve all cities |
| POST | `/city` | Create a city |
| GET | `/hotel` | Retrieve all hotels |
| POST | `/hotel` | Create a hotel |
| GET | `/rating/city/{cityId}` | Get rating summary for a city |

### Example Requests

#### 1. Create a city

`POST /city`

```json
{
  "name": "Hyderabad",
  "cityCentreLatitude": 17.385,
  "cityCentreLongitude": 78.4867
}
```

#### 2. Create a hotel

`POST /hotel`

```json
{
  "name": "Example Hotel",
  "rating": 4.5,
  "city": {
    "id": 1
  },
  "address": "Hitech City, Hyderabad",
  "latitude": 17.4435,
  "longitude": 78.3772
}
```

Use an existing city ID in the `city` object.

#### 3. Get all cities

`GET /city`

#### 4. Get all hotels

`GET /hotel`

#### 5. Get a city's rating summary

`GET /rating/city/1`

Example response:

```json
{
  "numberOfRatings": 3,
  "averageRating": 4.2
}
```

The response values depend on the hotels and ratings stored in the application.

## Testing

Run the automated test suite with:

```bash
mvn test
```

## Notes

- The application uses an embedded H2 database.
- Hibernate is configured with `ddl-auto: create-drop`, so the schema is recreated when the application starts and the data is not intended for permanent storage.
- The examples above assume that the referenced city already exists.

