Project Name

Gym Management System

Overview

A web-based Gym Management System built with Python, Streamlit for the UI and MySQL as the relational database. The system allows management of members, trainers, workout classes, gym branches and memberships through a clean dashboard.

Features

Add / View / Update / Delete Members

Add / View / Update / Delete Trainers

Add / View / Update / Delete Workout Classes

Add / View / Update / Delete Memberships (one-to-one mapping with members)

Gym branch data management

Basic authentication (login) for access control

Architecture & Workflow

The backend uses MySQL to store structured tables (members, membership, trainers, gyms, workout_class).

Streamlit provides an interactive front-end: menus in the sidebar, forms to input CRUD data, dataframes to display queries.

On each request, the system connects to MySQL, runs queries and closes the connection (via a helper function).

Validation and integrity checks are done both at the application level (e.g., duplicate membership prevention) and via database constraints (primary/foreign keys).

Login page gate-keeps access; once logged in the user sees the main dashboard.

Database Schema

member (member_id PK, name, gender, age, phone_no, address)

gym_membership (membership_id, member_id PK composite; start_date; end_date; price; gym_name FK) One-to-one with member

gym (name PK, address)

trainer (trainer_id PK, name, age, phone_no)

workout_class (workout_id PK, workout_name)

Optionally: users table if authentication is more formal (email PK, password)
