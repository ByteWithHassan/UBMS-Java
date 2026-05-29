# Utility Bill Management System (UBMS)

A comprehensive Java-based utility bill management application demonstrating Object-Oriented Programming (OOP) principles and best practices. This system manages customer records, calculates utility bills, and provides an intuitive GUI interface for seamless user interaction.

---

## 📋 Table of Contents

- [Features](#-features)
- [System Architecture](#-system-architecture)
- [Technologies & Dependencies](#-technologies--dependencies)
- [Project Structure](#-project-structure)
- [Installation & Setup](#-installation--setup)
- [Usage Guide](#-usage-guide)
- [Code Quality](#-code-quality)
- [Contributing](#-contributing)
- [License](#-license)
- [Author](#-author)

---

## 🚀 Features

- **Multi-User Support**: Admin and Customer role-based authentication
- **Customer Management**: Add, update, and manage customer records
- **Bill Generation**: Automated utility bill calculation for multiple bill types
- **Multiple Utility Types**: 
  - Electricity Bills
  - Water Bills
  - Gas Bills
- **Data Persistence**: File-based storage for customers and bills
- **User-Friendly GUI**: Menu-driven interface with FlatLaf modern look and feel
- **OOP Principles**: Demonstrates inheritance, polymorphism, and encapsulation

---

## 🏗 System Architecture

### Class Hierarchy

```
User (Abstract Base Class)
├── Admin
└── Customer

Bill (Abstract Base Class)
├── ElectricityBill
├── WaterBill
└── GasBill

Payable (Interface)
└── Implemented by Bill classes
```

### Key Components

| Class | Purpose |
|-------|---------|
| `BillManagement` | Application entry point |
| `loginform` | User authentication interface |
| `AdminDashboard` | Admin operations panel |
| `CustomerDashboard` | Customer operations panel |
| `AddCustomerForm` | Customer registration form |
| `GenerateBillForm` | Bill generation interface |
| `FileManager` | File I/O operations |
| `Customer` | Customer data model |
| `Bill` | Base bill class |

---

## 🛠 Technologies & Dependencies

| Component | Version |
|-----------|---------|
| **Java** | 25 |
| **Build Tool** | Maven 4.0.0 |
| **FlatLaf** | 3.6 (Modern UI Theme) |
| **Packaging** | JAR |

### Dependencies

```xml
<dependency>
    <groupId>com.formdev</groupId>
    <artifactId>flatlaf</artifactId>
    <version>3.6</version>
</dependency>
```

---

## 📂 Project Structure

```
UBMS-Java/
├── src/
│   └── main/
│       └── java/
│           └── com/
│               └── billsystem/
│                   ├── BillManagement.java          (Entry Point)
│                   ├── loginform.java               (Authentication)
│                   ├── Admin.java                   (Admin Model)
│                   ├── User.java                    (Base User)
│                   ├── Customer.java                (Customer Model)
│                   ├── Bill.java                    (Abstract Bill Base)
│                   ├── ElectricityBill.java         (Electricity Implementation)
│                   ├── WaterBill.java               (Water Implementation)
│                   ├── GasBill.java                 (Gas Implementation)
│                   ├── Payable.java                 (Interface)
│                   ├── AdminDashboard.java          (Admin UI)
│                   ├── CustomerDashboard.java       (Customer UI)
│                   ├── AddCustomerForm.java         (Registration UI)
│                   ├── GenerateBillForm.java        (Bill UI)
│                   ├── FileManager.java             (Data Persistence)
│                   └── *.form                       (NetBeans Form Files)
├── pom.xml                                          (Maven Configuration)
├── README.md                                        (This File)
├── CONTRIBUTING.md                                  (Contribution Guide)
├── CODE_OF_CONDUCT.md                              (Community Standards)
├── customers.txt                                    (Customer Data)
├── bills.txt                                        (Bill Data)
└── .gitignore                                       (Git Ignore Rules)
```

---

## ⚙️ Installation & Setup

### Prerequisites

- **Java Development Kit (JDK)**: Version 25 or higher
- **Maven**: Version 3.6.0 or higher
- **Git**: For cloning the repository

### Step 1: Clone the Repository

```bash
git clone https://github.com/ByteWithHassan/UBMS-Java.git
cd UBMS-Java
```

### Step 2: Build the Project

```bash
mvn clean install
```

### Step 3: Run the Application

**Option A - Using Maven:**
```bash
mvn exec:java
```

**Option B - Using NetBeans IDE:**
1. Open NetBeans
2. File → Open Project → Select UBMS-Java folder
3. Right-click project → Build
4. Right-click project → Run

**Option C - Execute JAR:**
```bash
java -jar target/Bill.Management-1.0-SNAPSHOT.jar
```

---

## 📖 Usage Guide

### Login

1. Launch the application
2. Select user role: **Admin** or **Customer**
3. Enter credentials (default credentials in system)

### Admin Functions

- **Add Customer**: Register new customer accounts
- **Generate Bill**: Calculate and save utility bills
- **View Records**: Access customer and bill information
- **Manage Data**: Handle customer and bill database

### Customer Functions

- **View Bill**: Check personal utility bills
- **View Profile**: Access account information
- **Logout**: Exit the system securely

### Sample Login Credentials

```
Admin Panel:
- Username: admin
- Password: admin123

Customer Panel:
- Username: customer
- Password: customer123
```

---

## 🎯 OOP Concepts Demonstrated

### 1. **Inheritance**
```java
public abstract class Bill implements Payable {
    // Base implementation
}

public class ElectricityBill extends Bill {
    // Specific implementation
}
```

### 2. **Polymorphism**
```java
Bill bill = new ElectricityBill();
double amount = bill.calculateBill();
```

### 3. **Encapsulation**
```java
private String customerId;
public String getCustomerId() { return customerId; }
public void setCustomerId(String id) { this.customerId = id; }
```

### 4. **Abstraction**
```java
public abstract double calculateBill();
```

### 5. **Interfaces**
```java
public interface Payable {
    double calculateBill();
}
```

---

## 💻 Code Quality

### Naming Conventions

- **Classes**: PascalCase (e.g., `AdminDashboard`)
- **Methods**: camelCase (e.g., `calculateBill()`)
- **Constants**: UPPER_SNAKE_CASE (e.g., `MAX_BILL_AMOUNT`)
- **Variables**: camelCase (e.g., `customerName`)

### Code Standards

- **Indentation**: 4 spaces
- **Line Length**: Maximum 100 characters
- **Comments**: JavaDoc for public methods
- **Error Handling**: Try-catch blocks for file operations

### Best Practices

✅ Follows OOP principles  
✅ Proper encapsulation with getters/setters  
✅ Maven build automation  
✅ Modular class design  
✅ File-based data persistence  

---

## 🤝 Contributing

Contributions are welcome! To contribute to this project:

### Guidelines

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** changes (`git commit -m 'Add AmazingFeature'`)
4. **Push** to branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Code Standards

- Follow the existing code style
- Add JavaDoc comments for new methods
- Test your changes before submitting
- Write clear, descriptive commit messages
- Reference any related issues in PR description

For detailed contribution guidelines, see [CONTRIBUTING.md](CONTRIBUTING.md)

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

MIT License Summary:
- ✅ Commercial use permitted
- ✅ Distribution allowed
- ✅ Modification allowed
- ✅ Private use allowed
- ❌ Liability not accepted
- ❌ Warranty not provided

---

## 📞 Support & Questions

- **Report Bugs**: [Open an Issue](https://github.com/ByteWithHassan/UBMS-Java/issues)
- **Request Features**: [Discussion Tab](https://github.com/ByteWithHassan/UBMS-Java/discussions)
- **Email**: Contact repository owner for direct support

---

## 👤 Author

**ByteWithHassan**

- GitHub: [@ByteWithHassan](https://github.com/ByteWithHassan)
- Repository: [UBMS-Java](https://github.com/ByteWithHassan/UBMS-Java)

---

## 🙏 Acknowledgments

- FlatLaf team for the modern UI library
- Java community for excellent documentation
- Contributors and testers

---

## 📊 Project Statistics

- **Language**: 100% Java
- **Build System**: Maven
- **Architecture**: MVC-inspired GUI application
- **Data Storage**: File-based (TXT)

---

## 🔄 Version History

### v1.0-SNAPSHOT
- Initial release
- Core functionality implemented
- Admin and Customer roles
- Multi-utility bill support
- File-based persistence

---

## 🎓 Learning Outcomes

By studying this project, you will learn:

1. **OOP Principles** - Inheritance, polymorphism, encapsulation, abstraction
2. **Java GUI Development** - Swing components with FlatLaf
3. **File I/O Operations** - Reading and writing data persistence
4. **Maven Build System** - Project configuration and dependency management
5. **Software Architecture** - Modular and maintainable code design
6. **Best Practices** - Professional coding standards and conventions

---

## 📝 Notes

- Data is stored in `customers.txt` and `bills.txt` in the project root
- Ensure proper file permissions for data file access
- Default admin credentials should be changed in production
- Application requires GUI environment (not suitable for headless servers)

---

**Last Updated**: May 2026  
**Status**: Active Development
