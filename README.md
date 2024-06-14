# RESTful-Web-Services-Complete-Course-java
RESTful-Web-Services-Complete-Course-java
# Topic

# RESTful Web Services - S1

## 1. Designing RESTful Services
- REST and the Rebirth of HTTP
- RESTful Architectural Principles
- The Object Model
- Model the URIs
- Defining the Data Format
- Assigning HTTP Methods

## 2. HTTP Method and URI Matching
- Developing a JAX-RS RESTful Service
- Deploying RESTful Service
- Binding HTTP Methods
- Subresource Locators

## 3. JAX-RS Injection
- @PathParam
- @MatrixParam
- @QueryParam
- @FormParam
- @HeaderParam
- @CookieParam
- Common Functionality

## 4. JAX-RS Content Handlers
- Built-in Content Marshalling - JAXB
- Custom Marshalling

## 5. Response Codes, Complex Responses, and Exception Handling
- Default Response Codes
- Complex Responses
- Exception Handling
	

# RESTful Web Services - S2

## 1. HTTP Content Negotiation
- Conneg Explained
- Language Negotiation
- Encoding Negotiation
- JAX-RS and Conneg
- Leveraging Content Negotiation

## 2. HATEOAS
- HATEOAS and Web Services
- HATEOAS and JAX-RS
- Building Links and Link Headers

## 3. Scaling JAX-RS Applications
- Caching
- Concurrency control

## 4. Deployment and Integration
- Deployment
- Configuration
- Spring Integration

## 5. Securing JAX-RS
- Authentication
- Authorization
- Authentication and Authorization in JAX-RS

## 6. RESTful Java Clients
- java.net.URL
- Apache HttpClient
- RESTEasy Client Proxies

## 7. JAX-RS Implementations
- Jersey
- Apache CXF
- JBoss RESTEasy


### REST (Representational State Transfer)

**REST** is an architectural style for designing networked applications. It relies on a stateless, client-server, cacheable communications protocol -- the HTTP protocol is commonly used for this purpose. RESTful applications use HTTP requests to perform CRUD (Create/Read/Update/Delete) operations on resources, which can be identified using URLs. Here are the key principles of REST:

1. **Statelessness**: Each request from a client to a server must contain all the information needed to understand and process the request. The server cannot store client context between requests.
2. **Client-Server Architecture**: The client and server operate independently, allowing for improved scalability and modularity.
3. **Cacheability**: Responses must define themselves as cacheable or non-cacheable to improve client-side performance.
4. **Uniform Interface**: The principle of having a standardized way of interacting with resources. This typically involves:
   - Resource identification through URLs.
   - Manipulation of resources through representations (usually JSON or XML).
   - Self-descriptive messages.
   - Hypermedia as the engine of application state (HATEOAS).

5. **Layered System**: The architecture can be composed of multiple layers (e.g., security, load-balancing) without the client being aware of these layers.
6. **Code on Demand (optional)**: Servers can extend client functionality by transferring executable code (like JavaScript).

### The Rebirth of HTTP in Java

The "Rebirth of HTTP" in Java often refers to the adoption and enhancement of RESTful services in Java applications. The following aspects highlight this evolution:

1. **Java EE and JAX-RS**:
   - **JAX-RS** (Java API for RESTful Web Services) is a set of APIs to create REST web services in Java. It provides annotations to simplify the development of RESTful services.
   - Annotations like `@Path`, `@GET`, `@POST`, `@PUT`, `@DELETE`, and `@Produces` are used to define endpoints and their behavior.
   
2. **Spring Framework**:
   - **Spring MVC** and **Spring Boot** have significantly simplified the development of RESTful services in Java.
   - Using `@RestController`, `@RequestMapping`, and other annotations, developers can easily create RESTful web services.
   - Spring Boot, in particular, has streamlined the setup and deployment of REST services with minimal configuration.

3. **Improved HTTP Clients**:
   - The introduction of better HTTP clients, such as the `HttpClient` in Java 11, which supports modern features like HTTP/2 and WebSocket.
   - Libraries like Apache HttpClient and OkHttp have also been popular choices for making HTTP requests in Java applications.

