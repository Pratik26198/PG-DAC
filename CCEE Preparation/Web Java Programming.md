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



# Servlets: A Comprehensive Guide

## 1. Servlets: Dynamic Content Generation
Servlets are Java programs that run on a server and generate dynamic content in response to client requests, typically through HTTP. They are a crucial part of Java EE for building web applications.

### Features of Servlets:
- **Platform Independent**: Written in Java, making them portable across platforms.
- **Dynamic Content Generation**: Handles user input to produce dynamic responses like HTML, JSON, or XML.
- **Efficient and Scalable**: Eliminates the overhead of process creation, as they operate within a single JVM.

### Basic Example:
```java
import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

public class HelloWorldServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<h1>Hello, World!</h1>");
    }
}
```

### Flowchart:
1. **Request**: Client sends an HTTP request.
2. **Servlet Container**: Passes the request to the servlet.
3. **Processing**: Servlet processes the request and generates a response.
4. **Response**: Sent back to the client.

---

## 2. Advantages of Servlets over CGI
| Feature                 | Servlets                                   | CGI (Common Gateway Interface)                  |
|-------------------------|--------------------------------------------|------------------------------------------------|
| **Performance**         | High, as servlets run in the JVM and reuse threads. | Low, as each request spawns a new process.     |
| **Scalability**         | Excellent, as they handle multiple requests in threads. | Poor, limited by process creation overhead.    |
| **Portability**         | Platform-independent (Java).              | Platform-dependent (based on language used).   |
| **Security**            | Integrated with Java security APIs.       | Limited security.                              |
| **Maintenance**         | Easier with centralized Java code.        | Harder due to script-based implementation.     |

---

## 3. Servlet Life Cycle
The servlet lifecycle is defined by the **javax.servlet.Servlet** interface.

### Stages:
1. **Loading and Instantiation**:
   - Servlet class is loaded into the JVM by the servlet container.
   - A single instance of the servlet is created.

2. **Initialization (`init` method)**:
   - Invoked once after instantiation.
   - Used for initialization code, such as setting up resources.
   ```java
   public void init(ServletConfig config) throws ServletException {
       super.init(config);
   }
   ```

3. **Request Handling (`service` method)**:
   - Handles client requests by calling `doGet`, `doPost`, etc.
   ```java
   public void service(ServletRequest req, ServletResponse res) throws ServletException, IOException {
       // Dynamic content generation logic
   }
   ```

4. **Destruction (`destroy` method)**:
   - Cleans up resources before servlet is destroyed.
   ```java
   public void destroy() {
       // Cleanup logic
   }
   ```

### Diagram:
```
[Loading] --> [Initialization (init)] --> [Request Handling (service)] --> [Destruction (destroy)]
```

---

## 4. Servlet API & Deployment
Servlets rely on the **Java Servlet API** provided by `javax.servlet` and `javax.servlet.http` packages.

### Deployment:
1. **Directory Structure**:
   ```
   webapp/
   ├── WEB-INF/
   │   ├── web.xml
   │   └── classes/
   │       └── HelloWorldServlet.class
   └── index.html
   ```

2. **web.xml Configuration**:
   ```xml
   <web-app>
       <servlet>
           <servlet-name>HelloWorldServlet</servlet-name>
           <servlet-class>HelloWorldServlet</servlet-class>
       </servlet>
       <servlet-mapping>
           <servlet-name>HelloWorldServlet</servlet-name>
           <url-pattern>/hello</url-pattern>
       </servlet-mapping>
   </web-app>
   ```

---

## 5. Servlet Annotations
Annotations simplify servlet deployment by eliminating the need for `web.xml`.

### Example:
```java
import javax.servlet.annotation.WebServlet;

@WebServlet("/hello")
public class HelloWorldServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.getWriter().println("Hello, World!");
    }
}
```

---

## 6. The Servlet Interface
The **Servlet** interface defines the lifecycle methods:
- `init()`
- `service()`
- `destroy()`
- `getServletConfig()`
- `getServletInfo()`

---

## 7. The HttpServlet, HttpServletRequest, HttpServletResponse
### `HttpServlet`:
A subclass of `GenericServlet` that simplifies HTTP request handling.

