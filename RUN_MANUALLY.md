# 🎬 BookMyShow – Manual Running Instructions

This guide explains how to compile, configure, and run this project manually on your computer without using any AI agent or helper tools.

---

## 🛠️ Prerequisites

Before you start, make sure you have the following installed on your laptop:
1. **Java Development Kit (JDK 25)** (Verify by running `java -version` in terminal)
2. **Node.js (v25+) and NPM** (Verify by running `node -v` and `npm -v`)
3. **MySQL Server** (Running on port `3306`)

---

## 1️⃣ Step 1: Database Setup

Make sure your MySQL server is running and configured with a database named `bms`.

If you ever need to create the database manually:
1. Open PowerShell or Command Prompt.
2. Run the MySQL CLI:
   ```powershell
   mysql -u root -pyeobo1520 -e "CREATE DATABASE IF NOT EXISTS bms;"
   ```

*Note: The database tables and seed data (movies, theaters, shows, etc.) will automatically be created and loaded when the Spring Boot backend starts up for the first time.*

---

## 2️⃣ Step 2: Compile & Run the Backend (Spring Boot)

1. Open a new terminal window (PowerShell or Command Prompt).
2. Navigate to the project root folder:
   ```powershell
   cd "C:\Users\muram\OneDrive\Desktop\spring project\BookMyShow"
   ```
3. *(Optional)* If you need to force a clean build (recompile everything):
   ```powershell
   Remove-Item -Path "target\classes" -Recurse -Force -ErrorAction SilentlyContinue
   ```
4. Build the application:
   ```powershell
   .\mvnw.cmd compile
   ```
5. Run the Spring Boot application:
   ```powershell
   .\mvnw.cmd spring-boot:run
   ```

Keep this terminal window open. You should see logs ending with `Started BmsApplication in X seconds` and `Tomcat started on port 8080`.

---

## 3️⃣ Step 3: Install & Run the Frontend (React)

1. Open a **new, separate** terminal window.
2. Navigate to the frontend directory:
   ```powershell
   cd "C:\Users\muram\OneDrive\Desktop\spring project\BookMyShow\frontend"
   ```
3. Install frontend packages (only needed the first time, or if `package.json` changes):
   ```powershell
   npm install
   ```
4. Run the frontend development server:
   ```powershell
   npm run dev
   ```

Keep this terminal window open. You should see a message saying `Local: http://localhost:5173/`.

---

## 🌐 Accessing the Application

With both terminals running in the background:
* **User Interface**: Open your browser and go to [http://localhost:5173/](http://localhost:5173/)
* **Interactive API Documentation (Swagger)**: Open [http://localhost:8080/swagger-ui/index.html](http://localhost:8080/swagger-ui/index.html)

---

## ⚙️ How Configuration Files Were Adjusted

* **[`pom.xml`](pom.xml)**: Set `<java.version>21</java.version>`. Even though your system has Java 25, targeting compiler release 21 ensures compatibility with Spring Boot's internal build tools while running perfectly on your Java 25 runtime environment.
* **[`application.properties`](src/main/resources/application.properties)**: Configured to connect to `jdbc:mysql://localhost:3306/bms` using username `root` and password `yeobo1520`.
* **[`data.sql`](src/main/resources/data.sql)**: Replaced PostgreSQL anonymous loop block (`DO $$ BEGIN...`) with ANSI-compliant raw SQL insert statements compatible with MySQL.