4. **Microservices Architecture**:
   - The adoption of microservices architecture has boosted the usage of REST in Java applications.
   - Frameworks like Spring Cloud and technologies like Docker and Kubernetes have made it easier to build, deploy, and manage RESTful microservices.

5. **Enhanced Tooling and Libraries**:
   - Tools like Swagger (OpenAPI) for API documentation and testing have become standard.
   - Libraries for JSON processing (e.g., Jackson, Gson) and XML processing have been crucial in the development of RESTful services.

6. **Reactive Programming**:
   - The shift towards reactive programming (e.g., using Project Reactor and RxJava) has influenced the development of non-blocking REST services.
   - Spring WebFlux, part of Spring 5, supports reactive programming for RESTful web services.

### Conclusion

The adoption and enhancement of REST in Java have marked a significant shift towards more efficient, scalable, and maintainable web services. This "rebirth" has been driven by advancements in frameworks, libraries, and architectural patterns that have made it easier to develop and deploy RESTful services in Java.



# RESTful Architectural Principles

RESTful architectural principles, as defined by Roy Fielding in his doctoral dissertation, are the core guidelines for designing RESTful systems. These principles ensure that web services are scalable, performant, and maintainable. Here’s a detailed overview of each principle:

### 1. Statelessness

- **Definition**: Each request from a client to a server must contain all the information needed to understand and process the request. The server should not store any context about the client’s state between requests.
- **Benefits**:
  - Simplifies the server design since the server does not need to maintain session state.
  - Improves scalability as each request is independent and can be handled by any server in a load-balanced system.

### 2. Client-Server Architecture

- **Definition**: The client and server are separate entities that interact through a uniform interface. Clients are responsible for the user interface and user state, while servers manage the resources and application state.
- **Benefits**:
  - Separation of concerns: Allows the client and server to evolve independently.
  - Improves scalability and manageability by allowing them to focus on their specific responsibilities.

### 3. Cacheability

- **Definition**: Responses must define themselves as cacheable or non-cacheable. If a response is cacheable, clients and intermediaries can reuse the response data for later, equivalent requests.
- **Benefits**:
  - Reduces latency and network load, as repeated requests can be served from the cache.
  - Improves overall application performance.

### 4. Uniform Interface

- **Definition**: A standardized way of communicating between the client and server, simplifying and decoupling the architecture. It includes the following constraints:
  - **Resource Identification**: Resources are identified using URIs.
  - **Manipulation of Resources through Representations**: Clients interact with resources using their representations (e.g., JSON, XML).
  - **Self-descriptive Messages**: Each message includes enough information to describe how to process the message.
  - **HATEOAS (Hypermedia as the Engine of Application State)**: Clients interact with the application entirely through hypermedia provided dynamically by application servers.
- **Benefits**:
  - Simplifies the architecture, making it easier to understand and use.
  - Allows for the evolution of client and server components independently.

### 5. Layered System

- **Definition**: The architecture can be composed of multiple layers, each with its role, such as security, load-balancing, and caching. These layers are transparent to the client.
- **Benefits**:
  - Enhances scalability by allowing load balancing and shared caches.
  - Improves security as each layer can enforce its policies.

### 6. Code on Demand (Optional)

- **Definition**: Servers can temporarily extend or customize the functionality of a client by transferring executable code (e.g., JavaScript).
- **Benefits**:
  - Reduces the complexity of clients by enabling servers to provide additional functionality as needed.
  - Allows for dynamic and flexible client behavior.

### Practical Application of RESTful Principles in Java

- **Frameworks**: Java frameworks like Spring (Spring MVC, Spring Boot) and JAX-RS (Jersey, RESTEasy) are designed to facilitate the creation of RESTful services by adhering to these principles.
- **Annotations**: Annotations like `@RestController`, `@RequestMapping`, `@Path`, and `@GET` help define RESTful endpoints and behaviors in Java applications.
- **Libraries**: JSON processing libraries (Jackson, Gson) and HTTP clients (Apache HttpClient, OkHttp) support the manipulation of resource representations and HTTP communication.

### Conclusion

By adhering to these RESTful principles, developers can create web services that are scalable, reliable, and easy to maintain. These principles ensure a clear separation of concerns, enable independent evolution of client and server, and promote a uniform and stateless interaction model, which are essential for the robust functioning of web services in a distributed environment.



