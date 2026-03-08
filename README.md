# 👤 User Service

[![Kotlin](https://img.shields.io/badge/Kotlin-1.9.22-7F52FF?style=flat&logo=kotlin)](https://kotlinlang.org/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.2.3-6DB33F?style=flat&logo=springboot)](https://spring.io/projects/spring-boot)
[![Status](https://img.shields.io/badge/Status-Not_Started-red?style=flat)](#)

User profile, preferences, and settings management service for Trainer Hub platform.

---

## 🔗 Trainer Hub Ecosystem

**📚 [Documentation Hub](https://github.com/MateusO97/trainer-hub-docs)** | **🗺️ [Ecosystem Map](https://github.com/MateusO97/trainer-hub-docs/blob/master/ECOSYSTEM-MAP.md)** | **📋 [All Repositories](https://github.com/MateusO97/trainer-hub-docs/blob/master/REPOSITORIES.md)** | **🔌 [API Contracts](https://github.com/MateusO97/trainer-hub-docs/blob/master/docs/API-CONTRACTS.md)**

---

## 📋 Overview

The **User Service** manages all user-related data beyond authentication, including:
- Personal profiles (physical data, demographics)
- User preferences (diet type, restrictions, allergies)
- Goals and targets configuration
- Notification settings
- Activity level tracking

This service is part of **Wave 1** (foundational services) with no business logic dependencies beyond Auth Service.

---

## ✨ Features

- ✅ User profile management (birthDate, gender, height, weight, activityLevel)
- ✅ User preferences 
(dietType, restrictions, allergies, dislikedFoods)
- ✅ Goals configuration (weight loss, muscle gain, maintenance)
- ✅ Notification preferences (email, push, meal reminders)
- ✅ Profile history tracking
- ✅ Privacy settings

---

## 🏗️ Architecture

**Port**: `8082`  
**Database**: PostgreSQL  
**Cache**: Redis  
**Pattern**: Clean Architecture (Controller → Service → Repository → Entity)

### Dependencies
- **Auth Service** (8081) - Token validation

### API Endpoints

```
GET    /api/v1/users/{userId}
PATCH  /api/v1/users/{userId}
GET    /api/v1/users/{userId}/preferences
PATCH  /api/v1/users/{userId}/preferences
GET    /api/v1/users/{userId}/goals
POST   /api/v1/users/{userId}/goals
PATCH  /api/v1/users/{userId}/goals/{goalId}
```

---

## 🚀 Quick Start

```bash
# Clone repository
git clone https://github.com/MateusO97/trainer-hub-user-service.git
cd trainer-hub-user-service

# Start dependencies (PostgreSQL + Redis)
docker-compose up -d

# Build and run
./gradlew bootRun

# Run tests
./gradlew test

# Check code quality
./gradlew ktlintCheck detekt
```

---

## 🗄️ Database Schema

### Tables
- `user_profiles` - Personal info & physical data
- `user_preferences` - Diet preferences & restrictions
- `user_goals` - Weight/fitness goals
- `user_settings` - App & notification settings

See full schema in `src/main/resources/db/migration/V1__initial_schema.sql`

---

## 📚 Documentation

- **[API Contract](https://github.com/MateusO97/trainer-hub-docs/blob/master/docs/API-CONTRACTS.md#2-user-service-apis)** - Detailed API specification
- **[Architecture](https://github.com/MateusO97/trainer-hub-docs/blob/master/docs/02-ARCHITECTURE.md)** - Overall system design
- **[Engineering Standards](https://github.com/MateusO97/trainer-hub-docs/blob/master/docs/INFRASTRUCTURE/)** - Coding guidelines

---

## 🧪 Testing

- **Unit Tests**: ≥80% coverage required
- **Integration Tests**: TestContainers for PostgreSQL
- **Contract Tests**: Pact for API contracts

```bash
./gradlew test jacocoTestReport
open build/reports/jacoco/test/html/index.html
```

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| Language | Kotlin 1.9.22 |
| Framework | Spring Boot 3.2.3 |
| Database | PostgreSQL 15 |
| Cache | Redis 7.0 |
| Build Tool | Gradle 8.6 |
| Testing | JUnit 5, Mockito, TestContainers |
| Linting | ktlint 11.6.1, detekt 1.23.0 |
| Documentation | SpringDoc OpenAPI 2.3.0 |

---

## 🤝 Contributing

See [Git Workflow](https://github.com/MateusO97/trainer-hub-docs/blob/master/docs/INFRASTRUCTURE/GIT-WORKFLOW.md) and [Coding Standards](https://github.com/MateusO97/trainer-hub-docs/blob/master/docs/INFRASTRUCTURE/CODING-STANDARDS.md).

1. Create feature branch: `git checkout -b feature/USER-001-description`
2. Implement with tests (≥80% coverage)
3. Run linting: `./gradlew ktlintCheck detekt`
4. Create PR following [PR Standards](https://github.com/MateusO97/trainer-hub-docs/blob/master/docs/INFRASTRUCTURE/PR-STANDARDS.md)
5. Wait for CI/CD and code review

---

## 📄 License

MIT License - See [LICENSE](LICENSE)

---

**Part of [Trainer Hub Platform](https://github.com/MateusO97/trainer-hub-docs)** 🏋️
