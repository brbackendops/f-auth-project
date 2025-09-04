# Developed Authentication in Go lang , Python & Node.js

##### Note

I developed this project in three langauges because I have over 2+ exp in backend development. And Because the project is small, I thought it will be good idea to go for all options. I have tried my best with this test and rest is up to you !
[ skipped kubernetes implementation , logging , EFL stack ] (I thought to implement this but I have no time to go for it ...! )

#### CI pipeline with github actions

* Included CI pipeline with github action to automate workflow for reducing errors
* applied branch rules to f-python-auth only
* added three stages build , test & docker build & push (hub)
* skipped docker vulnerability check
* skipped code quality checks

#### Python (Django | postgresql | redis | django way)

* .env included as per rules
* implemented two endpoints

  * /signup
  * /login
* Implemented JWT authentication
* developed a custom rate limiter from scratch

  * used redis for tracking requests
  * based on fixed window algorithm
  * applied to /signup route
  * /apps/users/utils/limiter.py
* swagger included at

  * /swagger
  * /api-doc
* tests

  * unit tests for models
  * Integration test
    * used sqlite in-memory database for tests
* input validation is acheived through serializers
* docker

  * added Dockerfile to create containerize our application
  * added docker-compose file for running application with multiple containers
  * added docker-swarm file for managing multiple containers (if swarm is used to manage containers)

#### Go lang (fiber | postgresql | sqlx | layered architecture)

* .env included as per rules
* used naked orm like sqlx (efficient than gorm and others)
* implemented two endpoints
  * /signup
  * /login
* rate limiter added for /signup
* tests
  * unit tests for repository and service layers
  * used gomock and sqlmock for mocking some functions in unittests
  * Integration test
    * used sqlite in-memory database
  * go test -v ./...
  * input validation is acheived through middlewares
* docker
  * added Dockerfile to create containerize our application
  * added docker-compose file for running application with multiple containers
  * added docker-swarm file for managing multiple containers (if swarm is used to manage containers)

#### Node js (expressjs | postgresql | prisma orm | layered architecture)

* .env included as per rules
* global error handling is implemented but not enabled as this requires minimal details about errors
* implemented two endpoints
  * /signup
  * /login
* rate limiter added for /signup
  * fixed window
* input validation is acheived with Joi and implemented as middleware
* swagger added
  * /v1/swagger
* tests
  * unit tests for repository and service layers
  * API tests ( not integration test as I used to mock some layers )
  * used jest test framework
  * npm run test
* docker
  * added Dockerfile to create containerize our application
  * added docker-compose file for running application with multiple containers
  * added docker-swarm file for managing multiple containers (if swarm is used to manage containers)