# Object Model in RESTful Web Services

In RESTful web services, the object model refers to how resources are represented and structured within an application. Typically, resources are modeled as Java objects, and these objects are then mapped to JSON or XML representations for communication over HTTP.

## Key Concepts of Object Model in RESTful Web Services

### 1. Resources
- Resources are the key abstraction of information in REST. They are typically modeled as objects in the application.
- Each resource is identified by a unique URI.

### 2. Representations
- Resources are represented in a format like JSON or XML. These representations are the state of the resource at any given time.
- The server sends the resource's representation in response to client requests.

### 3. CRUD Operations
- Resources can be manipulated using standard HTTP methods (GET, POST, PUT, DELETE).

## Example Object Model

Let's consider an example of a RESTful web service for managing a collection of books.

### Define the Resource Model

#### Book
Represents a book resource.

```java
public class Book {
    private Long id;
    private String title;
    private String author;
    private String isbn;
    
    // Getters and Setters
}
```

### Define the REST Controller

Using Spring Boot, you can create a REST controller to handle HTTP requests for the `Book` resource.

```java
@RestController
@RequestMapping("/api/books")
public class BookController {

    private final Map<Long, Book> bookRepository = new ConcurrentHashMap<>();
    private final AtomicLong idCounter = new AtomicLong();

    @GetMapping
    public Collection<Book> getAllBooks() {
        return bookRepository.values();
    }

    @GetMapping("/{id}")
    public ResponseEntity<Book> getBookById(@PathVariable Long id) {
        Book book = bookRepository.get(id);
        if (book != null) {
            return ResponseEntity.ok(book);
        } else {
            return ResponseEntity.notFound().build();
        }
    }

    @PostMapping
    public ResponseEntity<Book> createBook(@RequestBody Book book) {
        long id = idCounter.incrementAndGet();
        book.setId(id);
        bookRepository.put(id, book);
        return ResponseEntity.status(HttpStatus.CREATED).body(book);
    }

    @PutMapping("/{id}")
    public ResponseEntity<Book> updateBook(@PathVariable Long id, @RequestBody Book book) {
        if (!bookRepository.containsKey(id)) {
            return ResponseEntity.notFound().build();
        }
        book.setId(id);
        bookRepository.put(id, book);
        return ResponseEntity.ok(book);
    }

    @DeleteMapping("/{id}")
    public ResponseEntity<Void> deleteBook(@PathVariable Long id) {
        if (bookRepository.remove(id) != null) {
            return ResponseEntity.noContent().build();
        } else {
            return ResponseEntity.notFound().build();
        }
    }
}
```

### Example HTTP Requests and Responses

#### GET /api/books
Retrieve all books.

```json
[
    {
        "id": 1,
        "title": "Effective Java",
        "author": "Joshua Bloch",
        "isbn": "978-0134685991"
    },
    {
        "id": 2,
        "title": "Clean Code",
        "author": "Robert C. Martin",
        "isbn": "978-0132350884"
    }
]
```

#### GET /api/books/1
Retrieve book with ID 1.

```json
{
    "id": 1,
    "title": "Effective Java",
    "author": "Joshua Bloch",
    "isbn": "978-0134685991"
}
```

#### POST /api/books
Create a new book.

```json
{
    "title": "Domain-Driven Design",
    "author": "Eric Evans",
    "isbn": "978-0321125217"
}
```

Response:

```json
{
    "id": 3,
    "title": "Domain-Driven Design",
    "author": "Eric Evans",
    "isbn": "978-0321125217"
}
```

#### PUT /api/books/1
Update book with ID 1.

```json
{
    "title": "Effective Java, 3rd Edition",
    "author": "Joshua Bloch",
    "isbn": "978-0134685991"
}
```

Response:

```json
{
    "id": 1,
    "title": "Effective Java, 3rd Edition",
    "author": "Joshua Bloch",
    "isbn": "978-0134685991"
}
```

#### DELETE /api/books/1
Delete book with ID 1.

Response: `204 No Content`

