# Authentication System with Flask-Login

This repository demonstrates a basic authentication system using Flask-Login. It includes user registration, login, logout functionality, and session management.

---

## Table of Contents

- [Introduction](#introduction)
- [Dependencies](#dependencies)
- [Application Structure](#application-structure)
- [Database Model](#database-model)
- [Routes](#routes)
  - [/register - User Registration](#register---user-registration)
  - [/login - User Login](#login---user-login)
  - [/logout - User Logout](#logout---user-logout)
  - [/ - Home Page](#---home-page)
- [Authentication Logic](#authentication-logic)
  - [Login Process](#login-process)
  - [Logout Process](#logout-process)
- [How to Run](#how-to-run)
- [Templates](#templates)
  - [signup.html](#signuphtml)
  - [login.html](#loginhtml)
  - [index.html](#indexhtml)
- [Security Notes](#security-notes)
- [Improvements](#improvements)
- [Preview](#preview)

---

## Introduction

This Flask application implements a simple authentication system using the Flask-Login extension. It supports the following functionalities:

- User registration
- User login
- User logout
- Session management

User credentials are stored in an SQLite database.

---

## Dependencies

To run this application, ensure you have the following libraries installed:

- **Flask**: Core framework for the application.
- **Flask-SQLAlchemy**: ORM for interacting with the SQLite database.
- **Flask-Login**: Handles user authentication and session management.

Install these dependencies using:

```bash
pip install flask flask-sqlalchemy flask-login
```

## **Application Structure**
  1. Configurations
      SQLALCHEMY_DATABASE_URI: Specifies the SQLite database file path (db.sqlite).
      SECRET_KEY: Secret key used for securing session cookies.
  2. Database Models
  The application uses the Users model to manage user data.
  ```
  class Users(UserMixin, db.Model):
      id = db.Column(db.Integer, primary_key=True)
      username = db.Column(db.String(250), unique=True, nullable=False)
      password = db.Column(db.String(250), nullable=False)
  ```
  Fields:
    - id: Unique identifier for each user.
    - username: Stores the username, must be unique.
    - password: Stores the user's password (in plaintext for now; should be hashed in a production environment).
    
## **Routes**
  *a. /register*
  Handles user registration.
  Methods: GET, POST
  GET: Displays the registration form (signup.html).
  POST: Adds a new user to the database and redirects to the login page.<br>
  
  *b. /login*
  Handles user login.
  Methods: GET, POST
  GET: Displays the login form (login.html).
  POST: Verifies the user credentials. If valid, logs the user in and redirects to the home page.

  *c. /logout*
  Logs out the current user.
  Methods: GET
  Redirects the user to the home page.

  *d. / (Home Page)*
  The landing page of the application.
  Methods: GET
  Renders the index.html template.

## **Authentication Logic**
  Flask-Login Setup
  LoginManager: Initializes Flask-Login and manages user sessions.
  @login_manager.user_loader: Loads the user from the database using their ID.
  Login Process
  The user provides their credentials.
  The system verifies the username and password.
  If valid, the user session is initiated using login_user(user).
  Logout Process
  The logout_user() function ends the session and clears the user data.
   
## **How to Run**
Save the code in a file, e.g., app.py.
Run the application using:
    ```
    python app.py
    ```
Open the application in your browser at http://127.0.0.1:5000.
Templates

a. signup.html
Form for user registration with fields for username and password.

b. login.html
Form for user login with fields for username and password.

c. index.html
Home page template for the application.

## **Security Note**
Do not store passwords as plaintext. Use hashing algorithms like bcrypt or Argon2 to securely store passwords.
Implement additional validation to handle empty or invalid inputs.

6. Improvements
  - Add password hashing for security.
  - Improve the user interface with Bootstrap or other frontend frameworks.
  - Implement user-specific pages or content.
  - Add error handling for invalid login or registration attempts.


<h1 align="center">Preview</h1>

## Login
![image](https://github.com/user-attachments/assets/731038af-43f3-49ba-8cdf-7bb234cea8ee)

## Register
![image](https://github.com/user-attachments/assets/27e707fe-7559-4263-beb1-34ec4c517d5b)
