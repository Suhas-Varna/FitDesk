<!-- BANNER / HEADER -->
<h1 align="center">🏋️‍♂️ Gym Management System</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/Streamlit-App-red?logo=streamlit&logoColor=white" />
  <img src="https://img.shields.io/badge/MySQL-Database-orange?logo=mysql&logoColor=white" />
  <img src="https://img.shields.io/badge/Status-Active-success?style=flat-square" />
</p>

<p align="center">
  <b>Manage your gym members, trainers, and memberships all in one place — with Python, Streamlit & MySQL</b>
</p>

---

## 🧩 Overview  

The **Gym Management System** is a lightweight web app built using **Python** and **Streamlit**, backed by a **MySQL database**.  
It provides an intuitive interface for managing gym members, memberships, trainers, and workout classes — including secure login authentication.

---

## 🚀 Features  

- 🔐 **User Login Authentication** (email/password)
- 👤 **Member Management** — Add, update, or delete member info  
- 💳 **Membership Management** — One-to-One relationship with members  
- 🏋️ **Trainer Management** — Add and manage trainers  
- 🧘 **Workout Class Management**  
- 🏢 **Gym Branch Info**  
- ⚠️ **Duplicate Membership Prevention**  
- 💾 **Real-time MySQL Database Updates**

---

## 🧠 Tech Stack  

| Layer | Technology |
|-------|-------------|
| **Frontend / UI** | Streamlit |
| **Backend** | Python |
| **Database** | MySQL |
| **Libraries** | `mysql-connector-python`, `pandas`, `streamlit` |

---

## 🧱 Database Design  

### Entities & Relationships  

| Entity | Description |
|---------|-------------|
| 🧍‍♂️ **Member** | Stores member details (name, gender, age, etc.) |
| 💳 **Gym_Membership** | One-to-one link with member; includes price, start & end date |
| 🏢 **Gym** | Stores gym branch details |
| 🏋️ **Trainer** | Contains trainer data |
| 🧘 **Workout_Class** | Lists workout programs |
| 🔑 **User** *(for login)* | Holds credentials for authentication |

### ER Model  
- `Member` 🔗 `Gym_Membership` → **1 : 1**  
- `Gym` 🔗 `Gym_Membership` → **1 : N**  
- `Trainer` 🔗 `Workout_Class` → **1 : N**  

---

## ⚙️ Installation & Setup  

### 🧾 Prerequisites  
- Python 3.x  
- MySQL Server installed and running  
- Streamlit installed (`pip install streamlit`)  

### 🔧 Steps  

```bash
# 1️⃣ Clone the repository
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>

# 2️⃣ Install dependencies
pip install -r requirements.txt

# 3️⃣ Configure your MySQL credentials in app.py
host='localhost'
user='root'
password='your_password'
database='suhasvarna'

# 4️⃣ Run the Streamlit app
streamlit run app.py