## Conclusion
The object model in RESTful web services revolves around resources, which are typically represented as Java objects. These objects are then exposed through RESTful endpoints using HTTP methods to perform CRUD operations. In Java, frameworks like Spring Boot and JAX-RS facilitate the creation of RESTful services by providing annotations and tools to map Java objects to JSON or XML representations and handle HTTP requests and responses efficiently.




# Data Formats in RESTful Web Services

In RESTful web services, defining the data format is crucial for consistent and efficient communication between the client and server. Typically, JSON (JavaScript Object Notation) and XML (eXtensible Markup Language) are used as data formats. JSON is preferred due to its simplicity and ease of use, especially in web applications.

## Defining Data Formats

### Using JSON

JSON is lightweight and easy to parse, making it the most popular choice for RESTful APIs.

Example JSON representation of a `Book` resource:

```json
{
  "id": 1,
  "title": "Effective Java",
  "author": "Joshua Bloch",
  "isbn": "978-0134685991"
}
```

### Using XML

XML is more verbose than JSON but is still used in some enterprise applications where strict data typing and validation are required.

Example XML representation of a `Book` resource:

```xml
<Book>
  <id>1</id>
  <title>Effective Java</title>
  <author>Joshua Bloch</author>
  <isbn>978-0134685991</isbn>
</Book>
```

## Implementing Data Formats in a RESTful Web Service

Using Spring Boot, we can automatically handle JSON and XML data formats with the help of Jackson (for JSON) and JAXB (for XML).

### Define the Data Model

```java
import com.fasterxml.jackson.annotation.JsonProperty;
import javax.xml.bind.annotation.XmlElement;
import javax.xml.bind.annotation.XmlRootElement;

@XmlRootElement(name = "book")
public class Book {
    @JsonProperty("id")
    @XmlElement
    private Long id;

    @JsonProperty("title")
    @XmlElement
    private String title;

    @JsonProperty("author")
    @XmlElement
    private String author;

    @JsonProperty("isbn")
    @XmlElement
    private String isbn;

    // Getters and Setters
}
```

### Create the REST Controller

```java
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

import java.util.Collection;
import java.util.concurrent.ConcurrentHashMap;
import java.util.concurrent.atomic.AtomicLong;

@RestController
@RequestMapping("/api/books")
public class BookController {

    private final Map<Long, Book> bookRepository = a ConcurrentHashMap<>();
    private final AtomicLong idCounter = a AtomicLong();

    @GetMapping(produces = {"application/json", "application/xml"})
    public Collection<Book> getAllBooks() {
        return bookRepository.values();
    }

    @GetMapping(value = "/{id}", produces = {"application/json", "application/xml"})
    public ResponseEntity<Book> getBookById(@PathVariable Long id) {
        Book book = bookRepository.get(id);
        if (book != null) {
            return ResponseEntity.ok(book);
        } else {
            return ResponseEntity.notFound().build();
        }
    }

    @PostMapping(consumes = {"application/json", "application/xml"}, produces = {"application/json", "application/xml"})
    public ResponseEntity<Book> createBook(@RequestBody Book book) {
        long id = idCounter.incrementAndGet();
        book.setId(id);
        bookRepository.put(id, book);
        return ResponseEntity.status(HttpStatus.CREATED).body(book);
    }

    @PutMapping(value = "/{id}", consumes = {"application/json", "application/xml"}, produces = {"application/json", "application/xml"})
    public ResponseEntity<Book> updateBook(@PathVariable Long id, @RequestBody Book book) {
        if (!bookRepository.containsKey(id)) {
            return ResponseEntity.notFound().build();
        }
        book.setId(id);
        bookRepository.put(id, book);
        return ResponseEntity.ok(book);
    }

    @DeleteMapping("/{id}")
    public ResponseEntity<Void> deleteBook(@PathVariable Long id) {
        if (bookRepository.remove(id) != null) {
            return ResponseEntity.noContent().build();
        } else {
            return ResponseEntity.notFound().build();
        }
    }
}
```

### Testing the RESTful Service

You can test the RESTful web service using tools like Postman or curl. Here are some examples:

- **Get all books in JSON**

  ```sh
  curl -H "Accept: application/json" -X GET http://localhost:8080/api/books
  ```

