# Contributing to UBMS-Java

Thank you for your interest in contributing to the Utility Bill Management System (UBMS-Java)! This document provides guidelines and instructions for contributing to this project.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [Making Changes](#making-changes)
- [Commit Guidelines](#commit-guidelines)
- [Pull Request Process](#pull-request-process)
- [Coding Standards](#coding-standards)
- [Testing](#testing)
- [Documentation](#documentation)
- [Questions & Support](#questions--support)

---

## Code of Conduct

We are committed to providing a welcoming and inclusive environment for all contributors. Please be respectful and constructive in all interactions.

### Expected Behavior

- Use inclusive language
- Be respectful of differing opinions and approaches
- Accept constructive criticism gracefully
- Focus on what is best for the community
- Show empathy towards other community members

### Unacceptable Behavior

- Harassment, discrimination, or bullying of any kind
- Offensive comments, language, or imagery
- Trolling or derogatory comments
- Personal attacks on maintainers or contributors

---

## Getting Started

### Prerequisites

Before you begin contributing, ensure you have:

- **Java Development Kit (JDK)** 25 or higher
- **Maven** 3.6.0 or higher
- **Git** for version control
- **IDE** (NetBeans, IntelliJ IDEA, or Eclipse recommended)

### Fork & Clone

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/YOUR-USERNAME/UBMS-Java.git
   cd UBMS-Java
   ```
3. **Add upstream remote** to keep your fork synchronized:
   ```bash
   git remote add upstream https://github.com/ByteWithHassan/UBMS-Java.git
   ```

---

## Development Setup

### Step 1: Build the Project

```bash
mvn clean install
```

### Step 2: Create a Feature Branch

```bash
git checkout -b feature/YourFeatureName
```

**Branch naming conventions:**
- `feature/add-something` - New features
- `bugfix/fix-something` - Bug fixes
- `docs/update-something` - Documentation updates
- `refactor/improve-something` - Code refactoring
- `test/add-tests` - Test additions

### Step 3: Set Up Your IDE

**NetBeans:**
1. File → Open Project → Select UBMS-Java folder
2. IDE automatically recognizes Maven project

**IntelliJ IDEA:**
1. Open → Select UBMS-Java folder
2. Import Maven project when prompted

**Eclipse:**
1. File → Import → Existing Maven Projects
2. Select UBMS-Java folder

---

## Making Changes

### Code Style Guide

We follow Java conventions and best practices:

#### Naming Conventions
```java
// Classes: PascalCase
public class CustomerDashboard { }

// Methods: camelCase
public void addCustomer() { }

// Constants: UPPER_SNAKE_CASE
private static final int MAX_BILLS = 100;

// Variables: camelCase
private String customerName;
```

#### Indentation & Formatting
- **Indentation**: 4 spaces (no tabs)
- **Line Length**: Maximum 100 characters
- **Braces**: Opening brace on same line (Java style)

```java
public void calculateBill() {
    if (amount > 0) {
        total += amount;
    }
}
```

#### Comments & JavaDoc
```java
/**
 * Calculates the utility bill based on units consumed.
 *
 * @param units The number of units consumed
 * @return The calculated bill amount
 * @throws IllegalArgumentException if units is negative
 */
public double calculateBill(int units) {
    if (units < 0) {
        throw new IllegalArgumentException("Units cannot be negative");
    }
    return units * RATE;
}
```

### OOP Principles

Maintain the existing architecture:

```java
// Use interfaces for contracts
public interface Payable {
    double calculateBill();
}

// Use abstract classes for shared functionality
public abstract class Bill implements Payable {
    protected String billId;
    
    public abstract double calculateBill();
}

// Implement for specific types
public class ElectricityBill extends Bill {
    @Override
    public double calculateBill() {
        // Implementation
    }
}
```

---

## Commit Guidelines

### Commit Message Format

Use clear, descriptive commit messages following the format:

```
<type>: <subject>

<body>

<footer>
```

### Types

- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation changes
- `style:` - Code style changes (formatting, missing semicolons, etc.)
- `refactor:` - Code refactoring without feature changes
- `test:` - Adding or updating tests
- `chore:` - Maintenance tasks (dependencies, build config, etc.)

### Subject Line

- Keep it under 50 characters
- Use imperative mood ("add" not "added" or "adds")
- Don't capitalize first letter
- No period at the end

### Body (Optional)

- Explain what and why, not how
- Wrap at 72 characters
- Use bullet points for multiple changes

### Examples

```
feat: add water bill calculation

- Implement WaterBill class extending Bill
- Add unit rate constant for water
- Calculate bill based on units consumed

Closes #42
```

```
fix: prevent negative bill amounts

Users could input negative values leading to incorrect calculations.
Now validates input before processing.
```

```
docs: improve README installation section

Added step-by-step Maven build instructions and JAR execution examples.
```

---

## Pull Request Process

### Before Creating a PR

1. **Update your branch** with latest upstream changes:
   ```bash
   git fetch upstream
   git rebase upstream/main
   ```

2. **Test your changes**:
   ```bash
   mvn clean test
   mvn clean install
   ```

3. **Verify code quality**:
   - Follow coding standards
   - Add/update comments
   - No console errors or warnings

### Creating a Pull Request

1. **Push your feature branch**:
   ```bash
   git push origin feature/YourFeatureName
   ```

2. **Create PR on GitHub** with:
   - Clear, descriptive title
   - Detailed description of changes
   - Reference related issues: `Closes #42`
   - Screenshots (if UI changes)

3. **PR Template**:
   ```markdown
   ## Description
   Brief description of changes

   ## Type of Change
   - [ ] Bug fix
   - [ ] New feature
   - [ ] Documentation update
   - [ ] Other (please describe)

   ## Related Issues
   Closes #42

   ## Testing
   Describe how you tested changes

   ## Screenshots
   If applicable, add screenshots

   ## Checklist
   - [ ] Code follows style guidelines
   - [ ] Self-reviewed my code
   - [ ] Added comments/JavaDoc
   - [ ] Updated README if needed
   - [ ] Changes generate no new warnings
   ```

### PR Review Process

- Maintainers will review your PR
- Address any requested changes
- Re-request review after updates
- PRs are merged once approved

---

## Coding Standards

### File Organization

```
src/main/java/com/billsystem/
├── BillManagement.java      (Main entry point)
├── User.java                (Base class)
├── Admin.java               (Admin model)
├── Customer.java            (Customer model)
├── Bill.java                (Abstract bill)
├── ElectricityBill.java     (Electricity implementation)
├── WaterBill.java           (Water implementation)
├── GasBill.java             (Gas implementation)
├── Payable.java             (Interface)
├── FileManager.java         (File I/O)
├── loginform.java           (Login UI)
├── AdminDashboard.java      (Admin UI)
├── CustomerDashboard.java   (Customer UI)
├── AddCustomerForm.java     (Add customer UI)
└── GenerateBillForm.java    (Generate bill UI)
```

### Error Handling

```java
try {
    fileManager.saveCustomer(customer);
} catch (IOException e) {
    logger.error("Failed to save customer: " + customer.getId(), e);
    showErrorDialog("Error saving customer: " + e.getMessage());
}
```

### Avoid

- Hard-coded values (use constants)
- Null pointer dereferences (use Objects.requireNonNull())
- Catch generic Exception
- Unused imports
- Code duplication

---

## Testing

### Unit Tests

Create test files in `src/test/java/com/billsystem/`:

```java
import org.junit.Test;
import static org.junit.Assert.*;

public class ElectricityBillTest {
    
    @Test
    public void testCalculateBill() {
        ElectricityBill bill = new ElectricityBill();
        bill.setUnits(100);
        assertEquals(1500.0, bill.calculateBill(), 0.01);
    }
    
    @Test
    public void testNegativeUnitsThrowException() {
        ElectricityBill bill = new ElectricityBill();
        assertThrows(IllegalArgumentException.class, () -> {
            bill.setUnits(-10);
        });
    }
}
```

### Running Tests

```bash
mvn test
```

---

## Documentation

### README Updates

Update README.md if you:
- Add new features
- Change installation steps
- Modify configuration
- Add new dependencies

### JavaDoc Comments

Add JavaDoc for all public classes and methods:

```java
/**
 * Represents an electricity bill for a customer.
 * Calculates bill amount based on unit consumption.
 */
public class ElectricityBill extends Bill {
    
    /**
     * Calculates the electricity bill.
     *
     * @return calculated bill amount in currency
     */
    @Override
    public double calculateBill() {
        // Implementation
    }
}
```

### Code Comments

Add comments for complex logic:

```java
// Algorithm: Calculate average consumption over past 3 months
double avgConsumption = (month1 + month2 + month3) / 3.0;
```

---

## Questions & Support

### Getting Help

- **GitHub Issues**: For bug reports and feature requests
- **GitHub Discussions**: For questions and discussions
- **Email**: Contact repository owner for direct support

### Reporting Bugs

Provide:
- Clear description of the bug
- Steps to reproduce
- Expected vs actual behavior
- Java version and OS
- Error logs or stack traces

**Example:**
```
Title: Negative bill amount calculation bug

Description:
When entering negative units, the bill calculation returns negative amounts
instead of throwing an error.

Steps:
1. Open GenerateBillForm
2. Enter -10 in units field
3. Click Calculate Bill
4. See negative bill amount

Expected: Error message or validation error
Actual: Bill shows -1500.00

System: Java 25, Windows 11
```

---

## Review Checklist for Maintainers

- [ ] Code follows style guidelines
- [ ] Tests added/updated
- [ ] Documentation updated
- [ ] No breaking changes
- [ ] Commits are well-documented
- [ ] PR description is clear
- [ ] All discussions addressed

---

## Additional Resources

- [Java Style Guide](https://google.github.io/styleguide/javaguide.html)
- [Maven Documentation](https://maven.apache.org/guides/)
- [Git Workflow](https://guides.github.com/introduction/flow/)
- [Semantic Versioning](https://semver.org/)

---

## Recognition

Contributors will be recognized in:
- Project README contributors section
- Release notes for major contributions
- GitHub contributors page

---

Thank you for contributing to UBMS-Java! Your efforts help make this project better. 🙌

**Happy Coding!**
