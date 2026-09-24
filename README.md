# SpringUi — Subscriber Registration (Spring Boot + React)

A small full-stack example: a **React** form that registers telecom subscribers through a **Spring Boot** REST API and stores them with **Spring Data JPA**.

```text
React form (localhost:3000) ──POST JSON──▶ Spring Boot API ──JPA──▶ SUBSCRIBERS table
```

## 🔌 API

`POST /v1/subscriber/createSubscriber`

```json
{
  "subscriberName": "Ada",
  "subscriberSurname": "Lovelace",
  "subscriberMsisdn": "905xxxxxxxxx",
  "subscriberTariffId": "T1"
}
```

Returns the saved subscriber (id, name, surname, MSISDN, tariff id and start date).

## 🧰 Tech stack

| Part | Technologies |
| --- | --- |
| Backend | Java 17, Spring Boot 3.3, Spring Web, Spring Data JPA, Bean Validation |
| Frontend | React 18 (Create React App) |
| Database | Any JPA-supported RDBMS — `application.properties` ships with a SQL Server template, and the Oracle JDBC driver (`ojdbc11`) is included |

CORS is enabled for `http://localhost:3000`.

## 📁 Project structure

```text
springUI/
├── src/main/java/com/ky/springui/
│   ├── controller/      # SubscriberController (REST)
│   ├── service/         # SubscriberService
│   ├── repository/      # SubscriberRepository (JPA)
│   ├── model/           # Subscriber entity
│   ├── request/, dto/, mapper/
│   └── configuration/   # CORS config
└── ui/                  # React app (Form.jsx)
```

## 🚀 Getting started

**Backend**

1. Set the datasource in `springUI/src/main/resources/application.properties`
   (for SQL Server, add the `com.microsoft.sqlserver:mssql-jdbc` dependency).
2. The UI posts to port **8090**, so add `server.port=8090` to `application.properties`.
3. Run:

   ```bash
   cd springUI
   ./mvnw spring-boot:run
   ```

**Frontend**

```bash
cd springUI/ui
npm install
npm start   # http://localhost:3000
```

## 🗺️ Roadmap

- [ ] Implement `Subscriber.builder()` (e.g. with Lombok `@Builder`) — it is currently a placeholder, so creating a subscriber fails
- [ ] Show a success / error message in the UI after submitting the form
