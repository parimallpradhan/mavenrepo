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

![Image](https://images.openai.com/static-rsc-4/hYKmviaCZCD8tnHK1UwC_hUO46kCTkQIdiWZL69-Zode5uvfwlis7iZ8Vpu7CE2d7Np2C_8bIk-00YW0Jehrel3xkQLNtJWakkxuFgKeTdJa5dbRHKzUJgHovuZCQyUxHK5ht6WK0GYO0cD5DuUe_Am0pqfBvhEq5Y0cu1yjLMfBEUMPJ6zjm7xFgiulHRjd?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/you7UuXKYEk8T8gEvQ9vefyoVTtxueM68NT2x4EsPKv9WxuTsm6IM1sOF-55dKNpY2FhkDMWp00hy5WBXQembguMnniCAPs_DC4fT2_h-WGICLv1wgEMYeqk4PV2NJOWvj82cxYKy7UdflkngKyT8jNJp8t5JKxWo3qiVbmGPLEeybCmdsTkrSjBNzpndZZT?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/hr67UjU5jCRhNwsu3mlug45FA8O1H-caSpDX_wM2TCj6GvLT-e1An_Uyfd2sdU_QuDblbgHuyTA37I70M4GveRoSSgiptsmDhbvS6KnCaZds11JA2Ma-HaYcyt52uiqwRuG6Uw-LYmc6eTRAsJp_iD3VsLaiUf7IPtizyDGGBiVhdw1wvRsneOiRoSdADdE-?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/Lz_7VQxSpXumf5mgT7TzGngIyiHI4dPoCkPCmqWDU8y0RU53R-2rwzIMd7fR1IFEnZ6Us0EPzCSbNGh4AK7NzKlCgc16HDUpPcCH7X7LdawJLcIu9f1YalMXV5kEfVYGqN1VdfBp1ldFQhMi5YtOpAhSdwrU5K4GTJxESkHxWGMDq1e9sw3GFbulMLj_p1jW?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/tqNi3slV5g83bf7A6qfjUutxUojKAhMXaagsGvnpjHHzBJBiE7aO2BJa2wnwzNOfkZ5dtgQminPcoUc3oOaA5KbTXRrfSZNWlnzbDCp2dkzlgtaB8h8qJZjaCM-NRXhOjVQMC66TD2G5caYYlX6GILPKtjQg8fW3lE1102AK6UpvRepwdUTeLG3ui72AHT1G?purpose=fullsize)

👉 Standalone app → run using:

```bash
java -jar app.jar
```

---

## 🔵 WAR (Web App)

![Image](https://images.openai.com/static-rsc-4/59rAhsOTa0R7qMjZldJHCgdb24bp2qtZLiRhJ8SLLhLytbtb93OXC-Rh-H3wQa5mLPYtQFPLfDkZUECrW3L8R03lZF9eNNvmn-f5w51f-ALuiaXnQ-RvabOQ6jcW-pGzBskfSIAir4inbXb1keuJy_2_DGUrKM9ROXPRDsltrZg0cs244KVYlgEYBA3CZPFY?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/3HDcrLgdH5C2LXQW5XzXFlXsj3SJaWHJux-mHfNuJrWIhU8yXPrbbbCz4SLYCFhot9SPHhqAGoQgwLUzmZQKErylLDFXa6BiaPDi8mGUaQ_lundxkjBYbMrTLeiklkZ92s8nIAv8UuTzqNbsI6Sc3CL4tOi1SevF7XrWRmqRai83wttmsECw12rkYKOPM3-S?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/K2i5nJrfEP_fPUNq6b2CKUKmJwojpspzn3r8_Blb7t2zNprGX2UX0EwacSQaWnfFPmr-fK1knDH0MqRdZO2UWrnoVbVtmvK5dstrhTmIdkn4vaPmsq5r9PGyMNBE7NaclaxfCu-uOztz0Eg9eBI5Nwe80MVZ4rCcqinFFBEzM-nNKrYUNnNgOhhge7hhvxLR?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/tmJ1BKJFwxmGzh2J4v1Bz0vdMsnnJRqTdKRPtjUCxUldf8_j-jgBe6LZcAYkeGK8L3QAnhauUQuv6zHQ3BIr9ElBL3dmtdI6abZsYffBc1r8zU4bfqafaGrLtyDEtRXbNS_OzVkemlWArznejjVsTXmP1mEoISqUL73Y1Bozg5hHLP3z7GMj8BY6mk4RwMF8?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/ngJq2qhPh6nnUPk2j6rjmeSNkIOogVgwtSQNB5uIrm4Rn7KILDFI0Yu5y7b_3faZlvxGuapMPzZBaVxFnA0wKVKoqjqQTfIA4v6mNFWFOv2BZ-kZEp0mkZawbsd3qCxEFMG2KX7MhcX91JhKOI5399O3Z9F2w_0rDAC5RQSpPON-epQDc77z7aaJXv57nV6x?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/k2ngOAijcWuHS3dSaqcDJmxZAe6M7jKqx0Eby-eoIiY0wxJ9VFV8wLDrozxzTkj8E7cEGvxIeuBDKfbBg-64DvJdtBxECnCV4hb48yVexedh9kqJCs2WZsK9FXlbe9J-r47K05OtoNEtV8epqLVMTzDqllnptXbk_sUrGZWafmR9Uik9Rpq06_s6FLaHyzQB?purpose=fullsize)

👉 Deploy on:

* Apache Tomcat

---

## 🔴 EAR (Enterprise App)

![Image](https://images.openai.com/static-rsc-4/sEw2Kkvl1AXZPUFmIJyXwCIzEIy2Af0KzoJOb37uUTpREdvptnpfEm0W7tslyGKhRSw7vzWw6nQhEW15R-kETWacsAbXepk8aiGYGXJF1hsoyedMkhmz_aTEWb3Li7MqiVwlJes4gtrvrMUKQBJJ-ywhp6ppHpz__rtM0nm-qxgQVG0GbVTz2dukc37nTQaJ?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/u24VbG8aEla5BVz20UY6PuH4wRNSrVTN2U8pGs2bihiO6aR83IND2tsWGTxveBpdVC85IznEEqpVROvIWWKd6RHNc4kbaLORynEIJkyvWxSQTOsWGBN8rXKb8BZOitzTmh0pKN-xg1qmuUwWal2UO6oeh8FDRicFQlAX9fzlItTJBXRpv_LrnfrdwQcu3i1O?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/GbaSkIVL02dEtjsneacpfck-cxcIb2w_vZ2YIcR4ECFJSOCaLbfAEpEZBrhhL-pc6DKt2Aj2rCxw9E6vO_Nzv5HlmOBJNYlAHDAbrBugTNDeyW5LVI4cd01QdsSxKAp7YwfJkw0iiZwzojUGaTQ4m5L5gQg_XpwHuFh2Km0uzw-fIZpGtoDQLHwiNOmhFEU1?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/41whU9z07JvnEOl0NQ7HgP7ea5AQdQ8PvGF2JHnX4ICs6vRa1hmByj3rJn-hFttc5YuZ4WBIssJtClBfJ4ul7w0gRifCE-Rp0UXI3hLf_1vHOvWr7vnuhKkS_cprLrqEAgk2z-pan-6NOSoV-JbMYZQ7h_0hN3n5TpnxvP248EGPi0Dmc6t_221_hySlUfG4?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/ObhOvj0Q8gH4l-Wcmx97sPLxXLoEgMwUWm1oR8BMReqfDPLvTNghFA7It2YhlarIcRa7Ccf6IUb-SC8c_m8zgItgcqw-2YATKmQxfs0zj8sgq9g7u_vNcYHcCFlWhAJFphQDzX3meDQylVHcRS-xuwGFcxRh6Ci1kYxid_CPnEoQCvHQ7Xjc3LRNm8ahVEYu?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/ic4OZjxhh4FVfEWi0qfbi61GDE0gFdcJWnI9E18jL_BXHGnODgxPP9bRs2a7iaEtqnv8jXRZxYr0N0J1IeKfpYuQ_ED78nts_DjQQW0z_xlOYnMFLB6L1OH-82UjAc81Gl9zxwTzFuhaane54hGiTPUixQkgtm8yrrqNCekPo3jYy1CJwuBx-vBpXhT9ZeK7?purpose=fullsize)

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

## 🎯 Teaching Line

👉 “Maven first checks local → then central → then remote.”

---

# 🔁 5. Maven Lifecycle (VERY IMPORTANT)

## 📌 Explain Flow

![Image](https://images.openai.com/static-rsc-4/z2GwR0JEk3NQ-SoFXhwRtV0KaCv12Gtz5npvVfSdvJkrG6B3hV8PErMIH2cAvsA4pmq7pi7GTSpNlQEXoTqV08L_ih-JyiPmXnLyjOczjNqUsDfzdS_VRJFb3lMbZq6Rz9Z9wtNNj5gVgOvL6jbnVRYSP9CvLsC04GCLOZsXr7Evz6s6GvgpuX-3vRQ_e2kT?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/t_tdpG7aHSBR60w1a8D3wDdLWiYfUi_0z0jscAbnHV_WPkJDMsoKzDoCKdcAMzbW-5sHdJl-oybWxfxRM4Ql0ypCUJLimD-qG-l0x58cBg1MbZbUTLokhXlmu_UVJ9KF5_GcX7TM1JcIrEMAjPT2ZzH8qWPoxKlwvcvungK02GcRGimsNtwDqdg9ePF_FidS?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/4hki0cuFvovsnNNPbnl7n6M2GAf4cz6eZXab_z8KYqOqsM9s7LX82HTwjwKa8g7WSbd-99-xfoz3oZ9bu1amgjghlnH7wQHN4zkBgyyL5Uhv6N7kVG31ZbiEbAbj-vCIJNtbGHXup-jCwoOcpct83UZjv2YDd-_msCwtIn2snOPJ98YNOEFGxPTvu4xPE7FM?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/wEqXV6HFjmyGZHNkMDIBMYsJBeijuwda1fPZ364oE5k4N9aj39phEnyOp4dbgt62IyBGAIfgIN0yik3H3_m2VFiq2wLY3tXcQ4ZvWYIDkEUloG110v5rmvfWyQ_SQQ3w6U5dgmPt1oi7TpwnUqpZdNJLHjz9bRtQsbAJdJaea83KIz78YLEI1hOvpvDcm-Pg?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/Wp3bxErLLhRjnmnfUMzdAmIF4aU6yP3xvRab2LxC2d4DveAV7tt-HUlWg0vd6qJdZMyUjn6XY1AFo58SdEkDmZ9fTJmr6ErqzbrEVDEVtnatIEQfW8LKRjBw7nkk0JgxLaeRCWvC7MYJ7gWa5WozTmXee5AP5_0sbkbWh8Ta9FkvXuHq9834bpFimyalz-0-?purpose=fullsize)

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

## 🎯 Teaching Line

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

# 💼 7. Real-Time Use Case (VERY IMPORTANT FOR STUDENTS)

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

# 🚀 8. Quick Recap (Ask Students)

Ask:

* What is pom.xml?
* Difference between JAR & WAR?
* What does `mvn install` do?
* Where dependencies are stored?

---

# 🎁 Bonus Tips (Trainer Advantage)

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

If you want next level 🚀
I can give you:

✅ PPT slides (corporate style)
✅ Day-wise DevOps training plan
✅ Jenkins + Maven CI/CD live project

Just tell me 👍
