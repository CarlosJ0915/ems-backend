# Employee Management System - Backend

A robust REST API backend for managing employees and departments, built with **Spring Boot**, **Java**, and **MySQL**.

## 🎯 Features

- ✅ Employee management (Create, Read, Update, Delete)
- ✅ Department management 
- ✅ RESTful API endpoints
- ✅ Data persistence with JPA/Hibernate
- ✅ MySQL database integration
- ✅ Exception handling with custom error responses
- ✅ DTO-based API contracts
- ✅ Clean architecture with layered design

## 🏗️ Project Architecture

```
ems-backend/
├── src/main/java/net/javaguides/ems_backend/
│   ├── controller/          # REST API endpoints
│   │   ├── EmployeeController
│   │   └── DepartmentController
│   ├── service/             # Business logic interfaces
│   │   ├── EmployeeService
│   │   └── DepartmentService
│   ├── service/impl/        # Service implementations
│   │   ├── EmployeeServiceImpl
│   │   └── DepartmentServiceImpl
│   ├── repository/          # Data access layer (JPA)
│   │   ├── EmployeeRepository
│   │   └── DepartmentRepository
│   ├── entity/              # JPA entities
│   │   ├── Employee
│   │   └── Department
│   ├── dto/                 # Data Transfer Objects
│   │   ├── EmployeeDto
│   │   └── DepartmentDto
│   ├── mapper/              # DTO to Entity mappers
│   │   ├── EmployeeMapper
│   │   └── DepartmentMapper
│   ├── exception/           # Custom exceptions
│   │   └── ResourceNotFoundException
│   └── EmsBackendApplication.java  # Main Spring Boot class
├── src/main/resources/
│   └── application.properties      # Configuration
├── pom.xml                  # Maven dependencies
└── mvnw                     # Maven wrapper scripts
```

## 🛠️ Tech Stack

- **Java 26**
- **Spring Boot 4.0.6**
  - Spring Data JPA
  - Spring Web MVC
- **MySQL** (Database)
- **Maven** (Build tool)
- **Lombok** (Optional - for reducing boilerplate)

## 🚀 Getting Started

### Prerequisites
- Java 26 or later
- MySQL Server running locally or accessible
- Maven (or use included mvnw)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/ems-backend.git
   cd ems-backend
   ```

2. **Configure Database**
   
   Update `src/main/resources/application.properties`:
   ```properties
   spring.application.name=ems-backend
   
   # MySQL Configuration
   spring.datasource.url=jdbc:mysql://localhost:3306/ems_db
   spring.datasource.username=root
   spring.datasource.password=your_password
   spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
   
   # JPA Configuration
   spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect
   spring.jpa.hibernate.ddl-auto=update
   spring.jpa.show-sql=true
   spring.jpa.properties.hibernate.format_sql=true
   ```

3. **Create Database**
   ```sql
   CREATE DATABASE ems_db;
   ```

4. **Build the project**
   ```bash
   ./mvnw clean package
   ```

5. **Run the application**
   ```bash
   ./mvnw spring-boot:run
   ```

   The API will be available at `http://localhost:8080`

## 📚 API Endpoints

### Employees
- `GET /api/employees` - Get all employees
- `GET /api/employees/{id}` - Get employee by ID
- `POST /api/employees` - Create new employee
- `PUT /api/employees/{id}` - Update employee
- `DELETE /api/employees/{id}` - Delete employee

### Departments
- `GET /api/departments` - Get all departments
- `GET /api/departments/{id}` - Get department by ID
- `POST /api/departments` - Create new department
- `PUT /api/departments/{id}` - Update department
- `DELETE /api/departments/{id}` - Delete department

## 📝 Example Requests

### Create Employee
```bash
POST /api/employees
Content-Type: application/json

{
  "firstName": "John",
  "lastName": "Doe",
  "email": "john.doe@example.com",
  "departmentId": 1
}
```

### Create Department
```bash
POST /api/departments
Content-Type: application/json

{
  "name": "Engineering",
  "description": "Software Engineering Team"
}
```

## 🧪 Testing

Run the test suite:
```bash
./mvnw test
```

## 📦 Database Schema

### Employee Table
```sql
CREATE TABLE employee (
  id BIGINT PRIMARY KEY AUTO_INCREMENT,
  first_name VARCHAR(100) NOT NULL,
  last_name VARCHAR(100) NOT NULL,
  email VARCHAR(100) UNIQUE NOT NULL,
  department_id BIGINT,
  FOREIGN KEY (department_id) REFERENCES department(id)
);
```

### Department Table
```sql
CREATE TABLE department (
  id BIGINT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(100) NOT NULL,
  description TEXT
);
```

## 🤝 Contributing

This is a portfolio project. Feel free to fork and submit pull requests for any improvements!

## 📄 License

This project is open source and available under the MIT License.

## 👨‍💻 Author

**Carlos Artiles**
- GitHub: [@CarlosJ0915](https://github.com/CarlosJ0915)
- Portfolio: [Your portfolio URL]

## 📞 Contact

For questions or feedback, feel free to reach out!

---

**Built with ❤️ as a learning project**
