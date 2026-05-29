# Project Development Guide

## Quick Start

### For Users
1. Clone the repository: `git clone https://github.com/ByteWithHassan/UBMS-Java.git`
2. Build with Maven: `mvn clean install`
3. Run the application: `mvn exec:java`

### For Developers
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/YourFeature`
3. Make your changes
4. Submit a pull request to `main` branch

---

## Project Overview

**UBMS-Java** is an educational project demonstrating Object-Oriented Programming (OOP) principles in Java with a Swing GUI application for managing utility bills.

### Tech Stack
- **Language**: Java 25
- **Build Tool**: Maven 4.0.0
- **UI Library**: FlatLaf 3.6
- **Storage**: File-based (Text files)
- **IDE**: NetBeans (recommended)

---

## Architecture

### Design Patterns

#### 1. Inheritance Hierarchy
```
User (Abstract)
├── Admin
└── Customer

Bill (Abstract)
├── ElectricityBill
├── WaterBill
└── GasBill
```

#### 2. Interface Implementation
```
Payable (Interface)
└── Implemented by Bill classes
```

#### 3. MVC-Inspired Pattern
- **Model**: User, Customer, Bill classes
- **View**: Form classes (loginform, AdminDashboard, etc.)
- **Controller**: Logic in Dashboard and Form classes

---

## File Structure

```
UBMS-Java/
├── src/
│   └── main/java/com/billsystem/
│       ├── Core Classes
│       │   ├── BillManagement.java (Entry point)
│       │   ├── User.java (Base class)
│       │   ├── Admin.java
│       │   └── Customer.java
│       ├── Bill System
│       │   ├── Bill.java (Abstract)
│       │   ├── Payable.java (Interface)
│       │   ├── ElectricityBill.java
│       │   ├── WaterBill.java
│       │   └── GasBill.java
│       ├── UI Components
│       │   ├── loginform.java
│       │   ├── AdminDashboard.java
│       │   ├── CustomerDashboard.java
│       │   ├── AddCustomerForm.java
│       │   └── GenerateBillForm.java
│       └── Utilities
│           └── FileManager.java
├── target/ (Build output)
├── pom.xml
├── README.md
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── SECURITY.md
├── CHANGELOG.md
├── LICENSE
├── .gitignore
├── customers.txt (Data file)
└── bills.txt (Data file)
```

---

## Development Workflow

### 1. Setup Development Environment

```bash
# Clone repository
git clone https://github.com/ByteWithHassan/UBMS-Java.git
cd UBMS-Java

# Add upstream remote
git remote add upstream https://github.com/ByteWithHassan/UBMS-Java.git

# Install dependencies
mvn clean install
```

### 2. Create Feature Branch

```bash
git checkout -b feature/add-feature-name
```

### 3. Make Changes

- Write code following standards
- Add tests if applicable
- Update documentation
- Commit regularly with clear messages

### 4. Test Your Changes

```bash
# Run tests
mvn test

# Build project
mvn clean install

# Test GUI manually
mvn exec:java
```

### 5. Push and Create PR

```bash
git push origin feature/add-feature-name
```

Then create a Pull Request on GitHub.

---

## Code Standards

### Naming Conventions

```java
// Classes: PascalCase
public class CustomerDashboard { }

// Methods: camelCase, verb-based
public void calculateBill() { }
public boolean validateInput() { }

// Constants: UPPER_SNAKE_CASE
private static final double ELECTRICITY_RATE = 15.0;

// Variables: camelCase
private String customerName;
private int billAmount;
```

### Code Structure

```java
public class ClassName {
    // Constants first
    private static final int CONSTANT = 100;
    
    // Static variables
    private static String staticVar;
    
    // Instance variables
    private String instanceVar;
    
    // Constructors
    public ClassName() { }
    
    // Public methods
    public void publicMethod() { }
    
    // Private methods
    private void privateMethod() { }
}
```

### Documentation

```java
/**
 * Calculates the utility bill amount.
 *
 * @param units Number of units consumed
 * @return Calculated bill amount
 * @throws IllegalArgumentException if units is negative
 */
