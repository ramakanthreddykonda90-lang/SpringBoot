# Why Do We Need Spring Framework?

## 1. Before Learning Spring – Understand the Problem

Before learning Spring Framework, we should understand two things:

1. What is a Servlet?
2. What is a Servlet Container?

Then we can understand why Spring was introduced.

---

## 2. What is a Servlet?

**Definition:**

A Servlet is a Java class that handles HTTP requests from clients and generates HTTP responses.

### Why do we need Servlets?

Imagine we are developing a banking application.

A user enters their username and password and clicks the Login button.

The browser sends an HTTP request:

```http
POST /login
username=ram
password=1234
```

A Servlet receives this request, processes the login information and sends a response.

### Simple Servlet Example

```java
@WebServlet("/hello")
public class HelloServlet extends HttpServlet {

    @Override
    protected void doGet(
        HttpServletRequest request,
        HttpServletResponse response
    ) throws IOException {

        response.getWriter().println("Hello Ram!");
    }
}
```

### Understanding the code

- `@WebServlet("/hello")` → Maps the URL `/hello` to this Servlet.
- `HttpServlet` → Provides methods to handle HTTP requests.
- `doGet()` → Executes when a GET request is received.
- `HttpServletRequest` → Contains incoming request information.
- `HttpServletResponse` → Helps send a response to the client.

### Remember

Servlet = Handles HTTP requests and responses.

---

## 3. What is a Servlet Container?

**Definition:**

A Servlet Container is an environment that manages and executes Servlets.

### Why do we need it?

A Servlet is just a Java class. It cannot independently listen for HTTP requests.

It needs an environment to execute.

That environment is called a Servlet Container.

### Examples

- Apache Tomcat
- Jetty
- Undertow

### Responsibilities of a Servlet Container

1. Creates Servlet objects.
2. Manages the Servlet lifecycle.
3. Maps URLs to appropriate Servlets.
4. Receives HTTP requests and invokes the appropriate Servlet.
5. Sends responses back to clients.
6. Manages request handling and multithreading.

### Simple understanding

Think of a Servlet as an employee who performs a particular task.

The Servlet Container is like a manager who assigns work to the employee and manages their working environment.

### Remember

Servlet = Performs the request-handling task.

Servlet Container = Manages the Servlet and its execution.

---

## 4. Why Do We Need Spring Framework?

Now imagine we are developing a complete banking application using only Servlets.

Our application needs:

- User registration and login.
- Account management.
- Money transfers.
- Transaction history.
- Database connectivity.
- Authentication and authorization.

As the application grows, managing everything manually becomes difficult.

Let's understand the problems.

### Problem 1: Manual Object Creation

Without Spring, we create objects manually using the `new` keyword.

Example:

```java
class AccountRepository {
}

class AccountService {

    AccountRepository repository =
        new AccountRepository();
}
```

Here, AccountService is responsible for creating its dependency.

If we change the repository implementation, we may need to modify the service class.

This creates tight coupling.

**How Spring solves it:**

Spring provides an IoC Container and Dependency Injection.

Spring creates objects and injects the required dependencies.

### Problem 2: Database Management

When using JDBC directly, we commonly need to handle:

- Database connections.
- SQL queries.
- PreparedStatements.
- ResultSets.
- Closing database resources.
- Transaction management.

Writing this code repeatedly increases development effort.

**How Spring helps:**

Spring provides Spring JDBC, Spring ORM and transaction management to simplify database operations.

### Problem 3: Security Management

Our banking application needs:

- Authentication.
- Authorization.
- Password validation.
- Session management.

Implementing all security-related infrastructure manually takes considerable effort.

**How Spring helps:**

Spring Security provides infrastructure for authentication, authorization and other security requirements.

### Problem 4: Request Handling

In a Servlet-based application, we may need to write repetitive request-processing and response-handling code.

**How Spring helps:**

Spring MVC provides a structured way to handle HTTP requests using Controllers, Services and other components.

### Conclusion

Spring reduces repetitive infrastructure code and makes applications easier to develop, test and maintain.

---

## 5. How Does Spring Framework Solve These Problems?

| Problem | Spring Solution |
|---|---|
| Manual object creation | IoC Container |
| Dependency management | Dependency Injection |
| Database operations | Spring JDBC / Spring Data |
| Transaction management | `@Transactional` |
| HTTP request handling | Spring MVC |
| Security | Spring Security |
| Object configuration | Spring Configuration |

### Example: Dependency Injection

Without Spring:

```java
class AccountRepository {
}

class AccountService {

    AccountRepository repository =
        new AccountRepository();
}
```

With Spring:

```java
@Component
class AccountRepository {
}

@Service
class AccountService {

    private final AccountRepository repository;

    public AccountService(AccountRepository repository) {
        this.repository = repository;
    }
}
```

### What happens internally?

1. Spring scans the application for components.
2. It creates an AccountRepository object.
3. It creates an AccountService object.
4. It injects AccountRepository into AccountService.

