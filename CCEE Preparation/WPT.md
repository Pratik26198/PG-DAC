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
```
# Introduction to HTML5

## What is HTML5?
HTML5 is the latest version of the HyperText Markup Language, designed to structure and present content on the web. It introduces new features to support multimedia, semantic elements, APIs, and enhanced performance. HTML5 is widely used for building responsive and interactive web applications.

### Key Features of HTML5:
1. **Semantic Elements**: New tags like `<header>`, `<footer>`, `<article>`, and `<section>` enhance readability and structure.
2. **Multimedia Support**: Native support for audio and video using `<audio>` and `<video>` tags.
3. **Canvas and SVG**: Allows dynamic graphics rendering without plugins.
4. **Geolocation API**: Enables location-based services.
5. **Responsive Design**: Works seamlessly with CSS3 for adaptive layouts.
6. **Offline Storage**: Provides local storage via `localStorage` and `sessionStorage`.
7. **Form Enhancements**: New input types like `email`, `date`, and `range`.

---

# Introduction to Basic HTML Tags

HTML tags form the building blocks of a webpage. They are enclosed in angle brackets (`< >`) and usually have an opening and closing tag.

---

## Common HTML Tags and Their Uses

### 1. **Alignment**
Align content using CSS, but HTML provides basic tags:
- `<center>` (deprecated in HTML5; use CSS instead):
  ```html
  <center>This text is centered</center>
  ```

### 2. **Headings**
HTML provides six levels of headings:
- Syntax:
  ```html
  <h1>Main Heading</h1>
  <h2>Subheading</h2>
  <h3>Smaller Heading</h3>
  ```
- Output:
  - `<h1>` is the largest.
  - `<h6>` is the smallest.

### 3. **Anchor**
Creates hyperlinks to other pages or resources:
- Syntax:
  ```html
  <a href="https://www.example.com">Visit Example</a>
  ```
- Attributes:
  - `href`: The URL to navigate.
  - `target="_blank"`: Opens the link in a new tab.

### 4. **Paragraph**
Defines a block of text:
- Syntax:
  ```html
  <p>This is a paragraph of text.</p>
  ```

### 5. **Image**
Displays images on a webpage:
- Syntax:
  ```html
  <img src="image.jpg" alt="Description" width="300" height="200">
  ```
- Attributes:
  - `src`: Path to the image file.
  - `alt`: Alternative text for accessibility.
  - `width` and `height`: Dimensions of the image.

### 6. **Lists**
HTML supports ordered and unordered lists:
- **Unordered List**:
  ```html
  <ul>
    <li>Item 1</li>
    <li>Item 2</li>
  </ul>
  ```
- **Ordered List**:
  ```html
  <ol>
    <li>First Item</li>
    <li>Second Item</li>
  </ol>
  ```
- Output:
  - `<ul>`: Bulleted list.
  - `<ol>`: Numbered list.

### 7. **Tables**
Defines tabular data:
- Syntax:
  ```html
  <table border="1">
    <tr>
      <th>Header 1</th>
      <th>Header 2</th>
    </tr>
    <tr>
      <td>Data 1</td>
      <td>Data 2</td>
    </tr>
  </table>
  ```
- Attributes:
  - `border`: Adds a border around the table.

### 8. **iFrames**
Embeds another HTML document within the current page:
- Syntax:
  ```html
  <iframe src="https://www.example.com" width="600" height="400"></iframe>
  ```
- Attributes:
  - `src`: URL of the embedded document.
  - `width` and `height`: Size of the frame.

---

# Example: Combining HTML Tags
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>HTML5 Introduction</title>
</head>
<body>
  <h1>Welcome to HTML5</h1>
  <p>This is an example of basic HTML tags.</p>
  
  <h2>Example List</h2>
  <ul>
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
  </ul>

  <h2>Sample Table</h2>
  <table border="1">
    <tr>
      <th>Language</th>
      <th>Popularity</th>
    </tr>
    <tr>
      <td>HTML</td>
      <td>High</td>
    </tr>
    <tr>
      <td>CSS</td>
      <td>High</td>
    </tr>
  </table>

  <h2>Embedded Content</h2>
  <iframe src="https://www.example.com" width="600" height="400"></iframe>

  <h2>Image Example</h2>
  <img src="image.jpg" alt="Example Image" width="300">

  <h2>Anchor Example</h2>
  <a href="https://www.example.com" target="_blank">Visit Example</a>
</body>
</html>
```

---

# Diagram: Basic HTML Structure
```plaintext
<!DOCTYPE html>
<html>
  <head>
    <title>Page Title</title>  <!-- Meta information -->
  </head>
  <body>
    <!-- Content -->
  </body>
</html>
```
# HTML5

## New Features in HTML5
HTML5 introduces numerous enhancements that improve web development capabilities, interactivity, and accessibility. Key features include:

