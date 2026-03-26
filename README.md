# 🏋️‍♂️ FitDesk - Gym Management System
## A full-stack gym administration platform built with Python, Streamlit & MySQL — enabling complete management of members, trainers, memberships, and workout classes through a clean web interface.

<h2>Table of Contents</h2>
<ul>
  <li><a href="#about">About</a></li>
  <ul>
    <li><a href="#what-is-gms">What is FitDesk?</a></li>
    <li><a href="#features">Features</a></li>
    <li><a href="#why-gms">Why FitDesk?</a></li>
  </ul>
  <li><a href="#getting-started">Getting Started</a></li>
  <ul>
    <li><a href="#prerequisites">Prerequisites</a></li>
    <li><a href="#installation">Installation</a></li>
    <li><a href="#backend-setup">Database Setup</a></li>
    <li><a href="#frontend-setup">Running the App</a></li>
  </ul>
  <li><a href="#tech-used">Tech Stack Used</a></li>
  <li><a href="#architecture">System Architecture</a></li>
  <li><a href="#screenshots">Screenshots & App Demonstration</a></li>
  <li><a href="#conclusion">Conclusion</a></li>
  <li><a href="#team">Developed By</a></li>
</ul>

---

<section id="about">

## About

<h3 id="what-is-gms">What is FitDesk?</h3>

The **FitDesk** is a full-stack web application built using **Python** and **Streamlit**, backed by a **MySQL** relational database. It provides gym administrators with a clean, intuitive interface for managing members, memberships, trainers, and workout classes — complete with secure login authentication, duplicate prevention logic, cascaded deletion, and real-time database synchronization.

Designed as a **DBMS mini-project**, it demonstrates full CRUD operations, relational integrity constraints, and a lightweight UI layer built entirely in Python.

<h3 id="features">Features</h3>

- **🔐 Secure Login Authentication**
  - Username and password login before accessing any module.
  - Session-based access control using Streamlit session state.

- **👤 Member Management**
  - Add, view, update, and delete member records.
  - Stores name, gender, age, phone number, and address.

- **💳 Membership Management**
  - One-to-one membership per member with duplicate prevention.
  - Tracks price, start date, end date, and gym branch.
  - Validates member existence before assigning a membership.

- **🏋️ Trainer Management**
  - Full CRUD for trainer profiles including name, age, and contact number.

- **🧘 Workout Class Management**
  - Add, update, and delete workout programs offered at the gym.

- **🏢 Gym Branch Information**
  - View gym details and branch-level data from the database.

- **⚠️ Duplicate Membership Prevention**
  - Checks if a member already holds a membership before creating a new one.
  - Raises clear error messages when violations are detected.

- **🗑️ Cascaded Deletion**
  - Deleting a member automatically removes their linked membership records.
  - Maintains referential integrity across the database.

- **💾 Real-time MySQL Updates**
  - All CRUD operations commit instantly to MySQL.
  - Inline success and error feedback using Streamlit notifications.

<h3 id="why-gms">Why FitDesk?</h3>

- **Eliminates Manual Record-Keeping**: Replaces paper-based or spreadsheet gym management with a fast, database-backed web interface.
- **Enforces Data Integrity**: Relational constraints, duplicate checks, and cascaded deletions ensure clean and consistent data at all times.
- **Simple Yet Powerful UI**: Streamlit's sidebar-driven navigation provides an intuitive workflow with zero frontend complexity.
- **One Platform, All Operations**: Members, trainers, memberships, and workout classes are all managed from a single unified application.
- **Python-Native Stack**: No separate frontend framework needed — the entire app runs from a single Python file.
- **Lightweight & Easy to Deploy**: Minimal dependencies, runs locally with a simple `streamlit run app.py` command.

</section>

---

<section id="getting-started">

## Getting Started

<h3 id="prerequisites">Prerequisites</h3>

Before you begin, ensure the following are installed in your environment:

