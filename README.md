# 🚍 Transport Management System (TMS)

A desktop-based **Transport Management System (TMS)** developed to simplify and automate fleet, passenger, and transportation operations. Built using **Python (PyQt5)** with **Microsoft SQL Server (MSSQL)** as the database, the application provides dedicated dashboards for **Administrators, Passengers, Drivers, and Maintenance Staff**, making day-to-day transport management more efficient and organized.

---

## Tech Stack

- **Programming Language:** Python 3
- **GUI Framework:** PyQt5
- **Database:** Microsoft SQL Server (LocalDB / Express Edition)
- **Database Connectivity:** pyodbc
- **Visualization:** Matplotlib
- **PDF Report Generation:** ReportLab
- **Security:** bcrypt & cryptography

---

## Key Features

The application includes four role-based portals, each designed for a specific user group.

##  Administrator Portal

The administrator has complete control over the system and can manage all transport operations.

### Features

- Manage vehicles with full Create, Read, Update, and Delete (CRUD) functionality.
- Register and manage drivers, licenses, and vehicle assignments.
- Create and manage travel routes and schedules.
- Allocate passengers and manage transport bookings.
- Monitor passenger payments, balances, and transport fees.
- Generate financial reports and analytics using Matplotlib.
- View GPS tracking logs and monitor trip progress.

---

## Passenger Portal

Passengers can easily manage their transport services through a simple dashboard.

### Features

- View personal profile and account information.
- Browse available routes and reserve seats.
- Check booking history.
- View outstanding transport fees.
- Make payments and review transaction history.

---

##  Driver Portal

Drivers have access to their assigned duties and reporting tools.

### Features

- View assigned routes and schedules.
- Check duty status.
- Submit vehicle inspection reports.
- Report maintenance issues directly to the maintenance department.

---

##  Maintenance Portal

The maintenance dashboard helps workshop staff efficiently manage repairs.

### Features

- Review maintenance requests submitted by drivers.
- Schedule vehicle repairs.
- Update repair progress and maintenance status.
- Record repair costs and maintenance history.

---

#  Database Design

The system uses **Microsoft SQL Server** as its backend database and consists of **13 interconnected tables** linked through foreign keys and relational constraints.

| Table | Description |
|------|-------------|
| `users` | Stores user login credentials and system roles |
| `vehicles` | Maintains fleet information, capacity, mileage, and availability |
| `drivers` | Stores driver details, licenses, and assigned vehicles |
| `routes` | Contains travel routes including origin, destination, and distance |
| `assignments` | Connects vehicles, drivers, and routes |
| `schedules` | Stores trip departure and arrival schedules |
| `passengers` | Maintains passenger records and balances |
| `bookings` | Records passenger seat reservations |
| `transport_fees` | Stores monthly transport billing information |
| `payments` | Keeps payment transactions and payment methods |
| `fuel_logs` | Tracks fuel consumption and costs |
| `maintenance_records` | Records maintenance requests and repair details |
| `tracking_logs` | Stores GPS tracking information and trip logs |

For complete table structures, relationships, and ER diagrams, refer to **DATABASE_SCHEMA.md**.

---

#  Project Structure

```text
TransportManagementSystem/
├── main.py
├── config.py
├── setup_database.py
├── requirements.txt
├── CREDENTIALS.md
├── DATABASE_SCHEMA.md
├── assets/
│   └── styles/
│       └── theme.qss
├── controllers/
├── database/
│   ├── db_handler.py
│   └── schema.sql
├── models/
├── services/
├── utils/
└── views/
    ├── admin/
    ├── driver/
    ├── maintenance/
    └── passenger/
```

---

#  Installation

## Prerequisites

Before running the project, ensure you have:

- Windows Operating System
- Python 3.8 or later
- Microsoft SQL Server (LocalDB, Express, or Developer Edition)
- ODBC Driver 17 for SQL Server

---

## Setup Instructions

### 1. Clone the Repository

```bash
git clone <repository-url>
cd TransportManagementSystem
```

### 2. Install Required Packages

```bash
pip install -r requirements.txt
```

### 3. Configure the Database

Update the database configuration in `config.py` or set the following environment variables:

- `MSSQL_SERVER`
- `MSSQL_DATABASE`
- `MSSQL_DRIVER`

Example:

```text
Server: localhost\SQLEXPRESS
Database: TransportDB
Driver: ODBC Driver 17 for SQL Server
```

### 4. Create the Database

Run the setup script:

```bash
python setup_database.py
```

This will automatically:

- Create the database (if it doesn't already exist)
- Create all required tables
- Apply relationships and constraints
- Insert sample data and demo accounts

### 5. Launch the Application

```bash
python main.py
```

---

#  Demo Credentials

**Default Password (All Accounts)**

```text
Pass@123
```

| Username | Role | Description |
|----------|------|-------------|
| `admin` | Administrator | Full system access |
| `driver01` | Driver | Driver dashboard |
| `passenger01` | Passenger | Booking and payment portal |
| `maint01` | Maintenance | Maintenance management |

For additional demo users and permissions, refer to **CREDENTIALS.md**.

---

# Project Highlights

- Role-based authentication and authorization
- Secure password hashing using **bcrypt**
- Encryption using the **cryptography** library
- Object-Oriented Python architecture
- Microsoft SQL Server relational database
- Modern PyQt5 desktop interface
- Fleet and vehicle management
- Route and schedule management
- Passenger booking system
- Payment and billing management
- PDF invoice generation
- Data visualization using Matplotlib
- Driver maintenance reporting
- GPS tracking and trip monitoring
