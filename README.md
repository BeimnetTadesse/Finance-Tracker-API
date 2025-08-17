Perfect! I’ve added the **Profile** and **User Stats** endpoints to the formal documentation. Here’s the updated version:

---

# Finance Tracker API Documentation

**Finance Tracker API** is a personal finance management backend built with Django REST Framework. It enables users to securely track and manage their expenses, income, budgets, categories, and savings goals. All endpoints are designed for authenticated users with JWT-based security.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Base URL](#base-url)
3. [Authentication Endpoints](#authentication-endpoints)
4. [Profile & User Stats](#profile--user-stats)
5. [Categories](#categories)
6. [Transactions](#transactions)
7. [Budgets](#budgets)
8. [Savings Goals](#savings-goals)
9. [Tech Stack](#tech-stack)
10. [Notes](#notes)

---

## Introduction

The Finance Tracker API provides a secure and organized way to manage personal finances. Users can:

* Register and authenticate accounts
* Categorize transactions
* Record and view income and expenses
* Set monthly budgets per category
* Track savings goals and progress

---

## Base URL

```
http://127.0.0.1:8000/api/
```

All endpoints are prefixed with `/api/`.

---

## Authentication Endpoints

These endpoints handle **user registration and authentication** using JWT.

| Endpoint                   | Method | Description                                       |
| -------------------------- | ------ | ------------------------------------------------- |
| `/accounts/register/`      | POST   | Register a new user account                       |
| `/accounts/login/`         | POST   | Log in and receive access & refresh tokens        |
| `/accounts/token/refresh/` | POST   | Refresh your access token using the refresh token |

### JWT Tokens

* **Access Token**: Short-lived token used for authenticated requests.
* **Refresh Token**: Used to obtain a new access token without logging in again.

**Example Authorization Header**:

```
Authorization: Bearer <access_token>
```

---

## Profile & User Stats

Manage user profile and view personal statistics.

| Endpoint             | Method      | Description                           |
| -------------------- | ----------- | ------------------------------------- |
| `/accounts/profile/` | GET         | Retrieve logged-in user’s profile     |
| `/accounts/profile/` | PUT / PATCH | Update logged-in user’s profile       |
| `/core/stats/`       | GET         | Retrieve stats for the logged-in user |

---

## Categories

Manage custom categories for organizing transactions.

| Endpoint                 | Method | Description                 |
| ------------------------ | ------ | --------------------------- |
| `/core/categories/`      | GET    | List all categories         |
| `/core/categories/`      | POST   | Create a new category       |
| `/core/categories/{id}/` | GET    | Retrieve a single category  |
| `/core/categories/{id}/` | PUT    | Update a category           |
| `/core/categories/{id}/` | PATCH  | Partially update a category |
| `/core/categories/{id}/` | DELETE | Delete a category           |

---

## Transactions

Track income and expenses efficiently.

| Endpoint                   | Method | Description                    |
| -------------------------- | ------ | ------------------------------ |
| `/core/transactions/`      | GET    | List all transactions          |
| `/core/transactions/`      | POST   | Create a new transaction       |
| `/core/transactions/{id}/` | GET    | Retrieve a single transaction  |
| `/core/transactions/{id}/` | PUT    | Update a transaction           |
| `/core/transactions/{id}/` | PATCH  | Partially update a transaction |
| `/core/transactions/{id}/` | DELETE | Delete a transaction           |

---

## Budgets

Set monthly limits for spending per category.

| Endpoint              | Method | Description               |
| --------------------- | ------ | ------------------------- |
| `/core/budgets/`      | GET    | List all budgets          |
| `/core/budgets/`      | POST   | Create a new budget       |
| `/core/budgets/{id}/` | GET    | Retrieve a single budget  |
| `/core/budgets/{id}/` | PUT    | Update a budget           |
| `/core/budgets/{id}/` | PATCH  | Partially update a budget |
| `/core/budgets/{id}/` | DELETE | Delete a budget           |

---

## Savings Goals

Monitor progress toward financial goals.

| Endpoint            | Method | Description               |
| ------------------- | ------ | ------------------------- |
| `/core/goals/`      | GET    | List all goals            |
| `/core/goals/`      | POST   | Create a new savings goal |
| `/core/goals/{id}/` | GET    | Retrieve a specific goal  |
| `/core/goals/{id}/` | PUT    | Update a goal             |
| `/core/goals/{id}/` | PATCH  | Partially update a goal   |
| `/core/goals/{id}/` | DELETE | Delete a goal             |

---

## Tech Stack

* Django & Django REST Framework
* JWT Authentication (`djangorestframework-simplejwt`)
* MySQL or PostgreSQL (depending on deployment)

---

## Notes

* All endpoints **except registration, login, and token refresh** require JWT authentication.
* All data returned is scoped to the authenticated user.
* Include the **access token** in the `Authorization` header for secure requests:

  ```
  Authorization: Bearer <access_token>
  ```

---