#### For the Application:
- **Python 3.x** — Core language for the app and database logic.
  - [Download Python](https://www.python.org/downloads/)
- **pip** — Python package manager.
- **Required Python Libraries**:
  - `streamlit` — Web UI framework
  - `mysql-connector-python` — MySQL database connector
  - `pandas` — Query result handling and display

#### For the Database:
- **MySQL Server** — Installed and running locally.
  - [Download MySQL](https://dev.mysql.com/downloads/installer/)
- A MySQL database (default: `suhasvarna`) with the required tables created.

> 💡 **Default Login Credentials** — `Username: dbms` | `Password: 1234`

<h3 id="installation">Installation</h3>

#### Clone the Repository:
```bash
git clone https://github.com/Suhas-Varna/FitDesk.git
cd FitDesk
```

<h3 id="backend-setup">Database Setup (MySQL)</h3>

1. **Start your MySQL Server** and open MySQL Workbench or CLI.

2. **Create the database**:
```sql
CREATE DATABASE databasename;
USE databasename;
```

3. **Create the required tables**:
```sql
CREATE TABLE member (
    member_id INT PRIMARY KEY,
    name VARCHAR(100),
    gender CHAR(1),
    age INT,
    phone_no VARCHAR(15),
    address VARCHAR(255)
);

CREATE TABLE gym (
    gym_id INT PRIMARY KEY,
    gym_name VARCHAR(100),
    location VARCHAR(255)
);

CREATE TABLE gym_membership (
    membership_id INT PRIMARY KEY,
    member_id INT UNIQUE,
    price DECIMAL(10,2),
    start_date DATE,
    end_date DATE,
    gym_name VARCHAR(100),
    FOREIGN KEY (member_id) REFERENCES member(member_id)
);

CREATE TABLE trainer (
    trainer_id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    phone_no VARCHAR(15)
);

CREATE TABLE workout_class (
    workout_id INT PRIMARY KEY,
    workout_name VARCHAR(100)
);
```

4. **Update your credentials** inside `app.py`:
```python
connection = mysql.connector.connect(
    host='localhost',
    database='databasename',   # Your database name
    user='root',             # Your MySQL username
    password='your_password' # Your MySQL password
)
```

<h3 id="frontend-setup">Running the App</h3>

1. **Create and activate a virtual environment** (Recommended):
```bash
# Create
python -m venv venv

# Activate — Windows
venv\Scripts\activate

# Activate — Mac / Linux
source venv/bin/activate
```

2. **Install dependencies**:
```bash
pip install -r requirements.txt
```

3. **Run the Streamlit app**:
```bash
streamlit run app.py
```

The app will open at: `http://localhost:8501`

</section>

---

<section id="tech-used">

## Tech Stack — Built With
![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-App-red?logo=streamlit&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-Database-orange?logo=mysql&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data-lightgrey?logo=pandas&logoColor=white)

**Python:** Core programming language used for the entire application — UI, business logic, validation, and database operations.

**Streamlit:** Python-based web framework that renders the interactive UI including sidebar navigation, forms, tables, and real-time notifications.

**MySQL:** Relational database management system storing all gym data across five normalized tables with enforced foreign key constraints.

**mysql-connector-python:** Official MySQL driver for Python, used to establish connections and execute all CRUD queries.

**pandas:** Used to convert MySQL query results (dictionaries) into DataFrames for clean tabular display via `st.dataframe()`.

</section>

---

<section id="architecture">

## System Architecture

### 🏗️ High-Level Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                      FitDesk (Gym Management System)                    │
│  ┌──────────────────┐  ┌──────────────────────┐  ┌──────────────────┐   │
│  │   Login Screen   │→ │  Sidebar Navigation  │→ │  Feature Module  │   │
│  └──────────────────┘  └──────────────────────┘  └──────────────────┘   │
│              ↓                    ↓                        ↓            │
│  ┌──────────────────┐  ┌──────────────────────┐  ┌──────────────────┐   │
│  │ Member Manager   │  │ Membership Manager   │  │ Trainer Manager  │   │
│  │  (CRUD)          │  │  (CRUD + Validation) │  │  (CRUD)          │   │
│  └──────────────────┘  └──────────────────────┘  └──────────────────┘   │
│              ↓                    ↓                        ↓            │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │              Python Query Layer (app.py)                         │   │
│  │  execute_read_query() │ execute_write_query()                    │   │
│  │  execute_update_query() │ execute_delete_query()                 │   │
│  └──────────────────────────────────────────────────────────────────┘   │
└──────────────────────────────│──────────────────────────────────────────┘
                               │  mysql-connector-python
                               ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                            MySQL Database                               │
│  ┌────────────┐  ┌─────────────────┐  ┌───────────┐  ┌─────────────┐    │
│  │   member   │  │  gym_membership │  │  trainer  │  │workout_class│    │
│  └────────────┘  └─────────────────┘  └───────────┘  └─────────────┘    │
└─────────────────────────────────────────────────────────────────────────┘
```

### 📊 Data Flow Diagram

```
  USER LOGS IN (username: dbms / password: 1234)
                │
                ▼
┌───────────────────────────────────────────────┐
│              Streamlit Frontend               │
│  • Sidebar menu selection                     │
│  • Form input (Add / Update / Delete)         │
└──────────────────┬────────────────────────────┘
                   │  Python function call
                   ▼
┌───────────────────────────────────────────────┐
│            Python Backend (app.py)            │
│  • Validates input fields                     │
│  • Checks record existence                    │
│  • Builds raw SQL query string                │
│  • Calls create_connection()                  │
└──────────────────┬────────────────────────────┘
                   │
                   ▼
┌───────────────────────────────────────────────┐
│              MySQL Server                     │
│  • Executes INSERT / UPDATE / DELETE / SELECT │
│  • Enforces FK constraints                    │
│  • Commits or rolls back transaction          │
└──────────────────┬────────────────────────────┘
                   │
                   ▼
┌───────────────────────────────────────────────┐
│           Result Returned to UI               │
│  • SELECT → pd.DataFrame → st.dataframe()     │
│  • Write  → st.success() or st.error()        │
└───────────────────────────────────────────────┘
```

### 🗂️ Database Schema

```
suhasvarna/
│
├── member               # Core member profiles
│   ├── member_id (PK)
│   ├── name
│   ├── gender
│   ├── age
│   ├── phone_no
│   └── address
│
├── gym_membership       # 1:1 with member, N:1 with gym
│   ├── membership_id (PK)
│   ├── member_id (FK → member, UNIQUE)
│   ├── price
│   ├── start_date
│   ├── end_date
│   └── gym_name
│
├── gym                  # Gym branch details
│   ├── gym_id (PK)
│   ├── gym_name
│   └── location
│
├── trainer              # Trainer profiles
│   ├── trainer_id (PK)
│   ├── name
│   ├── age
│   └── phone_no
│
└── workout_class        # Workout programs
    ├── workout_id (PK)
    └── workout_name
```

### 🔗 Entity Relationships

| Entity A | Relationship | Entity B | Constraint |
|----------|-------------|----------|------------|
| 🧍 Member | **1 : 1** | 💳 Gym_Membership | One member can hold only one membership |
| 🏢 Gym | **1 : N** | 💳 Gym_Membership | One gym branch can have many memberships |
| 🏋️ Trainer | **1 : N** | 🧘 Workout_Class | One trainer can conduct many workout classes |

### 🔐 Security & Integrity

- **Login Gate**: All features are locked behind session-based authentication.
- **Existence Checks**: Every update and delete operation first verifies the record exists.
- **Duplicate Prevention**: Membership creation checks for an existing membership on the same `member_id`.
- **Cascaded Deletion**: Deleting a member first removes their `gym_membership` record to prevent orphan rows.
- **Input Validation**: All form fields are validated before any SQL query is constructed.

### ⚡ Application Structure

```
FitDesk/
│
├── app.py                  # Main Streamlit application (all logic)
├── requirements.txt        # Python dependencies
├── static/
│   └── images/
│       └── gymphoto.jpg    # Background image asset
└── README.md
```

</section>

---

<!-- <section id="screenshots">


## Screenshots & App Demonstration

> 📸 *Add your screenshots here after running the app.*

<!-- Uncomment and replace paths once you have screenshots:
<img src="screenshots/login.png" width="200"/>
<img src="screenshots/members.png" width="200"/>
<img src="screenshots/add_member.png" width="200"/>
<img src="screenshots/membership.png" width="200"/>
<img src="screenshots/trainers.png" width="200"/>


</section>
-->
---

<section id="conclusion">

## Conclusion

The **FitDesk** successfully delivers a complete, database-driven admin platform for gym operations. By combining the simplicity of **Streamlit** with the reliability of **MySQL**, the system handles all core gym workflows — member onboarding, membership control, trainer management, and class administration — in one unified interface.

The project demonstrates practical application of DBMS concepts including normalization, foreign key constraints, relational integrity, and CRUD operations, while maintaining a clean and accessible user experience entirely within Python.

</section>

---

<section id="team">

## The Team

### Suhas Varna
<p>
  <a href="https://github.com/Suhas-Varna">
    <img src="https://img.shields.io/badge/GitHub-black?style=flat&logo=github" alt="GitHub"/>
  </a>
  <a href="https://www.linkedin.com/in/suhas-varna2003/">
    <img src="https://img.shields.io/badge/LinkedIn-blue?style=flat&logo=linkedin" alt="LinkedIn"/>
  </a>
</p>

### Seeripi Ganesh Kumar
<p>
  <a href="">
    <img src="https://img.shields.io/badge/GitHub-black?style=flat&logo=github" alt="GitHub"/>
  </a>
  <a href="">
    <img src="https://img.shields.io/badge/LinkedIn-blue?style=flat&logo=linkedin" alt="LinkedIn"/>
  </a>
</p>

### Vikas D H
<p>
  <a href="">
    <img src="https://img.shields.io/badge/GitHub-black?style=flat&logo=github" alt="GitHub"/>
  </a>
  <a href="">
    <img src="https://img.shields.io/badge/LinkedIn-blue?style=flat&logo=linkedin" alt="LinkedIn"/>
  </a>
</p>

### Sanjay J
<p>
  <a href="">
    <img src="https://img.shields.io/badge/GitHub-black?style=flat&logo=github" alt="GitHub"/>
  </a>
  <a href="">
    <img src="https://img.shields.io/badge/LinkedIn-blue?style=flat&logo=linkedin" alt="LinkedIn"/>
  </a>
</p>

</section>
