# 🌱 Spring Boot Introduction Project

A hands-on project focused on learning **Spring Beans** and **Dependency Injection** concepts.

## 🎯 What I Learned
- Spring Beans lifecycle and configuration
- Dependency Injection (Constructor, Setter, Field)
- IoC Container and Component Scanning
- **Spring Profiles** for environment-specific configurations
- Best practices for enterprise applications

## 🚀 Quick Start
```bash
git checkout master  # Main code is in master branch

# Run using IntelliJ IDEA (Recommended)
# 1. Click Run button in IntelliJ
# 2. Or use Run Configuration with profile arguments

# Alternative: Set profile in application.properties
# spring.profiles.active=dev
            OR
# Run with default profile
mvn spring-boot:run

# Run with specific profile
mvn spring-boot:run -Dspring-boot.run.profiles=dev
mvn spring-boot:run -Dspring-boot.run.profiles=prod
```

## 💻 Technologies
- **Java** | **Spring Boot** | **Maven**
- Spring Core (IoC & DI) | REST APIs

## 📂 Project Structure
```
src/main/java/com/springboot/introduction/
├── IntroductionToSpringbootApplication.java  # Main Spring Boot class
├── AppConfig.java                            # Bean configuration
├── Apple.java                                # Bean example with lifecycle
├── DB.java & ProdDB.java                     # Database interface & implementation
├── DBService.java & DevDB.java               # Service layer with DI
└── resources/application.properties          # App configuration
```

## 🔧 Core Concepts Demonstrated

### Bean Lifecycle Example
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

### Spring Profiles Example
```java
@Component
@ConditionalOnProperty(name = "deploy.env", havingValue = "development")
public class DevDB implements DB {

    public String getData() {
        return "Dev Data";
    }

}

@Component
@ConditionalOnProperty(name = "deploy.env", havingValue = "production")
public class ProdDB implements DB{

    public String getData() {
        return "Prod Data";
    }
}
```

### Dependency Injection Example
```java
@Service
public class DBService {

    @Autowired
    final private DB db;

    public DBService(DB db) {
        this.db = db;
    }
    String getData() {
        return db.getData();
    }

}
```

## 🌟 Key Benefits Learned
- **Loose Coupling** - Easy to maintain and test
- **Environment-specific Configuration** - Different profiles for dev/prod
- **Reusable Components** - Beans managed by Spring
- **Clean Architecture** - Separation of concerns

## 📝 Project Structure
- **main branch**: Documentation
- **master branch**: Complete Spring Boot code

## 👨‍💻 Developer
**Mansi Arora** - Learning Spring Boot fundamentals

---
⭐ Star if helpful for Spring Boot learning!
