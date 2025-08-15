# solid-principle
solid principle 

Here’s your content neatly decorated in **Markdown (.md)** format so you can directly save it as `OOPS_SOLID_Principles.md`:

---

````markdown
# OOPS Principles

## 1) Encapsulation  
## 2) Polymorphism  
## 3) Abstraction  
## 4) Inheritance  

---

# SOLID OOPS Principles

**S** => Single Responsibility  
**O** => Open Closed  
**L** => Liskov's Substitution  
**I** => Interface Segregation  
**D** => Dependency Inversion / Injection  

> The main aim of SOLID OOPS Principles is to make our code **more readable, maintainable, and loosely coupled**.

---

## S - Single Responsibility

> A class should have only one responsibility.

❌ **Not Recommended**
```java
class ReportGenerator {

    public void generateExcel() {
        // logic to generate excel
    }

    public void generatePdf() {
        // logic to generate pdf
    }
}
````

✅ **Recommended Approach**

```java
class ExcelReportGenerator {

    public void generateExcel() {
        // logic to generate excel
    }
}

class PdfReportGenerator {

    public void generatePdf() {
        // logic to generate pdf
    }
}
```

---

## O - Open Closed Principle

> Our code should be **open for extension** and **closed for modification**.

❌ **Not Recommended**

```java
public class LoanInterestCalculations {

    public double calculateLoanInterest(Loan loan) {

        if (loan instanceof CarLoan) {
            return loan.getValue() * 7.5;
        }

        if (loan instanceof PersonalLoan) {
            return loan.getValue() * 11.5;
        }
    }
}
```

> If we want to add another loan type, we would need to **modify** the above class — not recommended.

✅ **Recommended Approach**

```java
public class Loan {
    public double calculate(...) {
        // logic
    }
}

public class CarLoan extends Loan {
    public double calculate(...) {
        this.calculate() * 7.5;
    }
}

public class PersonalLoan extends Loan {
    public double calculate(...) {
        this.calculate() * 11.5;
    }
}
```

---

## L - Liskov's Substitution Principle

> If class **A** is a subtype of class **B**, we should be able to replace **B** with **A** without disturbing the behavior of our program.

❌ **Not Recommended**

```java
interface Car {
    void startEngine();
    void accelerate();
}

public class SwiftCar implements Car {
    private Engine eng;

    public void startEngine() {
        eng.start();
    }

    public void accelerate() {
        eng.powerOn();
    }
}

public class ElectricCar implements Car {
    public void startEngine() {
        throw new Exception("I don't have engine");
    }

    public void accelerate() {
        eng.powerOn();
    }
}
```

> The `ElectricCar` breaks substitution as it does not support `startEngine()`.

---

## I - Interface Segregation

> Don't force developers to implement unnecessary methods of an interface.
> Break larger interfaces into **smaller, specific** interfaces.

Example:
`javax.servlet.Servlet` has **5 methods**; if implemented, all must be overridden (even unused ones).
Spring's bean lifecycle uses **smaller interfaces**:

* `InitializingBean` → `afterPropertiesSet()`
* `DisposableBean` → `destroy()`

❌ **Not Recommended**

```java
interface ReportService {
    void excelReport();
    void pdfReport();
}
```

✅ **Recommended Approach**

```java
interface ExcelReportService {
    void excelReport();
}

interface PdfReportService {
    void pdfReport();
}
```

---

## D - Dependency Inversion

> Classes should not depend on **implementation classes** directly.
> Always **code to interfaces** and inject dependencies via **setter or constructor** for loose coupling.

❌ **Not Recommended (Tight Coupling)**

```java
public class Car {
    public void drive() {
        PetrolEngine eng = new PetrolEngine();
        eng.start();
        // drive
    }
}
```

✅ **Recommended Approach (Loose Coupling)**

```java
public class Car {
    private IEngine eng;

    public void setEng(IEngine eng) {
        this.eng = eng;
    }

    public void drive() {
        eng.start();
        // drive
    }
}
```

---

```

---

```

