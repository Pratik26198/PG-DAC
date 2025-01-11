# JDBC & Transaction Management

## Introduction to JDBC API

**Java Database Connectivity (JDBC)** is a standard Java API for interacting with relational databases. It allows developers to execute SQL statements, retrieve results, and manage database connections.

### Key Features:
- Platform-independent connectivity.
- Supports CRUD (Create, Read, Update, Delete) operations.
- Facilitates transaction management and batch processing.
- Extensible through various JDBC drivers.

### JDBC Workflow:
1. Load the JDBC Driver.
2. Establish a connection to the database.
3. Create and execute SQL queries.
4. Process the results.
5. Close the resources.

---

## JDBC Architecture

JDBC architecture consists of two layers:

1. **JDBC API Layer:**
   - Provides methods and classes for interacting with databases.
2. **JDBC Driver Layer:**
   - Translates JDBC calls into vendor-specific database calls.

### Diagram:

```plaintext
Application
    |
    v
JDBC API
    |
    v
JDBC Driver Manager
    |
    v
Database-Specific Driver
    |
    v
Database
```

---

## JDBC Drivers

JDBC drivers act as an interface between the Java application and the database.

### Types of Drivers:

1. **Type 1: JDBC-ODBC Bridge Driver**
   - Uses ODBC drivers for database communication.
   - Pros: Easy to use.
   - Cons: Slower and platform-dependent.

2. **Type 2: Native-API Driver**
   - Uses native libraries of the database.
   - Pros: Faster than Type 1.
   - Cons: Platform-dependent.

3. **Type 3: Network Protocol Driver**
   - Communicates with middleware for database access.
   - Pros: Platform-independent, suitable for multi-tier applications.
   - Cons: Middleware required.

4. **Type 4: Thin Driver**
   - Directly converts JDBC calls to database-specific protocol.
   - Pros: Fast, platform-independent.
   - Cons: Requires a separate driver for each database.

### Table Comparison:

| Type    | Speed     | Platform Dependency | Middleware Required |
|---------|-----------|---------------------|---------------------|
| Type 1  | Slow      | Yes                 | No                  |
| Type 2  | Moderate  | Yes                 | No                  |
| Type 3  | Moderate  | No                  | Yes                 |
| Type 4  | Fast      | No                  | No                  |

---

## JDBC Classes & Interfaces

### Key Components:

1. **Driver**
   - Loads database-specific driver.
   - Example: `DriverManager.registerDriver(new MySQLDriver());`

2. **Connection**
   - Represents a connection to the database.
   - Example:

```java
Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/mydb", "user", "password");
```

3. **Statement**
   - Executes SQL queries.
   - Example:

```java
Statement stmt = conn.createStatement();
ResultSet rs = stmt.executeQuery("SELECT * FROM employees");
```

4. **PreparedStatement**
   - Precompiled SQL statements to prevent SQL injection.
   - Example:

```java
PreparedStatement pstmt = conn.prepareStatement("SELECT * FROM employees WHERE id = ?");
pstmt.setInt(1, 101);
ResultSet rs = pstmt.executeQuery();
```

5. **ResultSet**
   - Retrieves query results.
   - Example:

```java
while (rs.next()) {
    System.out.println("Name: " + rs.getString("name"));
}
```

---

## Stored Procedures and Functions Invocation

Stored procedures and functions are precompiled SQL statements stored in the database. JDBC allows invoking them using the `CallableStatement` interface.

### Example:

#### Stored Procedure (MySQL):
```sql
DELIMITER //
CREATE PROCEDURE getEmployeeName(IN empId INT, OUT empName VARCHAR(50))
BEGIN
    SELECT name INTO empName FROM employees WHERE id = empId;
END //
DELIMITER ;
```

#### Java Code:
```java
CallableStatement cstmt = conn.prepareCall("{CALL getEmployeeName(?, ?)}");
cstmt.setInt(1, 101);
cstmt.registerOutParameter(2, Types.VARCHAR);
cstmt.execute();
System.out.println("Employee Name: " + cstmt.getString(2));
```

