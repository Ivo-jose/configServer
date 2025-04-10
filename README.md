# ms-configServer

## 📖 Overview
The **ms-configServer** is a centralized configuration service for a microservices architecture. It provides a single source of truth for managing configuration properties across all microservices, ensuring consistency and simplifying configuration management.

This service is built using **Spring Cloud Config Server** and supports both local and remote configuration repositories.

---

## 🚀 Features
- Centralized configuration management for microservices.
- Supports configuration from Git repositories or local files.
- Dynamic refresh of configuration properties (when integrated with Spring Cloud Bus).
- Secure and scalable configuration management.

---

## 🛠️ Technologies
- **Java 21**: Latest version of Java for modern features and performance.
- **Spring Boot 3.4.4**: Framework for building microservices.
- **Spring Cloud Config Server**: Centralized configuration management.
- **Maven**: Dependency and build management.

---

## 📦 Dependencies
The key dependencies used in this project are:
- `spring-boot-starter-actuator`: For monitoring and management endpoints.
- `spring-cloud-config-server`: Core library for the configuration server.
- `lombok`: Simplifies Java code with annotations.

For a full list of dependencies, check the `pom.xml` file.

---

## ⚙️ How to Run

### Prerequisites
- **Java 21** installed.
- **Maven** installed.
- A Git repository or local directory with configuration files.

### Steps

1. Clone the repository:

   ```bash
   git clone https://github.com/Ivo-jose/configServer.git
   cd ms-configServer
   ```

2. Configure the `application.yml` (or `bootstrap.yml`) to point to the desired configuration repository:

   **Example using Git:**
   ```yaml
   spring:
     cloud:
       config:
         server:
           git:
             uri: https://github.com/seu-usuario/config-repo
   ```

3. Build and run the application:

   ```bash
   ./mvnw clean install
   ./mvnw spring-boot:run
   ```

   The server will be available at:  
   [http://localhost:8888](http://localhost:8888)

---

## 📁 Configuration Structure

The configuration files should follow this naming convention:

```
<application-name>.yml
<application-name>-<profile>.yml
```

**Examples:**
- `gateway.yml`
- `gateway-dev.yml`
- `auth-prod.yml`

These files should contain the properties required by your microservices.

---

## 🔄 Dynamic Refresh

If using **Spring Cloud Bus** with a message broker (like RabbitMQ or Kafka), clients can refresh their configuration by sending a `POST` request to:

```
/actuator/refresh
```

---

## 🔐 Security (Optional)

You can secure the config server with basic authentication or OAuth2. Example using basic auth:

```yaml
spring:
  security:
    user:
      name: admin
      password: secret
```

---

## 📚 Documentation

- [Spring Cloud Config Server Documentation](https://docs.spring.io/spring-cloud-config/docs/current/reference/html/)
- [Spring Boot Documentation](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/)

---

## 👨‍💻 Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.

---

## 📝 License

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.