- **Get all books in XML**

  ```sh
  curl -H "Accept: application/xml" -X GET http://localhost:8080/api/books
  ```

- **Create a book in JSON**

  ```sh
  curl -H "Content-Type: application/json" -X POST -d '{"title":"Clean Code","author":"Robert C. Martin","isbn":"978-0132350884"}' http://localhost:8080/api/books
  ```

- **Create a book in XML**

  ```sh
  curl -H "Content-Type: application/xml" -X POST -d '<book><title>Clean Code</title><author>Robert C. Martin</author><isbn>978-0132350884</isbn></book>' http://localhost:8080/api/books
  ```

## Conclusion

Defining the data format is a critical aspect of designing RESTful web services. JSON and XML are the two primary formats used for representing resources. In Java, frameworks like Spring Boot make it straightforward to handle these formats, enabling developers to create robust and flexible RESTful APIs.





# HTTP Methods in RESTful Web Services

Assigning HTTP methods to various actions in a RESTful web service is a key part of adhering to REST principles. The primary HTTP methods used in REST are GET, POST, PUT, DELETE, and PATCH, each serving a specific purpose in manipulating resources.

## HTTP Methods and Their Usage

1. **GET**: Retrieve a resource or a collection of resources.
   - **Use Case**: Fetching data from the server.
   - **Idempotent**: Yes.

2. **POST**: Create a new resource.
   - **Use Case**: Sending data to the server to create a new resource.
   - **Idempotent**: No.

3. **PUT**: Update an existing resource or create a new resource if it does not exist.
   - **Use Case**: Sending data to the server to update a resource.
   - **Idempotent**: Yes.

4. **DELETE**: Delete a resource.
   - **Use Case**: Removing a resource from the server.
   - **Idempotent**: Yes.

5. **PATCH**: Partially update a resource.
   - **Use Case**: Applying partial modifications to a resource.
   - **Idempotent**: No.

## Example RESTful Service with HTTP Methods

### Define the `Book` Resource

```java
public class Book {
    private Long id;
    private String title;
    private String author;
    private String isbn;

    // Getters and Setters
}
```

### Create the REST Controller

```java
@RestController
@RequestMapping("/api/books")
public class BookController {

    private final Map<Long, Book> bookRepository = new ConcurrentHashMap<>();
    private final AtomicLong idCounter = new AtomicLong();

    // GET all books
    @GetMapping(produces = {"application/json", "application/xml"})
    public Collection<Book> getAllBooks() {
        return bookRepository.values();
    }

    // GET a book by ID
    @GetMapping(value = "/{id}", produces = {"application/json", "application/xml"})
    public ResponseEntity<Book> getBookById(@PathVariable Long id) {
        Book book = bookRepository.get(id);
        if (book != null) {
            return ResponseEntity.ok(book);
        } else {
            return ResponseEntity.notFound().build();
        }
    }

    // POST a new book
    @PostMapping(consumes = {"application/json", "application/xml"}, produces = {"application/json", "application/xml"})
    public ResponseEntity<Book> createBook(@RequestBody Book book) {
        long id = idCounter.incrementAndGet();
        book.setId(id);
        bookRepository.put(id, book);
        return ResponseEntity.status(HttpStatus.CREATED).body(book);
    }

    // PUT to update an existing book or create a new book if not exists
    @PutMapping(value = "/{id}", consumes = {"application/json", "application/xml"}, produces = {"application/json", "application/xml"})
    public ResponseEntity<Book> updateBook(@PathVariable Long id, @RequestBody Book book) {
        book.setId(id);
        bookRepository.put(id, book);
        return ResponseEntity.ok(book);
    }

    // DELETE a book by ID
    @DeleteMapping("/{id}")
    public ResponseEntity<Void> deleteBook(@PathVariable Long id) {
        if (bookRepository.remove(id) != null) {
            return ResponseEntity.noContent().build();
        } else {
            return ResponseEntity.notFound().build();
        }
    }

    // PATCH to partially update a book by ID
    @PatchMapping(value = "/{id}", consumes = {"application/json", "application/xml"}, produces = {"application/json", "application/xml"})
    public ResponseEntity<Book> partiallyUpdateBook(@PathVariable Long id, @RequestBody Map<String, Object> updates) {
        Book book = bookRepository.get(id);
        if (book == null) {
            return ResponseEntity.notFound().build();
        }

        // Apply updates to the book...
        bookRepository.put(id, book);
        return ResponseEntity.ok(book);
    }
}
```