---
![jdbc overview](https://github.com/user-attachments/assets/cf445ea6-f2b1-492e-8c07-6a5d8c5d8e6c)

## SQL Injection Overview and Prevention

### SQL Injection:
A security vulnerability where attackers inject malicious SQL queries to manipulate the database.

### Example:
#### Vulnerable Code:
```java
String query = "SELECT * FROM users WHERE username = '" + userInput + "'";
Statement stmt = conn.createStatement();
ResultSet rs = stmt.executeQuery(query);
```

#### Malicious Input:
```plaintext
' OR '1'='1
```

### Prevention:
1. Use `PreparedStatement`:
```java
PreparedStatement pstmt = conn.prepareStatement("SELECT * FROM users WHERE username = ?");
pstmt.setString(1, userInput);
ResultSet rs = pstmt.executeQuery();
```

2. Validate user inputs.
3. Use stored procedures.
4. Implement ORM frameworks (e.g., Hibernate).

---

## Design Pattern: Data Access Object (DAO) Pattern

The DAO pattern abstracts and encapsulates data access logic, separating it from business logic.

### Structure:

```plaintext
Controller -> Service -> DAO -> Database
```

### Example:

#### User.java (POJO):
```java
public class User {
    private int id;
    private String name;

    // Getters and Setters
}
```

#### UserDAO Interface:
```java
public interface UserDAO {
    User getUserById(int id);
    void saveUser(User user);
}
```

#### UserDAOImpl:
```java
public class UserDAOImpl implements UserDAO {
    private Connection conn;

    public UserDAOImpl(Connection conn) {
        this.conn = conn;
    }

    @Override
    public User getUserById(int id) throws SQLException {
        String query = "SELECT * FROM users WHERE id = ?";
        PreparedStatement pstmt = conn.prepareStatement(query);
        pstmt.setInt(1, id);
        ResultSet rs = pstmt.executeQuery();
        if (rs.next()) {
            User user = new User();
            user.setId(rs.getInt("id"));
            user.setName(rs.getString("name"));
            return user;
        }
        return null;
    }

    @Override
    public void saveUser(User user) throws SQLException {
        String query = "INSERT INTO users (name) VALUES (?)";
        PreparedStatement pstmt = conn.prepareStatement(query);
        pstmt.setString(1, user.getName());
        pstmt.executeUpdate();
    }
}
```

### Benefits:
- Simplifies data access logic.
- Promotes separation of concerns.
- Easy to test and maintain.

```
```


# J2EE Overview

Java 2 Platform, Enterprise Edition (J2EE), now known as Java EE (Enterprise Edition), is a set of specifications and technologies that enable the development of enterprise-level applications in Java. It provides a platform for building and deploying distributed, multi-tiered, and transactional web-based applications.

### Key Components of J2EE:
1. **Servlets**: A Java class used to extend the capabilities of servers hosting applications accessed by users.
2. **JSP (JavaServer Pages)**: A technology used for creating dynamic web pages with Java.
3. **EJB (Enterprise JavaBeans)**: A server-side component used for business logic.
4. **JDBC (Java Database Connectivity)**: A Java API that allows interaction with databases.
5. **JMS (Java Message Service)**: A messaging standard for sending messages between applications.
6. **JTA (Java Transaction API)**: A standard interface for managing transactions.

J2EE applications typically consist of components like web components (Servlets and JSPs) and enterprise components (EJBs, JCA, etc.).

---

## J2EE Container

A J2EE container is a runtime environment for J2EE components, managing the life cycle, security, transactions, and many other services of the components within an application.

### Types of Containers:
1. **Web Container**: Manages the execution of web components such as Servlets and JSPs.
2. **EJB Container**: Manages the execution of enterprise beans, including session beans, entity beans, and message-driven beans.
3. **Application Client Container**: Manages the execution of Java application clients that interact with the enterprise server.

### Responsibilities of the Container:
- **Component Management**: Creating, loading, and managing component lifecycle.
- **Security Management**: Managing access control and user authentication.
- **Transaction Management**: Coordinating transaction activities within components.
- **Resource Management**: Managing external resources like databases and messaging systems.

**Diagram**:
```
+---------------------------------------+
|            J2EE Application          |
|                                       |
|   +-----------+    +---------------+  |
|   | Web       |    | EJB           |  |
|   | Container |    | Container     |  |
|   +-----------+    +---------------+  |
|          |               |           |
|   +------------------+    |           |
|   | Servlet/JSP      |    |           |
|   +------------------+    |           |
|                          |           |
|   +------------------+    |           |
|   | Enterprise Bean  |    |           |
|   +------------------+    |           |
+---------------------------------------+
```

---

## Packaging Web Applications

Web applications in J2EE are packaged into **WAR (Web Archive)** files. A WAR file is a compressed archive that contains all the files required for a web application, such as HTML, JSP, Servlets, and other resources.

### Structure of a WAR File:
```
my-web-app.war
├── WEB-INF/
│   ├── classes/                # Compiled Java classes
│   ├── lib/                    # Libraries (JAR files)
│   ├── web.xml                 # Deployment descriptor (web.xml)
│   └── tlds/                   # Tag Library Descriptors (for custom tags)
├── index.html                  # Static HTML page
└── images/                     # Images and other static resources
```

- **WEB-INF/web.xml**: The deployment descriptor for a web application. It configures the servlets, servlet mappings, and other resources for the application.

---

## J2EE Compliant Web Application

A J2EE-compliant web application adheres to the Java EE specifications and can run on any application server that supports J2EE. This includes having the proper directory structure, deployment descriptors, and required libraries.

### Characteristics:
- It must have a `web.xml` descriptor under the `WEB-INF` directory.
- Should be packaged as a WAR file.
- Can use J2EE technologies like Servlets, JSP, EJBs, JDBC, and more.
- Must conform to security, transaction, and session management protocols defined by Java EE.

---

## Deployment Tools

Deployment tools are used to deploy J2EE applications to an application server or a cloud environment.

### Common Tools:
- **Ant**: A build tool used for automating the deployment process of web applications.
- **Maven**: A build and dependency management tool that can also deploy applications.
- **EJB Deployment Tool**: A tool to deploy EJB components to the EJB container.
- **J2EE Deployment Descriptor**: The `web.xml` (for web applications) and `ejb-jar.xml` (for EJBs) files provide the necessary configuration for the deployment.

### Deployment Process:
1. **Compile** the source code.
2. **Package** the application into a WAR or EAR file.
3. **Deploy** the packaged file to the application server (e.g., JBoss, GlassFish).
4. **Start** the application using the deployment tools or application server console.

---

## Web Application Life Cycle

The web application life cycle defines the phases that a web application goes through during its existence. It involves the management of requests, sessions, and responses.

### Phases:
1. **Initialization**: When the servlet is loaded into memory by the web container.
2. **Request Handling**: The servlet or JSP processes client requests.
3. **Response Generation**: The servlet or JSP generates the response (usually HTML).
4. **Destruction**: When the servlet is unloaded and the container shuts down.

### Flowchart:

```
+------------------+      +--------------------+      +-------------------+
|    Initialization| ---> |  Request Handling   | ---> |  Response Generation|
+------------------+      +--------------------+      +-------------------+
                                      |
                                      v
                                +------------------+
                                |    Destruction   |
                                +------------------+
```

---

## Deploying Web Applications

Web applications are deployed on J2EE-compliant servers like Tomcat, JBoss, or GlassFish. The deployment process typically involves:

1. **Create a WAR file**: Package the application.
2. **Upload the WAR file**: Upload to the application server's web deployment directory.
3. **Configure the server**: Ensure the server is configured for the correct deployment, including context path and resource mapping.
4. **Start the application**: Start the server, and the application will be available for users.

### Deployment Descriptor (`web.xml`):
```xml
<web-app>
    <servlet>
        <servlet-name>helloServlet</servlet-name>
        <servlet-class>com.example.HelloServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>helloServlet</servlet-name>
        <url-pattern>/hello</url-pattern>
    </servlet-mapping>
</web-app>
```

---

## Web Services Support

J2EE provides support for building and deploying web services, enabling communication between distributed applications over the internet. Web services in J2EE are typically implemented using SOAP or REST protocols.

### SOAP-based Web Services:
- SOAP (Simple Object Access Protocol) is a protocol for exchanging XML-based messages.
- JAX-RPC (Java API for XML-Based RPC) and JAX-WS (Java API for Web Services) are used for implementing SOAP services.

### RESTful Web Services:
- REST (Representational State Transfer) is an architectural style based on HTTP.
- JAX-RS (Java API for RESTful Web Services) is used to develop RESTful web services.

### Web Service Deployment:
1. **Create a WSDL (Web Service Definition Language)** document for SOAP.
2. **Publish the service** on the application server.
3. **Consume the service** from a client application.

### Diagram:
```
+-------------------------+
|    Web Service Consumer |
| (Client Application)    |
+-------------------------+
            |
            v
+-------------------------+
|   Web Service Endpoint  |
| (Server-Side Service)   |
+-------------------------+
            |
            v
+-------------------------+
|    SOAP or REST API     |
| (Communication Layer)   |
+-------------------------+
```

