# Hoen Scanner

A Java REST backend implementation for a Skyscanner backend engineering task, built with **Dropwizard**, **Jersey**, **Jackson**, and bundled hotel and rental-car datasets.

## Overview

Hoen Scanner loads hotel and rental-car records from JSON resources and exposes a city-based search endpoint.

At startup, the application:

1. Loads `hotels.json` and `rental_cars.json`.
2. Combines the records into an in-memory search collection.
3. Registers a REST resource at `/search`.

## Tech Stack

- Java 11
- Dropwizard 4.0.0-beta.3
- Jersey / JAX-RS
- Jackson
- Maven
- JSON

## API

### POST /search

Request:

```json
{
  "city": "London"
}
```

The service returns matching results for the requested city.

Example response:

```json
[
  {
    "city": "London",
    "title": "Example result",
    "kind": "hotel"
  }
]
```

The exact results depend on the bundled JSON datasets.

## Project Structure

```text
.
├── src/
│   └── main/
│       ├── java/com/skyscanner/
│       │   ├── HoenScannerApplication.java
│       │   ├── HoenScannerConfiguration.java
│       │   ├── Search.java
│       │   ├── SearchResource.java
│       │   └── SearchResult.java
│       └── resources/
│           ├── banner.txt
│           ├── hotels.json
│           └── rental_cars.json
├── config.yml
├── pom.xml
├── .gitignore
└── README.md
```

## Running Locally

### Prerequisites

- Java 11 or later
- Maven

### Build

```bash
mvn clean package
```

### Run

```bash
java -jar target/hoen-scanner-1.0-SNAPSHOT.jar server config.yml
```

## Project Context

This repository is based on the Skyscanner backend engineering task and focuses on implementing the provided search service using a small in-memory dataset.