public double calculateBill(int units) {
    // Implementation
}
```

---

## Common Tasks

### Adding a New Bill Type

1. **Create new class** extending `Bill`:
```java
public class InternetBill extends Bill {
    private static final double RATE = 500.0;
    
    @Override
    public double calculateBill() {
        return units * RATE;
    }
}
```

2. **Update FileManager** to handle new type
3. **Update UI forms** to include new option
4. **Add tests** for new class
5. **Update documentation**

### Adding a Feature

1. Create feature branch
2. Implement feature with tests
3. Update README if needed
4. Submit PR with description
5. Address review comments
6. Merge when approved

### Fixing a Bug

1. Create bugfix branch: `git checkout -b bugfix/bug-description`
2. Write test that reproduces bug
3. Fix the bug
4. Verify test passes
5. Commit with clear message: `fix: describe the fix`
6. Create PR

---

## Testing

### Running Tests

```bash
# Run all tests
mvn test

# Run specific test class
mvn test -Dtest=ClassName

# Run with coverage
mvn test jacoco:report
```

### Writing Tests

```java
import org.junit.Test;
import static org.junit.Assert.*;

public class BillTest {
    
    @Test
    public void testCalculateBill() {
        ElectricityBill bill = new ElectricityBill();
        bill.setUnits(100);
        assertEquals(1500.0, bill.calculateBill(), 0.01);
    }
    
    @Test(expected = IllegalArgumentException.class)
    public void testNegativeUnitsThrowException() {
        ElectricityBill bill = new ElectricityBill();
        bill.setUnits(-10);
    }
}
```

---

## Building & Deployment

### Build Commands

```bash
# Clean build
mvn clean

# Compile
mvn compile

# Package
mvn package

# Install
mvn install
```

### Running Application

```bash
# Using Maven
mvn exec:java

# Using JAR
java -jar target/Bill.Management-1.0-SNAPSHOT.jar

# Using IDE (NetBeans)
Right-click project → Run
```

---

## Troubleshooting

### Maven Issues

```bash
# Update dependencies
mvn dependency:resolve

# Check for conflicts
mvn dependency:tree

# Clear Maven cache
rm -rf ~/.m2/repository
```

### Build Failures

```bash
# Clean and rebuild
mvn clean install

# Skip tests
mvn clean install -DskipTests

# Verbose output
mvn clean install -X
```

### IDE Issues

**NetBeans:**
- File → Project Properties → Build
- Clean and Build project
- Restart IDE if needed

**IntelliJ:**
- File → Invalidate Caches
- Rebuild project
- Maven → Reload Projects

---

## Documentation

### Maintaining Docs

- Update README for user-facing changes
- Update CONTRIBUTING for process changes
- Update CHANGELOG with new features/fixes
- Add JavaDoc to new public methods
- Keep security policies updated

### Building Documentation

```bash
# Generate JavaDoc
mvn javadoc:javadoc

# Output location: target/site/apidocs/
```

---

## Release Process

### Version Bumping

Current: `1.0-SNAPSHOT`

For release:
1. Update version in `pom.xml`
2. Update `CHANGELOG.md`
3. Create git tag: `git tag v1.0.0`
4. Push changes and tags

---

## Resources

### Documentation
- [README.md](README.md) - Project overview
- [CONTRIBUTING.md](CONTRIBUTING.md) - Contributing guide
- [SECURITY.md](SECURITY.md) - Security policy
- [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) - Community standards

### External References
- [Java 25 Docs](https://docs.oracle.com/en/java/)
- [Maven Guide](https://maven.apache.org/guides/)
- [FlatLaf Project](https://www.formdev.com/flatlaf/)
- [GitHub Guides](https://guides.github.com/)

---

## Getting Help

### Issues
- Check existing issues first
- Provide detailed descriptions
- Include error messages and logs
- Provide steps to reproduce

### Discussions
- Ask questions
- Share ideas
- Discuss improvements
- Get feedback

### Code Review
- Ask for review in PR
- Respond to comments
- Update code as needed
- Thank reviewers

---

## Code of Conduct

Please read [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) before participating.

---

## License

This project is licensed under MIT License. See [LICENSE](LICENSE) for details.

---

**Happy Coding! 🚀**
