# Transport Management System (TMS)

A desktop-based enterprise management solution designed to optimize, automate, and streamline logistics and public/private transit operations. Built with **Python (PyQt5)** and powered by a robust **Microsoft SQL Server (MSSQL)** database layer, this project provides a multi-role workspace for Administrators, Passengers, Drivers, and Maintenance personnel.

---

## 🛠️ Technology Stack

* **Front-end / GUI:** Python & PyQt5 (Desktop Interface)
* **Back-end Logic:** Python 3 (Object-Oriented Architecture)
* **Database Management:** Microsoft SQL Server (MS SQL LocalDB or Express Edition)
* **Database Connector:** `pyodbc`
* **Data Visualization:** `matplotlib` (for generating administration analytical reports)
* **Report Generation:** `reportlab` (for compiling billing and payment PDF invoices)
* **Security:** `bcrypt` (secure cryptographic hashing of passwords) and `cryptography`

---

## 📋 Features

The system supports four distinct user portals:

### 1. 🔑 Administrator Portal
* **Fleet Management:** Complete CRUD operations for vehicles, managing capacities, models, fuel types, and availability.
* **Driver Management:** Track driver registration details, licenses, status, and vehicle assignments.
* **Route & Schedule Management:** Plan travel routes (distance, duration, status) and generate corresponding departure/arrival trip schedules.
* **Passenger Allocation & Booking:** Add passengers to specific route assignments and manage trip bookings.
* **Financial Controls & Invoicing:** Manage passenger balances, track payments, review transport fees, and auto-generate reports/graphs using Matplotlib.
* **GPS Tracking Log Panel:** Monitor trip statuses and detect route deviations.

### 2. 👥 Passenger Portal
* **Dashboard:** Check profile information, outstanding balance, and trip bookings.
* **Bookings:** Browse active route assignments and book seats instantly.
* **Billing & Payments:** Review transaction history, track unpaid monthly transport fees, and pay outstanding balances securely.

### 3. 🚛 Driver Portal
* **Trip Schedules:** View assigned route details, schedules, and active duty statuses.
* **Maintenance Reporting:** Instantly report mechanical issues and submit vehicle inspection reports directly to the maintenance department.

### 4. 🔧 Maintenance Portal
* **Inspection Panel:** View incoming maintenance logs reported by drivers.
* **Repair Scheduler:** Assign vehicles to specific maintenance statuses, record scheduled repairs, and track final cost calculations.

---

## 🗄️ Database Architecture

The database engine runs on **Microsoft SQL Server** with a schema consisting of **13 interrelated tables** optimized with proper foreign key relationships, constraints, and cascade delete rules:

| Table | Purpose |
|---|---|
| `users` | Houses system user authentication details & roles |
| `vehicles` | Fleet inventory including status, capacity, and mileage |
| `drivers` | Driver logs, licenses, and assigned vehicle relations |
| `routes` | Travel routes (origin, destination, distance, estimated time) |
| `assignments` | Core linking model mapping vehicles, drivers, and routes |
| `schedules` | Trip timetables with departure/arrival logs |
| `passengers` | Customer records and outstanding financial balances |
| `bookings` | Seats reserved on assignments by passengers |
| `transport_fees` | Outstanding monthly billing cycles generated for passengers |
| `payments` | Records payment transaction history and payment methods |
| `fuel_logs` | Vehicle fuel usage, odometer readings, and costs |
| `maintenance_records` | Diagnostic logs, scheduler details, and repair costs |
| `tracking_logs` | Live coordinates and deviation logs for active trips |

> 📊 For full schema specifications, fields, and ER diagrams, refer to the [Database Schema Documentation](DATABASE_SCHEMA.md).

---

## 📂 Project Directory Structure

```text
TransportManagementSystem/
├── main.py                                  # Application entry point
├── config.py                                # Environment configurations & DB connections
├── setup_database.py                        # DB initialization & seeding script
├── requirements.txt                         # Application Python dependencies
├── CREDENTIALS.md                           # System demo user login information
├── DATABASE_SCHEMA.md                       # Markdown database schema documentation
├── assets/
│   └── styles/
│       └── theme.qss                        # Application stylesheet / UI Theme
├── controllers/                             # Handlers intermediate between views & database
├── database/
│   ├── db_handler.py                        # Database singleton connector utility
│   └── schema.sql                           # Idempotent T-SQL database creation script
├── models/                                  # Database access layer and query configurations
├── services/                                # Core business and transactional logic
├── utils/                                   # Shared utility functions (e.g. hashing)
└── views/                                   # PyQt5 UI views and dashboard components
    ├── admin/                               # Views for the administrator dashboard
    ├── driver/                              # Views for the driver dashboard
    ├── maintenance/                         # Views for the maintenance dashboard
    └── passenger/                           # Views for the passenger dashboard
```

---

## 🔧 Installation & Setup

### Prerequisites

* **OS:** Windows (Required for Local SQL Server Windows Authentication & PyQT5 components)
* **Python:** Python 3.8 or higher installed.
* **Database Server:** MS SQL Server (e.g., LocalDB or Developer/Express version `localhost\SQLEXPRESS`).
* **ODBC Driver:** ODBC Driver 17 for SQL Server.

### Installation Steps

1. **Install Dependencies:**
   Install required packages via pip:
   ```bash
   pip install -r requirements.txt
   ```

2. **Configure Database Connection:**
   Open `config.py` and modify connection settings (e.g., Server Name, Database Name, Authentication) or set them as environment variables if needed:
   * `MSSQL_SERVER`: Defaults to `localhost\SQLEXPRESS`
   * `MSSQL_DATABASE`: Defaults to `TransportDB`
   * `MSSQL_DRIVER`: Defaults to `ODBC Driver 17 for SQL Server`

3. **Initialize the Database:**
   Run the setup script. This script automatically checks and creates the SQL database, executes the database schema, and seeds default user credentials:
   ```bash
   python setup_database.py
   ```

4. **Launch the Application:**
   Start the desktop GUI application:
   ```bash
   python main.py
   ```

---

## 🔑 Demo User Credentials

The database comes pre-seeded with the following testing users:

* **Default Password for all accounts:** `Pass@123`

| Username | Role | Purpose |
|---|---|---|
| `admin` | Administrator | Full backend access, fleet management, and finance |
| `driver01` | Driver | Driver interface, trip logs, issue reporting |
| `passenger01` | Passenger | Seat booking, payment portal, billing history |
| `maint01` | Maintenance | Repairs, vehicle inspections, workshop management |

> 📝 For a complete breakdown of credentials and access roles, see [CREDENTIALS.md](CREDENTIALS.md).