## Testing the RESTful Service

- **GET all books**:
  ```sh
  curl -H "Accept: application/json" -X GET http://localhost:8080/api/books
  ```

- **GET book by ID**:
  ```sh
  curl -H "Accept: application/json" -X GET http://localhost:8080/api/books/1
  ```

- **POST a new book**:
  ```sh
  curl -H "Content-Type: application/json" -X POST -d '{"title":"Clean Code","author":"Robert C. Martin","isbn":"978-0132350884"}' http://localhost:8080/api/books
  ```

- **PUT to update a book**:
  ```sh
  curl -H "Content-Type: application/json" -X PUT -d '{"title":"Clean Code Updated","author":"Robert C. Martin","isbn":"978-0132350884"}' http://localhost:8080/api/books/1
  ```

- **DELETE a book**:
  ```sh
  curl -X DELETE http://localhost:8080/api/books/1
  ```

- **PATCH to partially update a book**:
  ```sh
  curl -H "Content-Type: application/json" -X PATCH -d '{"title":"Clean Code Partially Updated"}' http://localhost:8080/api/books/1
  ```

## Conclusion

Assigning HTTP methods appropriately in a RESTful web service ensures that each operation on a resource is clear, intuitive, and conforms to REST principles. Using frameworks like Spring Boot, developers can easily map these HTTP methods to Java methods, making the development of RESTful APIs straightforward and maintainable.



# Developing a JAX-RS RESTful Service

Developing a JAX-RS RESTful service involves creating a set of resources that respond to HTTP requests. JAX-RS (Java API for RESTful Web Services) is a Java programming language API that provides support in creating web services according to the Representational State Transfer (REST) architectural pattern.

## Step-by-Step Guide to Developing a JAX-RS RESTful Service

### 1. Set Up the Project

First, set up a Maven project and add the necessary dependencies. You need a JAX-RS implementation like Jersey.

**pom.xml**:
```xml
<dependencies>
    <!-- JAX-RS API -->
    <dependency>
        <groupId>javax.ws.rs</groupId>
        <artifactId>javax.ws.rs-api</artifactId>
        <version>2.1</version>
    </dependency>

    <!-- Jersey (JAX-RS Reference Implementation) -->
    <dependency>
        <groupId>org.glassfish.jersey.core</groupId>
        <artifactId>jersey-server</artifactId>
        <version>2.33</version>
    </dependency>
    <dependency>
        <groupId>org.glassfish.jersey.containers</groupId>
        <artifactId>jersey-container-servlet</artifactId>
        <version>2.33</version>
    </dependency>

    <!-- JSON processing -->
    <dependency>
        <groupId>org.glassfish.jersey.media</groupId>
        <artifactId>jersey-media-json-binding</artifactId>
        <version>2.33</version>
    </dependency>
</dependencies>
```

### 2. Define the Resource Class

Create a resource class that will handle the HTTP requests.

**Book.java**:
```java
public class Book {
    private Long id;
    private String title;
    private String author;
    private String isbn;

    // Constructors, getters, and setters
}
```

### 3. Create the REST Resource

