# 🧪 Prerequisites 

```bash
java -version
mvn -version
```

👉 Expected:

* Java → **21**
* Maven → **3.8+**

---

# 🟡 PART 1: Create JAR (Java 21 – Modern Way)

## 📁 Step 1: Generate Project

```bash
mvn archetype:generate \
-DgroupId=com.example \
-DartifactId=jar-demo \
-DarchetypeArtifactId=maven-archetype-quickstart \
-DinteractiveMode=false
```

```bash
cd jar-demo
```

---

## ✏️ Step 2: Update Java Code (Java 21 style)

Edit:

```bash
src/main/java/com/example/App.java
```

```java
public class App {
    public static void main(String[] args) {
        System.out.println("Hello from JAR using Java 21 🚀");
    }
}
```

---

## ⚙️ Step 3: Update `pom.xml` (VERY IMPORTANT for Java 21)

Add this:

```xml
<properties>
    <maven.compiler.release>21</maven.compiler.release>
</properties>
```

👉 This ensures compatibility with Java 21.

---

## ⚙️ Step 4: Make Executable JAR

Add plugin:

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-jar-plugin</artifactId>
            <version>3.3.0</version>
            <configuration>
                <archive>
                    <manifest>
                        <mainClass>com.example.App</mainClass>
                    </manifest>
                </archive>
            </configuration>
        </plugin>
    </plugins>
</build>
```

---

## 🏗️ Step 5: Build

```bash
mvn clean package
```

👉 Output:

```bash
target/jar-demo-1.0-SNAPSHOT.jar
```

---

## ▶️ Step 6: Run

```bash
java -jar target/jar-demo-1.0-SNAPSHOT.jar
```

👉 Output:

```
Hello from JAR using Java 21 🚀
```

---

# 🔵 PART 2: Create WAR (Java 21 Compatible Web App)

## 📁 Step 1: Generate Web Project

```bash
mvn archetype:generate \
-DgroupId=com.example \
-DartifactId=war-demo \
-DarchetypeArtifactId=maven-archetype-webapp \
-DinteractiveMode=false
```

```bash
cd war-demo
```

---

## ⚠️ IMPORTANT NOTE (TEACH THIS)

👉 Default web archetype is **OLD (Servlet 2.x)**
👉 We must upgrade to **Jakarta EE (Java 21 compatible)**

---

## ⚙️ Step 2: Update `pom.xml`

### 🔹 Change packaging:

```xml
<packaging>war</packaging>
```

---

### 🔹 Add Java 21:

```xml
<properties>
    <maven.compiler.release>21</maven.compiler.release>
</properties>
```

---

### 🔹 Add Modern Servlet Dependency (Jakarta)

```xml
<dependencies>
    <dependency>
        <groupId>jakarta.servlet</groupId>
        <artifactId>jakarta.servlet-api</artifactId>
        <version>6.0.0</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```

---

### 🔹 Add WAR Plugin (Fix for Java 21)

```xml
<build>
    <finalName>war-demo</finalName>
    <plugins>
        <plugin>
            <artifactId>maven-war-plugin</artifactId>
            <version>3.4.0</version>
        </plugin>
    </plugins>
</build>
```

---

## ✏️ Step 3: Create Simple Servlet

Create file:

```bash
src/main/java/com/example/HelloServlet.java
```

```java
package com.example;

import java.io.IOException;
import jakarta.servlet.*;
import jakarta.servlet.http.*;

public class HelloServlet extends HttpServlet {
    protected void doGet(HttpServletRequest req, HttpServletResponse resp)
            throws ServletException, IOException {
        resp.getWriter().println("Hello from WAR using Java 21 🌐");
    }
}
```

---

## ⚙️ Step 4: Configure `web.xml`

```bash
src/main/webapp/WEB-INF/web.xml
```

```xml
<web-app xmlns="https://jakarta.ee/xml/ns/jakartaee"
         version="6.0">

    <servlet>
        <servlet-name>hello</servlet-name>
        <servlet-class>com.example.HelloServlet</servlet-class>
    </servlet>

    <servlet-mapping>
        <servlet-name>hello</servlet-name>
        <url-pattern>/hello</url-pattern>
    </servlet-mapping>

</web-app>
```

---

## 🏗️ Step 5: Build WAR

```bash
mvn clean package
```

👉 Output:

```bash
target/war-demo.war
```

---

## 🚀 Step 6: Deploy on Apache Tomcat (Tomcat 10+ REQUIRED)

👉 Why?
Because Java 21 uses **Jakarta (not javax)**

---

### Copy WAR:

```bash
cp target/war-demo.war /opt/tomcat/webapps/
```

---

### Start Tomcat:

```bash
sh startup.sh
```

---

### Open:

```bash
http://localhost:8080/war-demo/hello
```

👉 Output:

```
Hello from WAR using Java 21 🌐
```

---

# 🎯 Teaching Explanation (Say This)

👉 “With Java 21, we use **Jakarta instead of javax**”
👉 “WAR apps now require **Tomcat 10+**”
👉 “Maven builds artifact using lifecycle → `clean → package`”

---

# 🔥 Common Errors (Students WILL face)

❌ Error: `javax.servlet not found`
✅ Fix: Use `jakarta.servlet-api`

❌ Error: WAR not deploying
✅ Fix: Use **Tomcat 10+**

❌ Error: Unsupported class version
✅ Fix: Set `<maven.compiler.release>21</maven.compiler.release>`

---

# 💡 Bonus (Interview Answer)

👉 “In Java 21 projects, WAR applications use Jakarta EE APIs and require compatible servers like Tomcat 10+. Maven handles packaging via lifecycle commands.”

---

If you want next level 🚀
I can give you:

✅ Spring Boot JAR (real-world microservice)
✅ Jenkins pipeline for build & deploy
✅ Full CI/CD project (GitHub + Maven + Tomcat + EC2)

Just tell me 👍
