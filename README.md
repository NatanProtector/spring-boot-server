# Basic Spring Server

This is a basic server built using **Java Spring Boot** and a **PostgreSQL** database.

The application is a **Student Management System**, where users can:

- Perform full **CRUD operations** on student records
- Query student **grades and details**
- Register and authenticate using **JWT tokens** for secure access
- Benefit from **exception handlers** that provide readable error messages
- Run **automated tests** using **Newman**
- Easily deploy and run the project via **Docker**

➡️ The project is fully dockerized and available on Docker Hub:  
🔗 [https://hub.docker.com/r/natanprotector/basic-spring-natanprotector](https://hub.docker.com/r/natanprotector/basic-spring-natanprotector)

---

## Technologies Used

- **Java 17**
- **Spring Boot**
- **PostgreSQL**
- **JWT (JSON Web Tokens)**
- **Docker**
- **Kubernetes**
- **Swagger / OpenAPI**
- **Newman (for Postman test automation)**

---

## Getting Started

## Main method

To run the app with testing support:

1. Start the app with the CI-specific Docker Compose file:

   ```bash
   docker-compose -f docker-compose-ci.yml up -d --force-recreate --build

2. close the app using the command:
   
   ```bash
   docker kill $(docker ps -q)

## View app
After app started use http://localhost:8080/swagger-ui.html#/ to view API routes

## Authentication
Use the signup routes to register an account, then use the token you received in return by clicking the "Authorize" button in the menu bar. Enter the value "Bearer {your_token}" to be granted access to the APIs.

# Alternative methods (unavailable for windows for now)
## Alternative method 1

1. **SBuild the container manually:**

   ```bash
   docker build . -t basic-sprin

2. **Run the database and server together:**

   ```bash
   docker-compose -f docker-compose-local.yml up --force-recreate

## Alternative method 2

1. **Start the database using Docker Compose:**

   ```bash
   docker-compose up

2. **Run the application:**

Open your IDE and run the BasicApplication.java file (the main entry point).


# Testing (for main method only)

1. Run the following to wait for the server to be ready:
   ```bash
   docker-compose -f docker-compose-ci.yml run wait -c server:8080 -t 120

2. Then execute the Newman tests:
   ```bash
   docker exec spring-boot-server_newman_1 newman run STUDENTS_TEST.postman_collection.json --reporters cli,junit,htmlextra --reporter-junit-export "newman/report.xml" --reporter-htmlextra-export "newman/report.html"

The test results will be saved in the ./test/newman/ directory.


## Acknowledgments

This project was developed as part of the Hands-On Programming course by Niv Itzhaki.

Through this experience, I had the opportunity to explore many amazing technologies and gain practical knowledge in backend development, security, testing, and DevOps.

Huge thanks to Niv Itzhaki for the guidance and support throughout the course!