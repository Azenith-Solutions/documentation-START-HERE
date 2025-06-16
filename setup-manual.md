# Hardware Tech - Setup Manual

Welcome to the setup guide for Hardware Tech Project. This document provides step-by-step instructions to configure the necessary environment and get the project operational on your system.

This manual focuses solely on the setup process. For comprehensive documentation about the project's features, architecture, API, and usage patterns, please refer to our [main](https://github.com/Azenith-Solutions/documentation-START-HERE) [documentation](https://github.com/Azenith-Solutions/documentation-START-HERE).

## Table of Contents

*   [Prerequisites](#prerequisites)
*   [Getting the Code](#getting-the-code)
*   [Installation](#installation)
*   [Configuration](#configuration)
    *   [Environment Setup](#environment-setup)
    *   [Database Configuration (If Applicable)](#database-configuration-if-applicable)
    *   [External Services Configuration (If Applicable)](#external-services-configuration-if-applicable)
*   [Running the Project](#running-the-project)
*   [Verification](#verification)
*   [Troubleshooting](#troubleshooting)
*   [Development Enviroment Configuration](#development-environment-configuration)

---

## Development Tools Prerequisites

This guide outlines the prerequisites for setting up various tools on Windows and Linux systems, with links for installation and configurations.

### General Requirements
- **Operating System**:
  - **Windows**: Version 10 or higher.
  - **Linux**: Any recent distribution (Ubuntu, Fedora, Debian, etc.).

- **Internet**: Stable connection (Wi-Fi or 4G).

---

## Tools and Installation

### Java (JDK 21)
- **Windows**:
  - Download the JDK from the official [Oracle website](https://www.oracle.com/java/technologies/javase-downloads.html).
  - After installation, set the `JAVA_HOME` environment variable.

- **Linux**:
  - Open a terminal and run:
    ```bash
    sudo apt update
    sudo apt install openjdk-21-jdk
    ```
  - Verify installation with:
    ```bash
    java -version
    ```

### Spring Boot
- Spring Boot requires Java. Install it using Maven.
- **Installation Guide**: [Spring Boot Documentation](https://spring.io/guides).

### Python 3
- **Windows**:
  - Download the installer from [python.org](https://www.python.org/downloads/).
  - During installation, check the box to add Python to PATH.

- **Linux**:
  - Run the following commands:
    ```bash
    sudo apt update
    sudo apt install python3
    ```
  - Verify installation:
    ```bash
    python3 --version
    ```

### Pip (Python Package Manager)
- **Windows**:
  - Pip is included in Python 3.x installers.
  - Verify installation:
    ```bash
    pip --version
    ```

- **Linux**:
  - Install pip:
    ```bash
    sudo apt install python3-pip
    ```

### Node.js (v21) and npm
- **Windows**:
  - Download from the [official Node.js website](https://nodejs.org/).
  - npm is bundled with Node.js.

- **Linux**:
  - Install Node.js and npm:
    ```bash
    sudo apt update
    sudo apt install -y nodejs npm
    ```

- Verify installation:
  ```bash
  node -v
  npm -v
  ```

### MySQL
- **Windows**:
  - Download the MySQL Installer from the [official website](https://dev.mysql.com/downloads/installer/).
  - During installation, select the Developer Default setup to include MySQL Server and Workbench.
  - Configure the root user credentials during the setup process.

- **Linux**:
  - Install MySQL Server:
    ```bash
    sudo apt update
    sudo apt install mysql-server
    ```
  - Start and enable MySQL service:
    ```bash
    sudo systemctl start mysql
    sudo systemctl enable mysql
    ```
  - Secure the installation to set a root password and remove unnecessary options:
    ```bash
    sudo mysql_secure_installation
    ```

- Verify installation:
  ```bash
  mysql --version
  ```
## Recommended IDEs and Tools


### Visual Studio Code
- **Description**: A lightweight, highly customizable code editor suitable for multiple programming languages.
- **Download**: [VSCode](https://code.visualstudio.com/).
- **Extensions:** Python.

### MySQL Workbench
- **Description**: A visual tool for database design, administration, and SQL development.
- **Download**: [MySQL Workbench](https://dev.mysql.com/downloads/workbench/).

### IntelliJ IDEA
- **Description**: A robust IDE ideal for Java, Spring Boot, and other JVM-based development.
- **Download**: [IntelliJ IDEA](https://www.jetbrains.com/idea/).

### PyCharm (Optional)
- **Description**: An IDE specifically designed for Python development.
- **Download**: [PyCharm](https://www.jetbrains.com/pycharm/).

### Additional Tools
- For frontend development, consider **Figma** for UI/UX design: [Figma](https://www.figma.com/).
- For lightweight text editing, use **Notepad++**: [Notepad++](https://notepad-plus-plus.org/).

---

## Verification

After installing the required tools, verify their installations by running the following commands in the terminal (Linux) or Command Prompt (Windows):

```bash
java -version
python3 --version
pip --version
node -v
npm -v
mysql --version
```

## Troubleshooting

If you encounter issues during installation or verification, follow the steps below to resolve common problems.

### Java Issues
- **Problem**: `java -version` not recognized.
  - **Solution**: Ensure the JDK `bin` directory is added to the PATH:
    - **Windows**: Add `C:\Program Files\Java\jdk-17\bin` to the PATH variable.
    - **Linux**: Add `export PATH=$PATH:/usr/lib/jvm/java-17-openjdk/bin` to `~/.bashrc` or `~/.zshrc`, then run `source ~/.bashrc`.

### Python Issues
- **Problem**: `python3 --version` not recognized.
  - **Solution**:
    - On **Windows**, ensure Python is added to PATH during installation.
    - On **Linux**, confirm installation with `sudo apt install python3`.

### Pip Issues
- **Problem**: `pip` command not found.
  - **Solution**:
    - Run `python3 -m ensurepip --upgrade` to install pip.

### Node.js or npm Issues
- **Problem**: `node` or `npm` commands not recognized.
  - **Solution**:
    - **Windows**: Reinstall Node.js and ensure "Add to PATH" is checked during setup.
    - **Linux**: Install using Node Version Manager (NVM) for better version management:
      ```bash
      curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
      source ~/.bashrc
      nvm install 21
      ```

### MySQL Issues
- **Problem**: Unable to start MySQL service.
  - **Solution**:
    - On **Linux**, check the service status:
      ```bash
      sudo systemctl status mysql
      ```
      If not active, start it:
      ```bash
      sudo systemctl start mysql
      ```

- **Problem**: Access denied for root user.
  - **Solution**:
    - Run the secure installation script to reset credentials:
      ```bash
      sudo mysql_secure_installation
      ```

### PATH Issues
- **Problem**: Commands not recognized globally.
  - **Solution**:
    - Verify that the tool's `bin` directory is added to the PATH.
    - Restart your terminal or system after updating PATH.

### IDE Issues
- **Problem**: IDE unable to detect installed tools.
  - **Solution**:
    - Check IDE settings for configured tool paths:
      - For PyCharm: Go to **File > Settings > Project > Python Interpreter**.
      - For IntelliJ IDEA: Go to **File > Project Structure > SDKs** and add the correct JDK.

## Additional Help
- Visit the official documentation or community forums for each tool:
  - [Java](https://www.oracle.com/java/technologies/)
  - [Python](https://www.python.org/)
  - [Node.js](https://nodejs.org/)
  - [MySQL](https://dev.mysql.com/doc/)

If the problem persists, consider reinstalling the tool or consulting with a development community for advanced troubleshooting.

---

## Development Enviroment Configuration

### 1. Database
- Open MySQL Workbench.
- Set up a local connection on port 3306.
- Create a database named "_hardwaretechdb_".

### 2. BACKEND
- Clone the [backend-api-REST](https://github.com/Azenith-Solutions/backend-api-rest) repository. 
- Create a .env.development file in the same directory as .env.production.
- Use the provided [.env.example](https://github.com/Azenith-Solutions/documentation-START-HERE/blob/main/.env.example) as a reference to configure database credentials, JWT secret, and Brevo API key in .env.development.
- Run the backend server.
- **Note:** Verify in MySQL Workbench whether the tables have been successfully created — JPA should generate them automatically from the model definitions.

### 3. ETL Process
- Clone the [excelDB_loader](https://github.com/Azenith-Solutions/extract-transform-load-script) repository.
- Make sure Python 3 is installed on your machine.
- Also ensure that PIP is up to date.
- Create a .env file in the root directory.
- Use the provided [.env.example](https://github.com/Azenith-Solutions/documentation-START-HERE/blob/main/.env.example) as a reference to configure database credentials and the environment in .env file.
- **Windows:**
  - Switch to the _windows_ branch.
  - Install the dependencies:
```bash
pip install -r requirements.txt
```
  - Run the ETL process:
```bash
python main.py
```
- **Linux:**
  - Switch to the _main_ branch.
- **Note:** Check in MySQL if the data have been inserted correctly.

### 4. FRONTEND
- Install the dependencies:
```bash
npm i
```
- Run the frontend using Vite command:
```bash
npm run dev
```
- **Note:** If an error occurs, delete package-lock.json and the node_modules folder, then reinstall the dependencies

---

For more details, please refer to our [main](https://github.com/Azenith-Solutions/documentation-START-HERE) [documentation](https://github.com/Azenith-Solutions/documentation-START-HERE).