**BookResource.java**:
```java
import javax.ws.rs.*;
import javax.ws.rs.core.MediaType;
import javax.ws.rs.core.Response;
import java.util.Collection;
import java.util.Map;
import java.util.concurrent.ConcurrentHashMap;
import java.util.concurrent.atomic.AtomicLong;

@Path("/books")
public class BookResource {

    private static final Map<Long, Book> bookRepository = new ConcurrentHashMap<>();
    private static final AtomicLong idCounter = new AtomicLong();

    @GET
    @Produces({ MediaType.APPLICATION_JSON, MediaType.APPLICATION_XML })
    public Collection<Book> getAllBooks() {
        return bookRepository.values();
    }

    @GET
    @Path("/{id}")
    @Produces({ MediaType.APPLICATION_JSON, MediaType.APPLICATION_XML })
    public Response getBookById(@PathParam("id") Long id) {
        Book book = bookRepository.get(id);
        if (book != null) {
            return Response.ok(book).build();
        } else {
            return Response.status(Response.Status.NOT_FOUND).build();
        }
    }

    @POST
    @Consumes({ MediaType.APPLICATION_JSON, MediaType.APPLICATION_XML })
    @Produces({ MediaType.APPLICATION_JSON, MediaType.APPLICATION_XML })
    public Response createBook(Book book) {
        long id = idCounter.incrementAndGet();
        book.setId(id);
        bookRepository.put(id, book);
        return Response.status(Response.Status.CREATED).entity(book).build();
    }

    @PUT
    @Path("/{id}")
    @Consumes({ MediaType.APPLICATION_JSON, MediaType.APPLICATION_XML })
    @Produces({ MediaType.APPLICATION_JSON, MediaType.APPLICATION_XML })
    public Response updateBook(@PathParam("id") Long id, Book book) {
        if (!bookRepository.containsKey(id)) {
            return Response.status(Response.Status.NOT_FOUND).build();
        }
        book.setId(id);
        bookRepository.put(id, book);
        return Response.ok(book).build();
    }

    @DELETE
    @Path("/{id}")
    public Response deleteBook(@PathParam("id") Long id) {
        if (bookRepository.remove(id) != null) {
            return Response.noContent().build();
        } else {
            return Response.status(Response.Status.NOT_FOUND).build();
        }
    }
}
```

### 4. Configure the Application

**MyApplication.java**:
```java
import javax.ws.rs.ApplicationPath;
import javax.ws.rs.core.Application;
import java.util.HashSet;
import java.util.Set;

@ApplicationPath("/api")
public class MyApplication extends Application {

    @Override
    public Set<Class<?>> getClasses() {
        Set<Class<?>> classes = new HashSet<>();
        classes.add(BookResource.class);
        return classes;
    }
}
```

### 5. Configure the Deployment Descriptor

**web.xml**:
```xml
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
         http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd"
         version="3.1">

    <display-name>JAX-RS Example</display-name>

    <servlet>
        <servlet-name>Jersey Web Application</servlet-name>
        <servlet-class>org.glassfish.jersey.servlet.ServletContainer</servlet-class>
        <init-param>
            <param-name>jersey.config.server.provider.packages</param-name>
            <param-value>com.example</param-value>
        </init-param>
        <load-on-startup>1</load-on-startup>
    </servlet>
    <servlet-mapping>
        <servlet-name>Jersey Web Application</servlet-name>
        <url-pattern>/api/*</url-pattern>
    </servlet-mapping>

</web-app>
```

### HTTP Method and URI Matching

- **GET /api/books**: Fetch all books.
- **GET /api/books/{id}**: Fetch a specific book by ID.
- **POST /api/books**: Create a new book.
- **PUT /api/books/{id}**: Update a specific book by ID.
- **DELETE /api/books/{id}**: Delete a specific book by ID.

### Testing the RESTful Service

You can use tools like Postman or curl to test your RESTful web service.

**Examples**:

- **GET all books**:
  ```sh
  curl -X GET http://localhost:8080/api/books
  ```

- **GET a book by ID**:
  ```sh
  curl -X GET http://localhost:8080/api/books/1
  ```

- **POST a new book**:
  ```sh
  curl -X POST -H "Content-Type: application/json" -d '{"title":"Effective Java","author":"Joshua Bloch","isbn":"978-0134685991"}' http://localhost:8080/api/books
  ```

- **PUT to update a book**:
  ```sh
  curl -X PUT -H "Content-Type: application/json" -d '{"title":"Effective Java, 2nd Edition","author":"Joshua Bloch","isbn":"978-0134685991"}' http://localhost:8080/api/books/1
  ```

- **DELETE a book**:
  ```sh
  curl -X DELETE http://localhost:8080/api/books/1
  ```

### Conclusion

This guide provides a basic overview of how to develop a JAX-RS RESTful web service in Java. By defining resources, creating a REST controller, and configuring the application, you can set up endpoints that handle HTTP methods and URI matching for various operations on resources. This structure allows for a clean, maintainable, and scalable RESTful service.