### `HttpServletRequest`:
Encapsulates the client request. Useful methods:
- `getParameter(String name)`
- `getSession()`

### `HttpServletResponse`:
Encapsulates the server response. Useful methods:
- `setContentType(String type)`
- `getWriter()`

---

## 8. Exception Handling
### Types of Exceptions:
1. **ServletException**: General exceptions in servlets.
2. **IOException**: Input/output-related issues.

### Example:
```java
try {
    // Code
} catch (IOException e) {
    throw new ServletException("Error processing request", e);
}
```

### Error Page Configuration in `web.xml`:
```xml
<error-page>
    <error-code>404</error-code>
    <location>/error.jsp</location>
</error-page>
```

---

## 9. Servlet, DAO, POJO DB Layers
### Architecture:
1. **Servlet**: Handles HTTP requests and responses.
2. **DAO (Data Access Object)**: Encapsulates database operations.
3. **POJO (Plain Old Java Object)**: Represents data as objects.

### Example:
#### POJO:
```java
public class User {
    private int id;
    private String name;
    private String email;
    // Getters and Setters
}
```

#### DAO:
```java
public class UserDAO {
    public User getUserById(int id) {
        // Database code
        return user;
    }
}
```

#### Servlet:
```java
@WebServlet("/user")
public class UserServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        UserDAO dao = new UserDAO();
        User user = dao.getUserById(1);
        response.getWriter().println("User: " + user.getName());
    }
}
```

---

# Session

## What is a Session?
A **session** represents a single interaction between a client and a server over a period of time. It helps maintain state information for a user across multiple HTTP requests, as HTTP is inherently stateless. Sessions are widely used in web applications to track user activities, such as login status, shopping cart contents, or preferences.

### Characteristics:
- Temporary: A session exists for a specific duration.
- User-specific: Each user has a unique session.
- Server-side: Most session data is stored on the server, ensuring better security.

### Session Lifecycle:
1. **Creation:** A session is created when a user accesses a web application for the first time.
2. **Usage:** Data is stored in the session for subsequent requests.
3. **Invalidation:** The session ends due to timeout or manual invalidation.

### Common Use Cases:
- Storing user login credentials.
- Keeping track of shopping cart items.
- Retaining user preferences.

---

# Session Management

## What is Session Management?
Session management refers to techniques used to maintain the state of a user across multiple HTTP requests. It ensures continuity of user interaction by associating data (like authentication information) with the user.

### Techniques for Session Management:
1. **Cookies:**
   - Stores session data on the client-side as key-value pairs.
   - Limited storage (typically 4 KB per cookie).
2. **URL Rewriting:**
   - Appends a session ID to the URL.
   - Example: `http://example.com;jsessionid=12345`
3. **Hidden Fields:**
   - Embeds session data in hidden form fields within web pages.
4. **HttpSession API (Java-specific):**
   - Stores session data on the server-side.

---

# Session Tracking

Session tracking is the process of identifying and tracking a user’s interaction with a web application. It ensures that the server recognizes subsequent requests from the same client.

## Techniques for Session Tracking:

### 1. Using Cookies
- **Definition:** Cookies are small text files stored on the client’s browser.
- **Working:**
  1. Server sends a `Set-Cookie` header to the browser.
  2. Browser stores the cookie and sends it back with each request using the `Cookie` header.

#### Example Code:
```java
// Setting a cookie
Cookie userCookie = new Cookie("username", "JohnDoe");
userCookie.setMaxAge(60 * 60); // 1 hour
response.addCookie(userCookie);

// Reading a cookie
Cookie[] cookies = request.getCookies();
if (cookies != null) {
    for (Cookie cookie : cookies) {
        if (cookie.getName().equals("username")) {
            String username = cookie.getValue();
        }
    }
}
```

#### Advantages:
- Easy to implement.
- No server storage required.

#### Disadvantages:
- Limited storage size.
- Can be disabled by users.
- Security risks if data isn’t encrypted.

### 2. Using HttpSession
- **Definition:** The `HttpSession` interface provides a way to store session data on the server.
- **Working:**
  1. The server creates a unique `JSESSIONID` for each session.
  2. This ID is sent to the client via cookies or URL rewriting.
  3. Session data is stored on the server and accessed using the session ID.

