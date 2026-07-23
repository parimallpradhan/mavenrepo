# 🎓 Session Plan: Maven End-to-End (Linux + Concepts + Hands-on)

---

# 🟢 1. Install Maven on Linux (Hands-on)


👉 “Maven is a build automation tool used to compile, test, and package Java applications.”

---

## 🧪 Install Steps (Amazon Linux / Ubuntu)

### 🔹 Step 1: Install Java 21

```bash
sudo yum install java-21-amazon-corretto -y   # Amazon Linux
```

OR

```bash
sudo apt install openjdk-21-jdk -y            # Ubuntu
```

---

### 🔹 Step 2: Install Maven

```bash
sudo yum install maven -y
```

OR

```bash
sudo apt install maven -y
```

---

### 🔹 Step 3: Verify

```bash
mvn -version
```

👉 Output should show:

* Java: 21
* Maven version

---

## 🎯 👉 “Java is required to run Maven, and Maven is used to build Java projects.”

---

# 🟡 2. What is `pom.xml` (Core Concept)


👉 “`pom.xml` is the heart of a Maven project. It contains project configuration.”

---

## 🧾 Basic Structure

```xml
<project>
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.company</groupId>
    <artifactId>my-app</artifactId>
    <version>1.0</version>

    <dependencies>
        <!-- external libraries -->
    </dependencies>
</project>
```

---


* **groupId** → Company/project group
* **artifactId** → Project name
* **version** → Version of app

---


👉 “If Maven is engine, pom.xml is the brain controlling everything.”

---

# 📦 3. JAR vs WAR vs EAR (Quick Revision)

## 🟡 JAR (Java App)


👉 Standalone app → run using:

```bash
java -jar app.jar
```

---

## 🔵 WAR (Web App)

👉 Deploy on:

* Apache Tomcat

---

## 🔴 EAR (Enterprise App)


👉 Deploy on:

* WebLogic Server
* WebSphere Application Server

---

## 🎯 Teaching Line

👉 “JAR = Java app, WAR = Web app, EAR = Enterprise system.”

---

# 🏢 4. Types of Maven Repository

## 📌 Explain 3 Types

### 1️⃣ Local Repository

```bash
~/.m2/repository
```

👉 Stored on developer machine

---

### 2️⃣ Central Repository

👉 Default remote repo
👉 Download dependencies from internet

---

### 3️⃣ Remote Repository (Private)

👉 Example:

* Nexus
* Artifactory

---

👉 “Maven first checks local → then central → then remote.”

---

# 🔁 5. Maven Lifecycle (VERY IMPORTANT)

## 📌 Explain Flow


---

## 🔥 Lifecycle Phases + Commands

### 1️⃣ Clean Lifecycle

```bash
mvn clean
```

👉 Deletes old build

---

### 2️⃣ Default Lifecycle

```bash
mvn compile
```

👉 Compiles code

```bash
mvn test
```

👉 Runs test cases

```bash
mvn package
```

👉 Creates JAR/WAR

```bash
mvn install
```

👉 Stores in local repo

```bash
mvn deploy
```

👉 Uploads to remote repo

---


👉 “When you run `mvn package`, Maven automatically runs compile + test + package.”

---

# 🧪 6. Hands-on Lab (MOST IMPORTANT)

---

## 🟡 Create JAR Project

```bash
mvn archetype:generate \
-DgroupId=com.demo \
-DartifactId=jar-demo \
-DarchetypeArtifactId=maven-archetype-quickstart \
-DinteractiveMode=false
```

```bash
cd jar-demo
mvn clean package
```

👉 Output:

```bash
target/jar-demo.jar
```

Run:

```bash
java -jar target/jar-demo.jar
```

---

## 🔵 Create WAR Project

```bash
mvn archetype:generate \
-DgroupId=com.demo \
-DartifactId=war-demo \
-DarchetypeArtifactId=maven-archetype-webapp \
-DinteractiveMode=false
```

```bash
cd war-demo
mvn clean package
```

👉 Output:

```bash
target/war-demo.war
```

Deploy to Apache Tomcat

---

# 💼 7. Real-Time Use Case 

## 🧑‍💻 Scenario: Developer Workflow

👉 “Developer writes code → pushes to Git → Jenkins runs:”

```bash
mvn clean package
```

👉 Output:

* JAR → deployed as microservice
* WAR → deployed on Tomcat

---

## 🏢 Enterprise Flow

```bash
mvn clean install
```

👉 Stores artifact in local repo

```bash
mvn deploy
```

👉 Upload to Nexus/Artifactory

---

## 🎯 Teaching Line

👉 “Maven is used in CI/CD pipelines to automate build and deployment.”

---

# 🚀 8. Quick Recap

Ask:

* What is pom.xml?
* Difference between JAR & WAR?
* What does `mvn install` do?
* Where dependencies are stored?

---



👉 Show this LIVE:

```bash
ls ~/.m2/repository
```

👉 Show dependency download:

```bash
mvn compile
```

---

# ✅ Final Teaching Flow (Time Split)

| Topic        | Time      |
| ------------ | --------- |
| Installation | 15 min    |
| pom.xml      | 15 min    |
| JAR/WAR/EAR  | 15 min    |
| Repository   | 10 min    |
| Lifecycle    | 20 min    |
| Hands-on     | 30–40 min |

---


