# 🎬 BookMyShow Clone - Advanced Movie Ticket Booking System

A full-stack movie ticket booking application built with a **Spring Boot** backend and a **React (Vite + TypeScript)** frontend. This guide provides clear, step-by-step instructions to download all necessary dependencies and run the project manually on **Windows** without any AI helper tools.

---

## 🛠️ Prerequisites: What to Download & Install

To run this application on your Windows machine, you need to download and install the following three tools:

### 1. Java Development Kit (JDK 21 or 25)
* **What it is:** The runtime and compiler environment required for the Spring Boot backend.
* **Download Link:** [Adoptium Eclipse Temurin JDK](https://adoptium.net/temurin/releases/) or [Oracle JDK Downloads](https://www.oracle.com/java/technologies/downloads/)
* **Installation:** Download the `.msi` or `.exe` installer for Windows x64 and follow the installation wizard.
* **Verification:** Open Command Prompt or PowerShell and type:
  ```cmd
  java -version
  ```
  You should see output indicating Java version `21` or `25`.

### 2. Node.js (v20 or v22 LTS)
* **What it is:** The JavaScript runtime environment needed to install packages and run the React frontend.
* **Download Link:** [Node.js Official Website](https://nodejs.org/)
* **Installation:** Choose the **LTS (Long Term Support)** Windows Installer (`.msi`) and follow the installer prompts. Make sure to check the box that adds Node.js to your PATH (enabled by default).
* **Verification:** Open a new terminal and type:
  ```cmd
  node -v
  npm -v
  ```
  You should see version numbers for both node and npm.

### 3. MySQL Community Server
* **What it is:** The relational database management system to store movies, theaters, showtimes, and booking information.
* **Download Link:** [MySQL Installer for Windows](https://dev.mysql.com/downloads/installer/)
* **Installation:** 
  - Download the web installer and choose "Developer Default" or "Server Only".
  - During setup, set a password for the `root` user (remember this password!).
  - Keep the port as `3306` (default).
  - Ensure the MySQL service starts automatically when Windows boots.
* **Verification:** Open Command Prompt or PowerShell and type:
  ```cmd
  mysql --version
  ```

---

## 🚀 Step-by-Step Running Guide

Follow these steps in order to set up the database, start the backend server, and run the frontend interface.

### 1️⃣ Step 1: Database Configuration
1. Open your **MySQL Workbench** or MySQL CLI.
2. Connect to your local database server.
3. Create a database named `bms` by running the following SQL command:
   ```sql
   CREATE DATABASE IF NOT EXISTS bms;
   ```
4. Configure the backend database credentials:
   - Open the file `src/main/resources/application.properties` in a text editor (e.g., Notepad, VS Code).
   - Verify/Update the username and password to match your MySQL configuration:
     ```properties
     spring.datasource.url=jdbc:mysql://localhost:3306/bms?useSSL=false&serverTimezone=UTC&allowPublicKeyRetrieval=true
     spring.datasource.username=root
     spring.datasource.password=YOUR_MYSQL_PASSWORD_HERE
     ```
     *(Note: If your root password is `yeobo1520`, then it is already pre-configured.)*

---

### 2️⃣ Step 2: Run the Backend (Spring Boot)
The project includes a Maven wrapper (`mvnw.cmd`), meaning you do not need to install Maven manually.

1. Open **Command Prompt** or **PowerShell**.
2. Navigate to the project root directory where `pom.xml` is located:
   ```cmd
   cd "C:\Users\muram\OneDrive\Desktop\spring project\BookMyShow"
   ```
3. Compile and build the project:
   ```cmd
   .\mvnw.cmd compile
   ```
4. Start the Spring Boot backend server:
   ```cmd
   .\mvnw.cmd spring-boot:run
   ```
5. Keep this terminal window open. You should see logs flowing, ending with a message like:
   ```text
   Started BmsApplication in X.XXX seconds (process running for X.XX)
   Tomcat started on port 8080 (http) with context path '/'
   ```
   *Note: On the first startup, Hibernate will automatically create the tables inside the `bms` database and populate them with seed data from `src/main/resources/data.sql`.*

---

### 3️⃣ Step 3: Run the Frontend (React + Vite)
Open a **new, separate** Command Prompt or PowerShell window (do not close the backend terminal).

1. Navigate to the frontend directory:
   ```cmd
   cd "C:\Users\muram\OneDrive\Desktop\spring project\BookMyShow\frontend"
   ```
2. Install the required node modules and dependencies:
   ```cmd
   npm install
   ```
3. Start the Vite development server:
   ```cmd
   npm run dev
   ```
4. You should see output like:
   ```text
    VITE v6.x.x  ready in XXX ms

    ➜  Local:   http://localhost:5173/
    ➜  Network: use --host to expose
   ```
5. Keep this terminal window open as well.

---

## 🌐 Accessing the Application

With both the backend and frontend servers running:

* **User Interface:** Open your web browser (Chrome, Edge, Firefox) and go to:
  👉 **[http://localhost:5173/](http://localhost:5173/)**
* **API Documentation (Swagger UI):** To view or test backend REST API endpoints directly, go to:
  👉 **[http://localhost:8080/swagger-ui/index.html](http://localhost:8080/swagger-ui/index.html)**

---

## 📂 Project Structure

* **`src/main/java/`**: Java source code for controllers, services, repositories, and entities.
* **`src/main/resources/`**: Configuration properties and SQL initialization files.
* **`frontend/`**: React application components, assets, pages, and routing.
* **`pom.xml`**: Project Object Model configuration file for Spring Boot dependencies.
