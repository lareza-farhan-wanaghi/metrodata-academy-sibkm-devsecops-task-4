# Metrodata Academy SIBKM DevSecOps Task 4: MySQL Connector

## Objective
- Establish a connection between the Spring Boot application in the Product-Service repository and a MySQL database.
- Create a new branch within the application repository and push the modified changes to the branch.

## Solution

### 1. Project Setup


1. Clone the Repository. Ensure you have the credential ready:
   ```bash
   git clone https://github.com/SIBKM-DevSecOps/product-service.git
   ```
2. Create a new branch.
	```bash
	cd product-service
	git checkout -b lareza-farhan-wanaghi
	```

### 2. Test the Application

1. Edit the `pom.xml` file:
   ```bash
   nano pom.xml
   ```

   Uncomment the MySQL and JPA dependencies to enable them (since the dependencies are previously commented):
   ```xml
   <dependency>
       <groupId>org.springframework.boot</groupId>
       <artifactId>spring-boot-starter-data-jpa</artifactId>
   </dependency>
   <dependency>
       <groupId>com.mysql</groupId>
       <artifactId>mysql-connector-j</artifactId>
       <scope>runtime</scope>
   </dependency>
   ```

3. Run the application:
   ```bash
   bash mvnw spring-boot:run
   ```

   You may encounter an error similar to this:

   <img src="_resources/Screenshot%202023-09-07%20at%2018.45.59.png" width="75%"/>

   This error occurs due to the lack of configurations declared for the database connection.

### 3. Solve the Problem

1. Edit the `application.yaml` file to configure the database connection:
   ```bash
   nano src/main/resources/application.yaml
   ```

   Add the following lines (assuming all provided information is correct):
   ```yaml
   spring:
     datasource:
       url: jdbc:mysql://localhost:3306/product_service
       username: user1
       password: 123456
   ```

### 4. Verify the Solution

1. Run the application:
   ```bash
   bash mvnw spring-boot:run
   ```

   You should see the application running successfully now.

      <img src="_resources/Screenshot%202023-09-07%20at%2018.56.51.png" width="75%"/>

2. Visit the application in your web browser.
   A rendered webpage should appear, indicating that the application is running.

      <img src="_resources/Screenshot%202023-09-07%20at%2018.57.28.png" width="75%"/>
	
### 5. Push the Solution.
1. Push the solution
	```
	git add .
	git commit -m "Adding configurations for etablishing the database connection"
	git push -u origin lareza-farhan-wanaghi
	```