1. **Improved Semantics**: Tags like `<header>`, `<footer>`, `<article>`, and `<section>` provide meaningful content structure.
2. **Enhanced Multimedia**: Native support for audio and video playback without plugins.
3. **Graphics and Effects**: The `<canvas>` element and SVG integration enable dynamic graphics rendering.
4. **APIs and Connectivity**:
   - Geolocation API
   - Offline storage using `localStorage` and `sessionStorage`
   - Drag-and-drop API.
5. **Performance and Integration**:
   - Reduced reliance on external plugins (e.g., Flash).
   - Improved parsing rules for error handling.

---

## New Elements, Attributes, and Features

### New Elements

| Element       | Description                                                                 |
|---------------|-----------------------------------------------------------------------------|
| `<header>`    | Represents the introductory section of a document or section.              |
| `<footer>`    | Represents the footer section with information like copyright.             |
| `<article>`   | Defines self-contained, independent content.                              |
| `<section>`   | Represents a thematic grouping of content.                                |
| `<nav>`       | Used for navigation links.                                                |
| `<figure>`    | Groups media elements with a caption.                                     |
| `<figcaption>`| Provides a caption for `<figure>`.                                        |
| `<mark>`      | Highlights text.                                                         |
| `<time>`      | Represents date and time.                                                |
| `<progress>`  | Displays progress of a task.                                             |

### New Attributes

| Attribute     | Description                                                                 |
|---------------|-----------------------------------------------------------------------------|
| `placeholder` | Provides placeholder text in inputs.                                       |
| `autofocus`   | Automatically focuses an element.                                         |
| `required`    | Specifies that an input must be filled out before submitting.             |
| `pattern`     | Defines a regular expression for input validation.                        |
| `form`        | Associates the element with a specific form.                              |
| `draggable`   | Specifies whether an element is draggable.                                |

### Link Relations

HTML5 introduces new values for the `rel` attribute in links:

| Relation       | Description                                                               |
|----------------|---------------------------------------------------------------------------|
| `preload`      | Specifies resources to load early.                                        |
| `prefetch`     | Indicates resources to fetch for future use.                              |
| `stylesheet`   | Links to external CSS files.                                             |

### Microdata
Microdata allows embedding structured data into HTML to improve search engine understanding.

Example:
```html
<div itemscope itemtype="https://schema.org/Person">
  <span itemprop="name">Alice</span>
  <span itemprop="jobTitle">Engineer</span>
</div>
```

### ARIA Accessibility
Accessible Rich Internet Applications (ARIA) improve accessibility for users with disabilities.

Example:
```html
<div role="banner">Site Title</div>
<nav role="navigation">
  <ul>
    <li><a href="#">Home</a></li>
    <li><a href="#">About</a></li>
  </ul>
</nav>
```

### Objects and Events
- **New Objects**: `FormData`, `Blob`, and `ArrayBuffer`.
- **New Events**: `oninput`, `oncanplay`, `onplay`, `onpause`.

### Canvas Tag
The `<canvas>` element enables dynamic graphics using JavaScript.

Example:
```html
<canvas id="myCanvas" width="300" height="150"></canvas>
<script>
  const canvas = document.getElementById('myCanvas');
  const ctx = canvas.getContext('2d');
  ctx.fillStyle = 'blue';
  ctx.fillRect(50, 50, 100, 75);
</script>
```

---

## HTML5 Validation
HTML5 enhances form validation with built-in attributes:

| Attribute     | Purpose                                  |
|---------------|------------------------------------------|
| `required`    | Ensures the input field is filled.       |
| `pattern`     | Validates input against a regular expression. |
| `maxlength`   | Limits the length of the input.          |
| `type`        | Validates based on the input type (e.g., email). |

Example:
```html
<form>
  <label for="email">Email:</label>
  <input type="email" id="email" required placeholder="Enter your email">
  <button type="submit">Submit</button>
</form>
```

---

## Audio & Video Support

### Audio Tag
The `<audio>` tag embeds audio files.

Example:
```html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>
```

### Video Tag
The `<video>` tag embeds video files.

Example:
```html
<video controls width="600">
  <source src="video.mp4" type="video/mp4">
  Your browser does not support the video element.
</video>
```

---

## Geo-location Support
The Geolocation API retrieves the user’s location.

Example:
```html
<button onclick="getLocation()">Get Location</button>
<p id="location"></p>

<script>
  function getLocation() {
    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(showPosition);
    } else {
      document.getElementById('location').innerText = "Geolocation not supported.";
    }
  }

  function showPosition(position) {
    document.getElementById('location').innerText = 
      `Latitude: ${position.coords.latitude}, Longitude: ${position.coords.longitude}`;
  }
</script>
```
```

# HTML Forms & Controls

## HTML Forms
HTML forms are used to collect user input and send it to a server for processing. Forms are defined using the `<form>` tag, which can contain various input elements.

### Basic Syntax
```html
<form action="/submit" method="POST">
  <!-- Form Controls Go Here -->
