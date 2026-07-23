# Real-Time Scenario

Suppose a developer creates an online banking application.

```java
public class Account {
    public static void main(String[] args) {
        System.out.println("Bank Application");
    }
}
```

The developer gives the **source code** to the DevOps engineer.

Now the DevOps engineer uses Maven to build the application.

```text
Developer
      │
      ▼
Java Source Code (.java)
      │
      ▼
Maven Build
      │
      ▼
Deploy Application
```

---

# 1. Validate

## What is Validate?

The **validate** phase checks whether the project structure and required files are correct before starting the build.

It **does not check whether your Java code is logically correct**.

It checks things like:

* Is `pom.xml` present?
* Is the project structure valid?
* Are mandatory configurations available?

### Example

Project structure:

```text
BankApp/
│
├── pom.xml
├── src/
└── target/
```

If `pom.xml` is missing:

```text
Build Failed

Reason:
pom.xml not found
```

Maven stops immediately.

### Real-Time Analogy

Imagine you are traveling by flight.

Before boarding:

* Do you have your ticket?
* Do you have your passport?
* Is your baggage checked?

Only after validation can you board.

Similarly, Maven first validates the project before building.

---

# 2. Compile

## What is Compile?

Developers write Java source code.

Example:

```java
public class Demo{
    public static void main(String args[]){
        System.out.println("Hello");
    }
}
```

Humans can read this code.

The computer **cannot execute `.java` files directly**.

So Maven calls the Java compiler (`javac`).

The compiler converts:

```text
.java
```

into

```text
.class
```

### Why?

* `.java` = Human-readable source code
* `.class` = Java **bytecode**, which the JVM can understand and execute.

### Flow

```text
Developer

↓

Demo.java

↓

javac

↓

Demo.class
```

### Real-Time Analogy

Think of English and French.

You speak English.

A French person cannot understand it.

A translator converts:

```text
English

↓

Translator

↓

French
```

Similarly:

```text
Java Source Code

↓

Compiler

↓

Bytecode (.class)
```

The compiler acts as a translator.

---

# 3. Test

## What is Test?

After compilation, Maven runs **unit tests** (typically using JUnit or TestNG).

The goal is to ensure the application behaves correctly.

Example:

```text
Calculator

2 + 3 = 5

Test Passed
```

Another example:

```text
Login

Username

Password

Login Successful

Test Passed
```

If any test fails:

```text
Build Failed
```

### Real-Time Example

Suppose your application has 200 unit tests.

Maven runs:

```text
Test 1

Passed

Test 2

Passed

...

Test 200

Passed
```

Only if all required tests pass does the build continue.

---

# 4. Package

## What is Package?

After successful compilation and testing, Maven packages the application into a distributable format.

Examples include:

* JAR
* WAR
* EAR

### Flow

```text
Demo.class

Account.class

Login.class

↓

Package

↓

BankApp.jar
```

Instead of sending hundreds of `.class` files, Maven bundles them into a single archive.

### Real-Time Analogy

Imagine you are moving to another city.

Instead of carrying:

* Clothes
* Books
* Shoes
* Laptop

one by one,

you pack everything into **one suitcase**.

Similarly:

```text
Many Class Files

↓

Package

↓

One JAR File
```

---

# 5. Verify

## What is Verify?

After packaging, Maven performs additional quality checks.

Examples:

* Is the JAR created successfully?
* Did all tests pass?
* Does the artifact meet quality rules?
* Are integration checks successful?

Think of it as a final inspection before delivery.

### Example

```text
BankApp.jar

↓

Verification

↓

Passed
```

---

# 6. Install

## What is Install?

The **install** phase copies the built artifact to your **local Maven repository**.

Local repository location:

```text
Windows

C:\Users\<username>\.m2\repository
```

### Why?

Other local projects can reuse this JAR without downloading it again.

### Flow

```text
BankApp.jar

↓

Install

↓

.m2/repository
```

### Real-Time Example

You build a common library:

```text
CommonUtils.jar
```

After `mvn install`, another project on your machine can use it directly from the local repository.

---

# 7. Deploy

## What is Deploy?

The **deploy** phase uploads the packaged artifact to a **remote repository** such as:

* Nexus Repository
* JFrog Artifactory
* AWS CodeArtifact

### Flow

```text
Developer

↓

Build

↓

BankApp.jar

↓

Nexus Repository

↓

Other Teams Download
```

### Why?

Now other developers, QA, or deployment pipelines can access the same artifact.

---

# Complete Maven Lifecycle Flow

```text
Developer writes Java code (.java)

                │
                ▼
         Validate
(Check project structure and pom.xml)

                │
                ▼
          Compile
(Convert .java → .class)

                │
                ▼
            Test
(Run unit tests)

                │
                ▼
          Package
(Create JAR/WAR)

                │
                ▼
           Verify
(Check build quality)

                │
                ▼
           Install
(Store artifact in local .m2 repository)

                │
                ▼
            Deploy
(Upload artifact to Nexus/Artifactory)
```

---

# Where Does a DevOps Engineer Use These?

A Jenkins pipeline typically invokes Maven like this:

```groovy
stage('Build') {
    steps {
        sh 'mvn clean install'
    }
}
```

When `mvn clean install` runs, Maven automatically executes these phases in order:

```text
Validate
    ↓
Compile
    ↓
Test
    ↓
Package
    ↓
Verify
    ↓
Install
```

If your pipeline uses:

```bash
mvn clean deploy
```

then Maven executes:

```text
Validate
    ↓
Compile
    ↓
Test
    ↓
Package
    ↓
Verify
    ↓
Install
    ↓
Deploy
```
