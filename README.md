### Prerequisites

This Project is build using Spring boot (2.1.5) and Maven. Its starter project is created using spring provided starter interface. https://start.spring.io/.

Additionally H2 database is used, which is in memory database and respective dependancy added into pom.xml file.

```
* JDK 8 ( JAVA )
* [Maven](https://maven.apache.org/) - Dependency Management
* H2 Database - In Memory database ( no need to install as spring manage it internally ) 
```


### Installation & Use source code

Since maven is used as a dependancy management tool, you can import this as a maven project into eclipse. Refer deployment section for getting more details if you want to create and deploy build into standalone container like tomcat or jetty container.

All the services are well documented inside the code in *com.ketul.springboot.onlinestore.retailstore.service* package

#### Spring/Java features used
- spring-boot-starter-data-jpa : For persistence API
- spring-boot-starter-web : To provide spring mvc support
- dozer : for mapping of Request bean to BL bean. It's not good practice to use directly request bean !!!!!!
- spring-boot-starter-tomcat : tomcat container
- com.h2database.h2 : In memory database

#### Class diagram and details
[Class Diagram](https://github.com/ktool/retailstore/blob/master/Class_diagram.png)

#### Sample data:
Inside /src/main/resources, i added **data.sql** file which will insert some test data when application context loads into H2 database. So no need to create and manage external database system.

## Running the tests

Tests can be run either on the Code editor (e.g. eclipse) and also one can use maven command line tool: 
```
mvn clean test
```

``Note: To run the project into eclipse, product needs to be imported into eclipse as a maven export`` and 
then from run configuration -> Maven Test

### Integration tests

Integration test include the 1 test of User Repository test to verify the DAO layer.
Service layer tests includes 3 tests for each user type. Store Employee, Affiliate users and customers. 

| UserRepositoryIntegrationTest | DAO (Repository) | User table repository test 

| BillingServiceStoreEmployeeIntegrationTest | DAO (Repository) | Billing service tests for Store Employee use case

| BillingServiceAffiliateUserIntegrationTest | DAO (Repository) | Billing service tests for Affiliate use case

| BillingServiceOldUserIntegrationTest | DAO (Repository) | Billing service tests for customer registered before 2 years use case

## API Testing
API testing can be carried out using postman and postman runner functionality. Added the postman collection for all user's on github
[postman collection](https://github.com/ktool/retailstore/blob/master/run/Online%20Retail%20App.postman_collection.json).

Run the project and Just import the collection to Postman !!!!!!!

## Deployment

Create a build file (WAR) and deploy on Jetty or Tomcat server webapp.
```
mvn clean install
```
Copy *retailstore-0.0.1.war* file from /target directory and paste it to respective webroot directory of tomcat or jetty container. Since we use h2 database no additional configurations required.

## Authors

* **Rahul Syal**