#### Example Code:
```java
// Creating a session and adding attributes
HttpSession session = request.getSession();
session.setAttribute("username", "JohnDoe");

// Retrieving session data
String username = (String) session.getAttribute("username");

// Invalidating a session
session.invalidate();
```

#### Advantages:
- Data stored securely on the server.
- Handles session timeout automatically (### 30 min by default).

#### Disadvantages:
- Increases server memory usage.
- Session replication is needed in a clustered environment.

---

# Request Dispatcher

## What is a Request Dispatcher?
The `RequestDispatcher` interface in Java is used to forward a request from one resource (such as a servlet) to another resource (servlet, JSP, or HTML file) within the same web application.

### Methods of RequestDispatcher:
1. **`forward()`**: Forwards the request and response to another resource on the server.
2. **`include()`**: Includes the content of another resource in the response.

#### Example Code:
```java
// Forwarding a request
RequestDispatcher rd = request.getRequestDispatcher("welcome.jsp");
rd.forward(request, response);

// Including a resource
RequestDispatcher rd = request.getRequestDispatcher("header.jsp");
rd.include(request, response);
```

### Forward vs Include:
| Feature          | Forward                                   | Include                                    |
|------------------|------------------------------------------|-------------------------------------------|
| Purpose          | Transfers control to another resource    | Embeds content of another resource        |
| URL Changes      | No                                       | No                                        |
| Execution Flow   | Stops after forwarding                   | Continues after including                 |

---

# Page Navigation

Page navigation refers to guiding users between different web pages in a web application. It is commonly achieved using:
1. **Hyperlinks:** Static navigation using `<a>` tags.
2. **Form Submissions:** Dynamic navigation using `<form>` elements.
3. **Request Dispatcher:** Server-side navigation using servlets.

#### Example of Hyperlink:
```html
<a href="products.jsp">View Products</a>
```

#### Example of Form Submission:
```html
<form action="LoginServlet" method="POST">
    <input type="text" name="username" />
    <button type="submit">Login</button>
</form>
```

---

# Case Study: Servlet-Based Application

## Use Case: User Authentication System

### Requirements:
1. A login page for user authentication.
2. Session management to track user login.
3. Logout functionality.

### Folder Structure:
```
web-app/
├── webapp/
│   ├── index.html          # Login page
│   ├── dashboard.jsp       # User dashboard
│   └── logout.jsp          # Logout page
├── src/
│   ├── LoginServlet.java   # Handles login requests
│   └── LogoutServlet.java  # Handles logout requests
├── web.xml                 # Servlet mappings
```

### Code Implementation:

#### 1. `index.html`
```html
<!DOCTYPE html>
<html>
<head>
    <title>Login</title>
</head>
<body>
    <form action="LoginServlet" method="POST">
        <label>Username:</label>
        <input type="text" name="username" required />
        <label>Password:</label>
        <input type="password" name="password" required />
        <button type="submit">Login</button>
    </form>
</body>
</html>
```

#### 2. `LoginServlet.java`
```java
@WebServlet("/LoginServlet")
public class LoginServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String username = request.getParameter("username");
        String password = request.getParameter("password");

        if ("admin".equals(username) && "password123".equals(password)) {
            HttpSession session = request.getSession();
            session.setAttribute("user", username);
            response.sendRedirect("dashboard.jsp");
        } else {
            response.getWriter().println("Invalid credentials!");
        }
    }
}
```

#### 3. `LogoutServlet.java`
```java
@WebServlet("/LogoutServlet")
public class LogoutServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        HttpSession session = request.getSession();
        session.invalidate();
        response.sendRedirect("index.html");
    }
}
```

#### 4. `dashboard.jsp`
```jsp
<%
    HttpSession session = request.getSession(false);
    if (session == null || session.getAttribute("user") == null) {
        response.sendRedirect("index.html");
    }
%>
<h1>Welcome, <%= session.getAttribute("user") %>!</h1>
<a href="LogoutServlet">Logout</a>
```

---

### Conclusion:
This guide demonstrates the fundamentals of session, session management, session tracking techniques, and request dispatching in Java servlets. By implementing the provided case study, you can create a robust servlet-based application.



