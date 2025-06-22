# Airbnb Clone Backend – StayBackend Project

## Project Overview
The Airbnb Clone project, **StayBackend**, is a backend-focused web development challenge designed to simulate building a robust and scalable property rental platform. This clone of Airbnb focuses on essential backend concepts including API development, database design, CI/CD, and security.

**Project Goals:**
- Build a scalable and secure backend using Django.
- Design a relational database with real-world booking relationships.
- Enable robust CI/CD pipelines and security practices.
- Foster collaboration through GitHub workflows.

---

## Team Roles

| Role | Description |
|------|-------------|
| **Backend Developer** | Responsible for implementing the application logic, setting up the Django project, creating API endpoints, and integrating with the database. |
| **Database Administrator (DBA)** | Designs the MySQL database schema, defines relationships, optimizes queries, and ensures data consistency and integrity. |
| **DevOps Engineer** | Sets up Docker containers, manages GitHub Actions workflows, and ensures automated deployments through CI/CD pipelines. |
| **Security Analyst** | Focuses on securing APIs, enforcing authentication and authorization, and applying best practices like rate limiting and input validation. |
| **Project Manager** | Coordinates the workflow, oversees task distribution, and ensures the team meets deadlines while maintaining quality standards. |

---

## Technology Stack

| Technology | Purpose |
|------------|---------|
| **Django** | A high-level Python web framework used to build the RESTful APIs for the application. |
| **MySQL** | The relational database system for storing users, properties, bookings, payments, and reviews. |
| **GraphQL** | Optional advanced API query language for flexible data retrieval in future versions. |
| **Docker** | Containerization tool to ensure consistent development and deployment environments. |
| **GitHub Actions** | CI/CD platform used to automate testing, building, and deployment processes. |
| **Postman** | Tool for testing and documenting APIs during development. |

---

## Database Design

### 📊 Entities and Fields

#### 1. Users
- `id` (PK)
- `username`
- `email`
- `password_hash`
- `is_host` (Boolean)

#### 2. Properties
- `id` (PK)
- `owner_id` (FK → Users)
- `title`
- `description`
- `location`
- `price_per_night`

#### 3. Bookings
- `id` (PK)
- `user_id` (FK → Users)
- `property_id` (FK → Properties)
- `check_in_date`
- `check_out_date`
- `total_price`

#### 4. Reviews
- `id` (PK)
- `user_id` (FK → Users)
- `property_id` (FK → Properties)
- `rating`
- `comment`

#### 5. Payments
- `id` (PK)
- `booking_id` (FK → Bookings)
- `amount`
- `payment_method`
- `payment_status`

### 🔗 Relationships
- One user can list many properties.
- One user can make multiple bookings.
- Each booking is linked to one property.
- A property can have many reviews and bookings.
- Payments are tied to bookings.

---

## Feature Breakdown

| Feature | Description |
|---------|-------------|
| **User Management** | Allows users to sign up, log in, manage profiles, and become hosts. Authentication and authorization are enforced. |
| **Property Management** | Hosts can list, update, and delete property listings. Users can browse properties based on filters. |
| **Booking System** | Users can book properties for specific dates and receive confirmation with pricing. |
| **Reviews and Ratings** | After a stay, users can rate and review properties, enhancing the platform’s trust and quality. |
| **Payment Handling** | Payments are processed for bookings, including tracking of payment status, amount, and method. |
| **Admin Tools** | Optional admin dashboard for managing listings, bookings, and users (if time permits). |

---

## API Security

| Measure | Purpose |
|--------|---------|
| **Authentication (JWT)** | Ensures only registered users can access protected routes (e.g., bookings, reviews). |
| **Authorization** | Role-based access: hosts can manage their listings, users can only book/review, admins can manage the platform. |
| **Rate Limiting** | Prevents abuse by limiting the number of requests per user/IP in a given time. |
| **Input Validation** | Prevents SQL injections, XSS, and other attacks by sanitizing inputs at all API layers. |
| **HTTPS Enforcement** | All API endpoints must be accessed securely over HTTPS to protect data in transit. |

**Why Security Matters:**
- Protects sensitive user data (emails, passwords, payment info).
- Ensures trust in transaction processes (booking/payment).
- Prevents abuse and denial-of-service scenarios.
- Maintains integrity of the booking platform.

---

## CI/CD Pipeline

### 🚀 Overview
CI/CD (Continuous Integration/Continuous Deployment) helps automate the build, test, and deployment phases of development. This leads to faster iteration, early bug detection, and reduced deployment errors.

### 🛠️ Tools Used
- **GitHub Actions**: Automates tests on every push or pull request.
- **Docker**: Ensures consistent environments for development and deployment.
- **PostgreSQL/MySQL Service Containers**: Used for automated DB testing in CI.
- **Heroku/DigitalOcean (optional)**: Used for deployment after CI pipeline passes.

### 📈 CI/CD Workflow
1. **Developer pushes code to GitHub.**
2. **GitHub Actions runs test suites.**
3. **Docker builds application container.**
4. **If successful, deploys to hosting service.**

---
-
