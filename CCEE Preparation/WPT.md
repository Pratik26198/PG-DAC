# Architecture of the Web

## 1. Brief History of the Internet

- **1960s**: The idea of connecting computers emerged. DARPA (Defense Advanced Research Projects Agency) funded ARPANET, the first packet-switching network.
- **1970s**: Introduction of the TCP/IP protocol suite:
  - TCP: Ensures reliable delivery of packets.
  - IP: Handles addressing and routing.
- **1983**: ARPANET adopted TCP/IP, creating the foundation for modern Internet.
- **1989**: Tim Berners-Lee introduced the World Wide Web, combining:
  - **HTML**: Hypertext Markup Language.
  - **HTTP**: Protocol to communicate between browsers and servers.
  - **URLs**: Uniform Resource Locators to identify resources.
- **1990s**: The Internet transitioned from academic research to commercial use, with the release of popular browsers like Mosaic and Netscape Navigator.

---

## 2. How Does the Internet Work?

The Internet connects billions of devices worldwide through a complex infrastructure. Here's how it works:

### 2.1. **Key Components**:
- **Devices**: Computers, smartphones, servers.
- **Routers**: Direct data packets between networks.
- **Switches**: Connect devices within a local network.
- **Cables and Satellites**: Provide physical connectivity.

### 2.2. **Data Transmission**:
1. Data is broken into small units called **packets**.
2. Each packet contains:
   - Source and destination IP addresses.
   - Data payload.
   - Sequence number (to reassemble data).
3. Packets travel through various routers to reach their destination, where they are reassembled.

### 2.3. **Client-Server Communication**:
1. The **client** (e.g., a browser) sends a request to the server using protocols like HTTP.
2. The **server** processes the request and responds with the requested data (e.g., a webpage).

### 2.4. **Routing**:
- Packets are routed based on their destination IP address.
- Routers use algorithms to determine the fastest path to the destination.

---

## 3. Internet Protocol

### 3.1. **IP (Internet Protocol)**:
- IP provides addressing for devices on a network.
- Versions:
  - **IPv4**: 32-bit address (e.g., `192.168.1.1`), supports ~4.3 billion devices.
  - **IPv6**: 128-bit address (e.g., `2001:db8::ff00:42:8329`), supports a virtually unlimited number of devices.

### 3.2. **HTTP (Hypertext Transfer Protocol)**:
- A protocol that allows clients to fetch resources from servers.
- Operates on a request-response model:
  1. Client sends an HTTP request.
  2. Server processes the request and returns an HTTP response.

---

## 4. Domain Names and DNS Servers

### 4.1. **Domain Names**:
- Human-readable addresses like `www.example.com`.
- Map to IP addresses, making it easier for users to access websites.

### 4.2. **DNS (Domain Name System)**:
- A hierarchical system that translates domain names into IP addresses.
- Structure:
  - **Root Servers**: Handle queries for top-level domains (TLDs).
  - **TLDs**: `.com`, `.org`, `.net`.
  - **Second-Level Domains**: `example.com`.
  - **Authoritative DNS Servers**: Provide the IP address for specific domains.

### DNS Query Flow:
1. User enters a domain name.
2. Browser queries the **Recursive DNS Server**.
3. The server checks:
   - Cache for previous results.
   - If not found, queries root servers and authoritative servers.
4. Returns the IP address to the client.

---

## 5. HTTP Protocols

### 5.1. **Difference Between HTTP/1.0, HTTP/1.1, and HTTP/2.0**
| Feature             | HTTP/1.0              | HTTP/1.1                        | HTTP/2.0                  |
|---------------------|-----------------------|----------------------------------|---------------------------|
| **Connection**      | One request per connection | Persistent connections allowed   | Multiplexing multiple requests on a single connection |
| **Compression**     | None                  | None                             | Header compression using HPACK |
| **Parallelism**     | None                  | Limited                          | Full parallelism          |
| **Performance**     | Basic                | Improved with pipelining         | High due to binary framing |
| **TLS Support**     | N/A                  | Optional                         | Native                   |

### 5.2. **HTTP Methods**
- **GET**: Retrieve data from the server.
- **POST**: Submit data to the server for processing.
- **PUT**: Update or replace a resource.
- **DELETE**: Remove a resource.
- **HEAD**: Fetch only headers, not the body.
- **OPTIONS**: Describe communication options for a resource.

### 5.3. **HTTP Status Codes**
| Code   | Description                                |
|--------|--------------------------------------------|
| 1xx    | Informational (`100 Continue`)            |
| 2xx    | Success (`200 OK`, `201 Created`)         |
| 3xx    | Redirection (`301 Moved Permanently`)     |
| 4xx    | Client Errors (`404 Not Found`)           |
| 5xx    | Server Errors (`500 Internal Server Error`)|

### 5.4. **Stateless Nature of HTTP**
- HTTP is stateless, meaning each request is independent.
- Sessions are maintained using:
  - **Cookies**: Small data stored on the client.
  - **URL Parameters**: Data passed in the URL.
  - **Server-Side Sessions**: Data stored on the server, linked via session IDs.

### 5.5. **HTTPS (HTTP Secure)**
- HTTPS adds encryption to HTTP using SSL/TLS.
- Benefits:
  - **Data Integrity**: Ensures data is not tampered with.
  - **Authentication**: Verifies the server's identity.
  - **Confidentiality**: Encrypts the data in transit.

---

## 6. Architecture of the Web

### 6.1. **Client-Server Model**
- **Client**: Initiates requests (e.g., browsers).
- **Server**: Responds to client requests (e.g., web servers).

### 6.2. **Three-Layer Architecture**
1. **Presentation Layer**:
   - User interface (HTML, CSS, JavaScript).
2. **Logic Layer**:
   - Handles application logic (e.g., server-side code).
3. **Data Layer**:
   - Manages databases and storage.

---

## 7. Web Servers

### 7.1. **IIS (Internet Information Services)**:
- Developed by Microsoft.
- Supports ASP.NET applications.
- Features:
  - Integrated Windows authentication.
  - Scalability and performance tuning.

### 7.2. **Apache HTTP Server**:
- Open-source and cross-platform.
- Supports multiple programming languages (PHP, Python).
- Features:
  - Modular design for extensibility.
  - Compatibility with Unix/Linux and Windows.

---

## 8. Flowchart: How the Web Works
```plaintext
Client (Browser)
    ↓
DNS Lookup (Domain to IP)
    ↓
HTTP Request (via IP)
    ↓
Web Server (e.g., Apache/IIS)
    ↓
Database (if needed)
    ↓
HTTP Response
    ↓
Rendered Web Page