This is called Dependency Injection.

**Remember:**

Dependency Injection means providing an object with the dependencies it needs instead of making it create those dependencies itself.

---

## 6. Does Spring Replace Servlets and Servlet Containers?

**Answer: NO!**

Spring does not replace Servlets or Servlet Containers.

In fact, Spring MVC internally uses a special Servlet called `DispatcherServlet`.

### What is DispatcherServlet?

DispatcherServlet is the Front Controller of Spring MVC.

It receives incoming HTTP requests and dispatches them to the appropriate Controller.

### Request Flow

Consider a user requesting account details.

```text
          Client / Browser
                 |
                 | HTTP Request
                 v
          Tomcat Server
                 |
                 v
          DispatcherServlet
                 |
                 v
             Controller
                 |
                 v
              Service
                 |
                 v
             Repository
                 |
                 v
              Database
                 |
                 v
          HTTP Response
                 |
                 v
          Client / Browser
```

### Step-by-step explanation

1. Client sends an HTTP request.
2. Tomcat receives the request.
3. Tomcat invokes Spring's DispatcherServlet.
4. DispatcherServlet identifies the appropriate Controller.
5. Controller calls the Service layer.
6. Service communicates with the Repository.
7. Repository interacts with the database.
8. The result is returned through the Controller and DispatcherServlet.
9. Tomcat sends the HTTP response to the client.

### Important

Tomcat is still responsible for running the Servlet.

Spring MVC provides higher-level web application infrastructure.

---

## 7. Servlet vs Spring Framework

| Servlet | Spring Framework |
|---|---|
| Java web API | Application development framework |
| Handles HTTP requests and responses | Provides application infrastructure |
| Manual object creation is common | Provides IoC and DI |
| JDBC code is commonly written manually | Provides database integration |
| Manual transaction handling is common | Provides declarative transactions |
| Does not provide a general-purpose IoC container | Provides an IoC container |

---

## 8. Interview Questions

### Q1. What is a Servlet?

A Servlet is a Java class that handles HTTP requests and generates HTTP responses. It runs inside a Servlet Container such as Tomcat.

### Q2. What is a Servlet Container?

A Servlet Container manages the lifecycle and execution of Servlets. Examples include Tomcat, Jetty and Undertow.

### Q3. Why do we need Spring Framework?

Spring simplifies Java application development by providing IoC, Dependency Injection, transaction management, database integration, Spring MVC and security infrastructure.

### Q4. Does Spring replace Tomcat?

No. Spring MVC uses DispatcherServlet, which runs inside a Servlet Container such as Tomcat.

### Q5. What is DispatcherServlet?

DispatcherServlet is the Front Controller in Spring MVC. It receives HTTP requests and dispatches them to appropriate Controllers.

### Q6. Can we develop web applications without Spring?

Yes. We can develop web applications using Servlets and Servlet Containers. However, Spring simplifies application development and maintenance.

---

## 9. Interview-Ready Answer

**Question: Why do we need Spring Framework when we already have Servlets and Servlet Containers?**

Servlets and Servlet Containers are sufficient to develop Java web applications. However, as applications grow, we need to manage object creation, dependency management, database operations, transactions and security.

Managing these things manually increases boilerplate code and creates tight coupling.

Spring Framework solves these problems by providing features like Inversion of Control, Dependency Injection, transaction management, Spring MVC and Spring Security.

Spring does not replace Servlets or Servlet Containers. Spring MVC itself uses DispatcherServlet, which runs inside a Servlet Container such as Tomcat.

Therefore, Spring makes Java application development easier, modular, loosely coupled and maintainable.

---

## 10. Quick Revision (Read Before an Interview)

| Concept | One-line Explanation |
|---|---|
| Servlet | Handles HTTP requests and responses |
| Servlet Container | Manages and executes Servlets |
| Tomcat | Popular Servlet Container |
| Spring Framework | Simplifies Java application development |
| IoC | Transfers control of object creation and management to the container |
| DI | Provides required dependencies to an object |
| DispatcherServlet | Front Controller of Spring MVC |
| Spring MVC | Handles web requests using a structured architecture |

### Remember This Flow

Servlet → Servlet Container → Problems with manual application development → Spring Framework → IoC and DI → Spring MVC → DispatcherServlet

---

## 11. Self-Assessment

Try answering these questions without looking at the notes:

- [ ] Can I explain what a Servlet is?
- [ ] Can I explain why Tomcat is needed?
- [ ] Can I explain the problems of developing applications using only Servlets?
- [ ] Can I explain how Spring solves those problems?
- [ ] Can I explain the difference between IoC and DI?
- [ ] Can I explain DispatcherServlet?
- [ ] Can I explain the complete HTTP request flow?

**Learning Status:** Not Started / Learning / Completed / Needs Revision

**Last Revised:** YYYY-MM-DD

