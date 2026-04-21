# 🌱 Spring Boot Introduction

A hands-on project focused on learning **Spring Beans** and **Dependency Injection** concepts in Spring Boot.

---

## ☁️ Core Concepts Overview

| Concept | Description |
|---------|-------------|
| Spring Beans | Objects managed by Spring IoC Container |
| Dependency Injection | Constructor, Setter, Field injection |
| Bean Lifecycle | @PostConstruct & @PreDestroy hooks |
| Spring Profiles | Environment-specific bean loading |
| Component Scanning | Auto-detection of Spring components |

---

## 🛠️ What I Built

### 1. Bean Lifecycle Management
- `Apple.java` — demonstrates `@PostConstruct` and `@PreDestroy`
- `AppConfig.java` — manual bean configuration

### 2. Spring Profiles Setup
- `DevDB.java` — loads only when `deploy.env=development`
- `ProdDB.java` — loads only when `deploy.env=production`
- `application.properties` — profile switching config

### 3. Dependency Injection
- `DBService.java` — constructor injection with `DB` interface
- Interface + Implementation pattern for loose coupling

---

## ⚙️ How Profiles Work

Set active profile in `application.properties`:
```properties
deploy.env=development
```

| Profile | Bean Loaded | Data Returned |
|---------|-------------|---------------|
| `development` | `DevDB` | "Dev Data" |
| `production` | `ProdDB` | "Prod Data" |

---

## 🔧 Core Concepts Demonstrated

### Bean Lifecycle
```java
@Component
public class Apple {
    void eatApple() {
        System.out.println("I am eating the apple");
    }

    @PostConstruct
    void callThisBeforeAppleIsUsed() {
        System.out.println("Creating the apple before use");
    }

    @PreDestroy
    void callThisBeforeDestroy() {
        System.out.println("Destroying the Apple bean");
    }
}
```

### Spring Profiles
```java
@Component
@ConditionalOnProperty(name = "deploy.env", havingValue = "development")
public class DevDB implements DB {
    public String getData() { return "Dev Data"; }
}

@Component
@ConditionalOnProperty(name = "deploy.env", havingValue = "production")
public class ProdDB implements DB {
    public String getData() { return "Prod Data"; }
}
```

### Constructor Injection
```java
@Service
public class DBService {
    final private DB db;

    public DBService(DB db) {
        this.db = db;
    }

    String getData() {
        return db.getData();
    }
}
```

---

## 🚀 Quick Start

**Prerequisites:** Java 21+, Maven

```bash
git clone https://github.com/MansiArora-dev/springboot-introduction.git
cd springboot-introduction
```

**Using IntelliJ IDEA (Recommended):**
1. Open project in IntelliJ
2. Run → **Edit Configurations**
3. Program arguments: `--spring.profiles.active=dev` or `--spring.profiles.active=prod`

      OR
   
   Environment variables: `DEPLOY_ENV=development` or `DEPLOY_ENV=production`
5. Click **Run ▶️**

**Using Maven:**
```bash
# Run with dev profile
mvn spring-boot:run -Dspring-boot.run.profiles=dev

# Run with prod profile
mvn spring-boot:run -Dspring-boot.run.profiles=prod
```
---

## 📂 Project Structure
```
src/main/java/com/springboot/introduction/
├── IntroductionToSpringbootApplication.java  # Main entry point
├── AppConfig.java                            # Bean configuration
├── Apple.java                                # Bean lifecycle example
├── DB.java                                   # Database interface
├── DevDB.java                                # Dev environment implementation
├── ProdDB.java                               # Prod environment implementation
├── DBService.java                            # Service layer with DI
└── resources/
    └── application.properties                # App configuration
```
---

## 💻 Technologies
- **Java 21** | **Spring Boot** | **Maven**
- Spring Core (IoC & DI)

---

## 🌟 Key Takeaways
- **Loose Coupling** — Easy to maintain and test
- **Environment-specific Configuration** — Different beans for dev/prod
- **Reusable Components** — Beans managed by Spring IoC
- **Clean Architecture** — Separation of concerns

---

## 👩‍💻 Developer
**Mansi Arora** — Software Engineer
