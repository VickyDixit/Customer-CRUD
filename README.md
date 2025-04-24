# 🧾 Customer Management

This is a RESTful **ASP.NET Core Web API** project to manage **Customer Personal and Employment Details** using clean architecture principles.

---

## 📌 Features

- ✅ CRUD Operations (Create, Read, Update, Delete)
- ✅ RESTful API built using ASP.NET Core Web API
- ✅ Database access via **ADO.NET** (No Entity Framework)
- ✅ Separation of Concerns using **Service + Repository Pattern**
- ✅ Swagger (OpenAPI) documentation
- ✅ Bootstrap + HTML/JS-based Frontend (served from `/UI`)
- ✅ Currency formatting and Bootstrap UI in frontend

---

## 🧱 Why This Project Uses Separation of Concerns

This project follows the **Separation of Concerns (SoC)** design principle to improve maintainability, readability, and scalability.

### 🎯 Breakdown of Each Layer

| Layer           | Responsibility                                                                 |
|-----------------|----------------------------------------------------------------------------------|
| **Controllers** | Handles HTTP requests and responses. Delegates business logic to services.      |
| **Services**    | Contains application logic. Converts DTOs to domain models and vice versa.     |
| **Repositories**| Responsible for direct database interaction using ADO.NET.                      |
| **DTOs**        | Data Transfer Objects used for receiving and sending simplified data structures.|
| **Models**      | Domain entities representing real-world business data (e.g., Customer, Employment). |
| **Validators**  | Ensures incoming data is clean and valid before any business logic is applied.  |
| **Data Layer**  | Provides utility for creating and managing SQL connections (e.g., DbConnectionFactory). |

### ✅ Benefits of This Approach

- **Maintainability**: Each layer has a single responsibility, making the code easier to manage.
- **Scalability**: Business logic, database code, and UI can evolve independently.
- **Testability**: You can test each layer in isolation using mocks.
- **Reusability**: Business logic or data access logic can be reused in other projects or interfaces (e.g., mobile apps, background jobs).

---

## 🏗 Technologies Used

| Layer            | Tech Used                      |
|------------------|-------------------------------|
| Backend API      | ASP.NET Core Web API (.NET 6+) |
| Database Access  | ADO.NET (SqlConnection)        |
| Frontend UI      | HTML, Bootstrap, JavaScript    |
| Documentation    | Swagger (Swashbuckle)          |
| Architecture     | Repository & DTO Pattern       |

---

## 📁 Project Structure

```
CustomerRegistrationAPI/
├── Controllers/        # API Controllers
├── DTOs/               # Clean input/output models
├── Models/             # Domain entities
├── Repositories/       # Data access layer (ADO.NET)
├── Services/           # Business logic layer
├── Validators/         # Custom validation logic
├── Data/               # DB connection factory
├── UI/                 # HTML/JS frontend
├── appsettings.json    # DB connection string
├── Program.cs          # App bootstrap & DI
```

---

## 🔧 Setup Instructions

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/customer-registration-api.git
   cd customer-registration-api
   ```

2. **Create Database in SQL Server:**
   ```sql
   CREATE DATABASE CustomerDB;
   USE CustomerDB;
   CREATE TABLE Customers (
       Id INT PRIMARY KEY IDENTITY,
       FullName NVARCHAR(100),
       Email NVARCHAR(100),
       Phone NVARCHAR(15),
       CompanyName NVARCHAR(100),
       Designation NVARCHAR(100),
       Salary DECIMAL(18, 2)
   );
   ```

3. **Update `appsettings.json`:**
   ```json
   "ConnectionStrings": {
     "DefaultConnection": "Server=localhost;Database=CustomerDB;Trusted_Connection=True;"
   }
   ```

4. **Run the Project in Visual Studio 2022**

---

## 🌐 API Endpoints

| Method | Endpoint               | Description         |
|--------|------------------------|---------------------|
| GET    | `/api/customer`        | Get all customers   |
| GET    | `/api/customer/{id}`   | Get customer by ID  |
| POST   | `/api/customer`        | Create new customer |
| PUT    | `/api/customer/{id}`   | Update customer     |
| DELETE | `/api/customer/{id}`   | Delete customer     |

📘 Swagger UI available at:
```
https://localhost:{port}/swagger
```

---

## 🎨 Frontend

- Frontend served from `/UI/index.html`
- Built using Bootstrap + JS
- Currency formatted using `Intl.NumberFormat('en-IN', { style: 'currency', currency: 'INR' })`

---

## 🙌 Contributions

Contributions and PRs are welcome! Fork this repo and raise an issue or PR.

---

## 🧑‍💻 Author

Developed by Vicky Dixit

---

## 📜 License

This project is licensed under the MIT License.
