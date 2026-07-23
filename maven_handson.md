
# 🎓 SESSION PLAN

## 📚 Topics Covered

* Build Automation (Ant vs Maven)
* What is Maven
* Running Test Cases using Maven

---

# 🧭 PART 1: Build Automation Basics (20 mins)

## 🎯 Step 1: Start with a Problem

👨‍🏫 Say:

> “You wrote Java code. Now how do you run it?”

## 🧑‍🏫 Board Work

```
Code → Compile → Test → Package → Run
```

---

## 💡 Explain

👉 Without tools:

* javac manually
* Download JARs manually
* Run tests manually

👉 Ask:
❓ “Is this efficient?”

---

## 🎯 Step 2: Introduce Automation

👨‍🏫 Say:

> “We use tools to automate all these steps”

---

## 🔁  Ant vs Maven


```
ANT            MAVEN
Manual         Automated
build.xml      pom.xml
No lifecycle   Lifecycle
```

---

## 🎯 Mini Task (Student Interaction)

👉 Ask students:

* “Which one is better for large projects?”

✔ Expected: Maven

---

# 🧭 PART 2: What is Maven (30 mins)

## 🎯 Step 1: Definition

👨‍🏫 Say:

> “Maven is a build automation tool that manages dependencies and project lifecycle.”

---

## 🧑‍🏫 Board Work

```
pom.xml = Project Info + Dependencies + Build
```

---

## 🎯 Step 2: Maven Lifecycle

### Write:

```
Validate → Compile → Test → Package → Install → Deploy
```

---

## 💡 Explain Like Story

* Validate → check project
* Compile → convert code
* Test → run test cases
* Package → create JAR

---

## 🎯 Step 3: Show Command

```bash
mvn clean install
```

👉 Explain:

* Runs everything automatically

---

# 🧪 HANDS-ON LAB 1 (Maven Setup – 20 mins)

## 🎯 Task: Create and Run Maven Project

### Step 1: Create Project

```bash
mvn archetype:generate
```

👉 Choose default options

---

### Step 2: Go to project

```bash
cd your-project
```

---

### Step 3: Build Project

```bash
mvn compile
```

---

### Step 4: Package Project

```bash
mvn package
```

👉 Show:
📁 `target/` folder
📦 `.jar` file

---

## 🎯 Student Task

✔ Ask them:

* Run `mvn compile`
* Run `mvn package`
* Identify generated file

---

# 🧭 PART 3: Running Test Cases (30 mins)

## 🎯 Step 1: Explain Testing

👨‍🏫 Say:

> “Testing ensures our code works correctly.”

---

## 🧪 Example

```
2 + 3 = 5 ✅
```

---

## 🎯 Step 2: Add JUnit Dependency

```xml
<dependency>
  <groupId>junit</groupId>
  <artifactId>junit</artifactId>
  <version>4.13.2</version>
  <scope>test</scope>
</dependency>
```

---

## 🎯 Step 3: Create Test File

📄 `AppTest.java`

```java
import org.junit.Test;
import static org.junit.Assert.*;

public class AppTest {

    @Test
    public void testAddition() {
        int result = 2 + 3;
        assertEquals(5, result);
    }
}
```

---

## 🎯 Step 4: Run Test

```bash
mvn test
```

---

## 🧠 Explain Output

* ✔ BUILD SUCCESS → test passed
* ❌ BUILD FAILURE → test failed

---

# 🧪 HANDS-ON LAB 2 (Testing – 20 mins)

## 🎯 Task: Break the Test

👉 Ask students to change:

```java
assertEquals(6, result);
```

---

## ▶️ Run Again

```bash
mvn test
```

---

## 🎯 Observe

👉 Output:
❌ BUILD FAILURE

---

## 💡 Learning Outcome

👉 “Maven stops build if test fails”

---

# 🧭 PART 4: Real Industry Connection (10 mins)

## 🧑‍🏫 Board Work

```
Developer → Git → Jenkins → Maven → Test → Deploy
```

---

## 💡 Explain

* Code pushed to Git
* CI tool runs Maven
* Tests run automatically
* Deployment happens only if success

---

# 🎯 FINAL CLASS ACTIVITY (10 mins)

## Ask Students:

1. What is Maven?
2. What is pom.xml?
3. What does `mvn test` do?
4. What happens if test fails?

---

# 🏁 FINAL SUMMARY 

```
✔ Build Automation saves time
✔ Ant = Manual
✔ Maven = Automated
✔ pom.xml = Project config
✔ mvn test = Runs tests
✔ Test failure stops build
```

---

# 🎁 BONUS HOMEWORK

👉 Give students:

1. Add new test case
2. Add new dependency
3. Run `mvn clean install`
4. Observe output

---
s + answers for this topic**
