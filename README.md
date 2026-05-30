<p align="center">
  <h1 align="center">BPARK — Automated Parking Management System</h1>
  <p align="center">
    A full-stack Client–Server parking management platform built with <strong>Java</strong>, <strong>JavaFX</strong>, and <strong>MySQL</strong>
  </p>
  <p align="center">
    <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java"/>
    <img src="https://img.shields.io/badge/JavaFX-007396?style=for-the-badge&logo=java&logoColor=white" alt="JavaFX"/>
    <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL"/>
    <img src="https://img.shields.io/badge/OCSF-Network_Framework-blueviolet?style=for-the-badge" alt="OCSF"/>
  </p>
</p>

---

## About

BPARK is an automated parking management system developed as a **semester project**. The system manages an automated parking facility end-to-end — vehicle drop-off and pickup, subscriber management, advance reservations, real-time capacity tracking, and operational reporting — all through an intuitive desktop interface.

**[Watch the System Demo Video](https://drive.google.com/file/d/13_XR9LdSh5GGeLFC7yP5YkBkM1SzHsdD/view)**

---

## Key Features

### User Management
- Registration of new subscribers via a parking attendant
- Unique subscriber ID and quick-access code generation
- Profile viewing and editing for subscribers
- Automatic account deactivation after **3 late pickups**

### Vehicle Drop-off & Pickup
- Identification via terminal or tag reader (simulated)
- Automatic parking code and confirmation code generation
- Default parking time with in-session extension options
- Lost parking code recovery via **email notification**
- Late pickup tracking with delay history

### Parking Reservations
- Advance reservations from **24 hours** up to **7 days** ahead
- Reservation allowed only when **≥ 40% capacity** is available
- Automatic cancellation if the user does not arrive on time (checked every 10 minutes)

### Reports & Analytics
- Monthly parking duration reports
- Subscriber activity and usage statistics
- Free space tracking and capacity monitoring
- Administrative dashboard for parking managers

---

## Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    BPARK System                         │
│                                                         │
│  ┌──────────────┐    TCP/IP (OCSF)   ┌──────────────┐  │
│  │              │◄──────────────────►│              │  │
│  │  JavaFX      │   Port 5555        │  Java        │  │
│  │  Client      │                    │  Server      │  │
│  │  (Desktop)   │                    │  (Backend)   │  │
│  │              │                    │              │  │
│  └──────────────┘                    └──────┬───────┘  │
│                                             │          │
│                                      ┌──────▼───────┐  │
│                                      │   MySQL 8.0  │  │
│                                      │   Database   │  │
│                                      │   (bpark)    │  │
│                                      └──────────────┘  │
└─────────────────────────────────────────────────────────┘
```

| Layer | Technology | Description |
|-------|-----------|-------------|
| **Frontend** | JavaFX + FXML | 23 screens with modern styled UI |
| **Networking** | OCSF Framework | TCP/IP client–server communication |
| **Backend** | Java | Business logic, scheduling, validation |
| **Database** | MySQL 8.0 | Relational storage with transaction support |
| **Email** | Jakarta Mail | SMTP notifications via Gmail |

---

## User Roles

| Role | Access Level | Key Capabilities |
|------|-------------|-------------------|
| **Subscriber** | Standard | Drop-off, pickup, reservations, profile management |
| **Attendant** | Staff | Register new subscribers, assist with operations |
| **Manager** | Admin | View reports, monitor system usage, manage subscribers |

---

## Project Structure

```
BPARK-main/
│
├── G14_Server/                    # Server module
│   └── src/
│       ├── server/
│       │   ├── BParkServer.java          # Main server — business logic (1,700+ lines)
│       │   ├── EmailSender.java          # Gmail SMTP email service
│       │   └── ServerUI.java             # Server launch & display
│       └── common/
│           ├── ClientRequest.java        # 22 request type definitions
│           └── ChatIF.java               # Communication interface
│
├── G14_Clien/                     # Client module
│   └── src/
│       ├── client/
│       │   ├── BParkClient.java          # OCSF client handler
│       │   └── ClientUI.java             # Client initialization
│       ├── clientGui/                    # 46 UI files (23 FXML + 23 Controllers)
│       │   ├── BparkHome.fxml            # Main entry screen
│       │   ├── ClientDropOff.fxml        # Vehicle drop-off
│       │   ├── ClientPickUp.fxml         # Vehicle pickup
│       │   ├── ClientReservationUi.fxml  # Reservations
│       │   ├── ParkingTimeReport.fxml    # Reports
│       │   └── ...                       # Additional screens
│       └── common/                       # Shared data models
│           ├── User.java                 # User account model
│           ├── Subscriber.java           # Subscription model
│           ├── Parking.java              # Parking session model
│           ├── Reservation.java          # Reservation model
│           ├── ParkingSpace.java         # Parking space model
│           └── ...                       # Additional models
│
├── G14_client.jar                 # Compiled client (ready to run)
├── G14_server.jar                 # Compiled server (ready to run)
└── G14__Assignment2.vpp           # UML diagrams (Visual Paradigm)
```

---

## Database Schema

| Table | Purpose |
|-------|---------|
| `user` | Account credentials, personal details, and role assignment |
| `subscriber` | Subscription codes, quick-access codes, registration dates, delay tracking |
| `parking` | Active and past parking sessions, confirmation codes, extensions |
| `parking_space` | Lot layout, space numbering, occupancy status |
| `reservation` | Advance bookings with time windows, status, and confirmation |
| `message` | System notifications and alerts |

---

## Getting Started

### Prerequisites

- **Java JDK 8+** with JavaFX support
- **MySQL 8.0** server running locally
- **Eclipse IDE** (recommended) or any Java IDE

### Database Setup

1. Create the database:
   ```sql
   CREATE DATABASE bpark;
   ```
2. Configure the connection in `BParkServer.java` (default: `localhost:3306`, user `root`)

### Running the Application

**Option A — Using pre-built JARs:**

```bash
# Start the server
java -jar G14_server.jar

# Start the client (in a separate terminal)
java -jar G14_client.jar
```

**Option B — From source (Eclipse):**

1. Import `G14_Server` and `G14_Clien` as existing Eclipse projects
2. Add `mysql-connector-java-8.0.13.jar` from `lib/` to the build path
3. Run `ServerUI.java` to start the server
4. Run `ClientUI.java` to start the client
5. Connect the client to `localhost` on port `5555`

---

## Tech Stack

| Category | Technology |
|----------|-----------|
| Language | Java |
| UI Framework | JavaFX + FXML |
| Network Layer | OCSF (Object Client-Server Framework) |
| Database | MySQL 8.0 |
| DB Connector | mysql-connector-java 8.0.13 |
| Email Service | Jakarta Mail 2.0.1 (Gmail SMTP) |
| IDE | Eclipse |
| Design & UML | Visual Paradigm |


---

<p align="center">
  <sub>Developed as a semester project &bull; Client–Server Architecture &bull; Designed for future web & mobile expansion</sub>
</p>