</form>
```

### Common Form Controls

#### 1. **Input**
The `<input>` tag is a versatile element for collecting user input.

| Type           | Description                             | Example                                      |
|----------------|-----------------------------------------|----------------------------------------------|
| `text`         | Single-line text input                 | `<input type="text" name="username">`     |
| `password`     | Masked text input                      | `<input type="password" name="pwd">`     |
| `email`        | Validates email addresses              | `<input type="email" name="email">`      |
| `number`       | Accepts numerical input                | `<input type="number" name="age">`       |
| `date`         | Date picker                            | `<input type="date" name="dob">`         |
| `file`         | Uploads a file                         | `<input type="file" name="profilePic">`  |

#### 2. **Text Area**
The `<textarea>` tag is used for multi-line text input.

```html
<textarea name="message" rows="4" cols="50">Enter your message here...</textarea>
```

#### 3. **Radio Buttons**
Used to select one option from a group.

```html
<label>
  <input type="radio" name="gender" value="male"> Male
</label>
<label>
  <input type="radio" name="gender" value="female"> Female
</label>
```

#### 4. **Checkbox**
Allows multiple selections.

```html
<label>
  <input type="checkbox" name="hobby" value="reading"> Reading
</label>
<label>
  <input type="checkbox" name="hobby" value="sports"> Sports
</label>
```

#### 5. **Dropdown (Select)**
The `<select>` tag creates a dropdown menu.

```html
<select name="country">
  <option value="india">India</option>
  <option value="usa">USA</option>
  <option value="uk">UK</option>
</select>
```

#### 6. **Buttons**

| Button Type | Description                            | Example                                  |
|-------------|----------------------------------------|------------------------------------------|
| `submit`    | Submits the form                      | `<button type="submit">Submit</button>` |
| `reset`     | Resets form fields to their defaults  | `<button type="reset">Reset</button>`   |
| `button`    | General-purpose button                | `<button type="button">Click Me</button>` |

### Example Form
```html
<form action="/submit" method="POST">
  <label for="username">Username:</label>
  <input type="text" id="username" name="username" required>

  <label for="password">Password:</label>
  <input type="password" id="password" name="password" required>

  <label for="gender">Gender:</label>
  <input type="radio" name="gender" value="male"> Male
  <input type="radio" name="gender" value="female"> Female

  <label for="country">Country:</label>
  <select id="country" name="country">
    <option value="india">India</option>
    <option value="usa">USA</option>
    <option value="uk">UK</option>
  </select>

  <button type="submit">Submit</button>
  <button type="reset">Reset</button>
</form>
```

---

# Introduction to Document Object Model (DOM)

## What is the DOM?
The Document Object Model (DOM) is a programming interface for web documents. It represents the structure of a webpage as a tree of objects that can be manipulated using programming languages like JavaScript.

### DOM Tree Structure
The DOM organizes the HTML document into a tree-like structure:

- The document root is `<html>`.
- Each HTML element becomes a node in the tree.
- Text, attributes, and comments are also nodes.

Example Tree:
```plaintext
<html>
 └── <body>
      ├── <h1>
      │    └── "Hello World"
      ├── <p>
      │    └── "This is a paragraph."
      └── <ul>
           ├── <li>Item 1</li>
           └── <li>Item 2</li>
```

### Accessing the DOM
JavaScript can be used to interact with the DOM.

#### Selecting Elements
| Method                     | Description                                      | Example                                   |
|----------------------------|--------------------------------------------------|-------------------------------------------|
| `getElementById()`         | Selects an element by its ID                    | `document.getElementById('id')`          |
| `getElementsByClassName()` | Selects elements by their class name            | `document.getElementsByClassName('class')` |
| `querySelector()`          | Selects the first element that matches a CSS selector | `document.querySelector('.class')`    |
| `querySelectorAll()`       | Selects all elements that match a CSS selector  | `document.querySelectorAll('div')`       |

#### Modifying Elements
```html
<p id="demo">This is a paragraph.</p>
<button onclick="changeText()">Change Text</button>
<script>
  function changeText() {
    document.getElementById('demo').innerHTML = 'Text has been changed!';
  }
</script>
```

#### Adding and Removing Elements
```html
<ul id="list">
  <li>Item 1</li>
</ul>
<button onclick="addItem()">Add Item</button>
<script>
  function addItem() {
    const ul = document.getElementById('list');
    const li = document.createElement('li');
    li.textContent = 'New Item';
    ul.appendChild(li);
  }
</script>
```

### Events in the DOM
Events allow interaction with the DOM, such as clicks, mouse movements, and keypresses.

#### Example: Event Listener
```html
<button id="btn">Click Me</button>
<script>
  document.getElementById('btn').addEventListener('click', function() {
    alert('Button clicked!');
  });
</script>
```

---

The DOM is a powerful model for interacting with web pages, enabling dynamic and interactive user experiences.

