# 🚗 BPARK – Automated Parking Management System

BPARK is an automated parking management system developed as a **semester project** 

The system is designed to manage an automated parking facility, including vehicle drop-off and pickup,
subscriber management, parking reservations, and operational reporting.

---

## 🎯 Project Goals

- Efficient management of an automated parking lot
- Support for subscribers and occasional users
- Real-time tracking of parking availability
- Reservation and parking time extension services
- Generation of operational and statistical reports
- Design with future web and mobile expansion in mind

---

## 🧩 System Overview

BPARK supports the following core functionalities:

### 👤 User Management
- Initial registration via parking attendant
- Unique subscriber ID generation
- Storage of personal details and parking history
- Limited profile editing for subscribers

### 🚘 Vehicle Drop-off & Pickup
- Identification via terminal or tag reader (simulated)
- Automatic parking code generation
- Default parking time with extension options
- Lost parking code recovery via email/SMS

### 📅 Parking Reservation
- Advance reservations (24 hours to 7 days)
- Reservation allowed only if at least 40% capacity is available
- Automatic cancellation if the user does not arrive on time

### 📊 Information & Reports
- Monthly parking duration reports
- Subscriber activity statistics
- Visual representation of system usage
- Administrative access for parking managers

---

## 🏗️ Architecture

- **Architecture style:** Client–Server (Full Stack)
- **Backend:** Java, relational database
- **Frontend:** Desktop-based UI (non-web, Phase 1)
- **Communication:** LAN-based TCP/IP
- **External devices:** Simulated (e.g., tag reader)

The system is developed in a way that allows **easy migration to Web and Mobile platforms** in future phases.

---

## 🛠️ Technologies

- Java (Eclipse)
- Object-Oriented Programming (OOP)
- UML (Class, Activity, Swimlane diagrams)
- Relational Database (SQL)
- Client–Server architecture

---

## 🎥 System Demonstration

A short video explaining the system architecture, core features,
and user interaction flow is available here:

▶️ [Watch the system explanation video](https://drive.google.com/file/d/13_XR9LdSh5GGeLFC7yP5YkBkM1SzHsdD/view)

