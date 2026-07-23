# 🚀 Project: Jenkins + Maven CI/CD (Java App)

## 🎯 Goal

👉 Automate:
**Code → Build (Maven) → Package (JAR/WAR) → Deploy**

---

# 🧱 Architecture (Explain to students)


👉 Flow:

1. Developer pushes code to Git
2. Jenkins pulls code
3. Maven builds project
4. Artifact deployed

---

# 🖥️ Step 1: Setup EC2 / Linux Server

## Install Java 21

```bash id="nl46nl"
sudo yum install java-21-amazon-corretto -y
```

## Install Maven

```bash id="8nypj9"
sudo yum install maven -y
```

## Install Jenkins

```bash id="skk8r8"
sudo wget -O /etc/yum.repos.d/jenkins.repo \
https://pkg.jenkins.io/redhat-stable/jenkins.repo
```

```bash id="qb6pjc"
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
```

```bash id="3ul2m3"
sudo yum install jenkins -y
```

```bash id="c5wj4p"
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

---

## Open Jenkins

👉 `http://<EC2-IP>:8080`

Unlock:

```bash id="0l7y6g"
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

---

# ⚙️ Step 2: Configure Jenkins

👉 Install Plugins:

* Git
* Maven Integration
* Pipeline

👉 Configure Maven:
Manage Jenkins → Tools → Add Maven
Name: `Maven3`

---

# 📦 Step 3: Create Maven Project (JAR)

```bash id="gw8a9z"
mvn archetype:generate \
-DgroupId=com.demo \
-DartifactId=ci-demo \
-DarchetypeArtifactId=maven-archetype-quickstart \
-DinteractiveMode=false
```

---

## Modify Code

AppTest.java

```java id="1x4bxz"
public class App {
    public static void main(String[] args) {
        System.out.println("CI/CD Pipeline Success 🚀");
    }
}
```

---

## Push to GitHub

```bash id="pgvvdj"
git init
git add .
git commit -m "initial commit"
git remote add origin <your-repo-url>
git push -u origin main
```

---

# 🔁 Step 4: Create Jenkins Pipeline Job

👉 New Item → Pipeline → Name: `ci-cd-demo`

---

## 🧾 Add Jenkinsfile in Project

```groovy id="1jgb9y"
pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git '<your-repo-url>'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        stage('Deploy (Local)') {
            steps {
                sh 'cp target/*.jar /home/ec2-user/'
            }
        }
    }
}
```

---

# ▶️ Step 5: Run Pipeline

👉 Click **Build Now**

---

## 🎯 Expected Output

* Jenkins stages executed
* JAR created
* Artifact stored
* File copied to server

---

# 🔵 (Optional Advanced) WAR Deployment

## Install Apache Tomcat

```bash id="lf4o09"
sudo yum install tomcat -y
sudo systemctl start tomcat
```

---

## Update Jenkinsfile (WAR Deploy)

```groovy id="x4s4o3"
stage('Deploy to Tomcat') {
    steps {
        sh 'cp target/*.war /var/lib/tomcat/webapps/'
    }
}
```

---

# 💼 Real-Time Explanation (Say This)

👉 “In companies, developers push code → Jenkins automatically builds using Maven → artifacts deployed to servers.”

👉 “This pipeline replaces manual build and deployment.”

---

# 🔥 Interview Questions 

👉 What is CI/CD?
👉 What does `mvn clean package` do?
👉 What is Jenkins pipeline?
👉 Difference between freestyle and pipeline job?

---

# 🎓 project Flow 

1. Draw CI/CD diagram
2. Setup Jenkins LIVE
3. Create Maven project
4. Push to GitHub
5. Run pipeline
6. Show output

---


