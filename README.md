# Software Requirements Specification
## For <project name>

Version 0.1  
Prepared by <author>  
<organization>  
<date created>  

Table of Contents
=================
* [Revision History](#revision-history)
* 1 [Introduction](#1-introduction)
  * 1.1 [Document Purpose](#11-document-purpose)
  * 1.2 [Product Scope](#12-product-scope)
  * 1.3 [Definitions, Acronyms and Abbreviations](#13-definitions-acronyms-and-abbreviations)
  * 1.4 [References](#14-references)
  * 1.5 [Document Overview](#15-document-overview)
* 2 [Product Overview](#2-product-overview)
  * 2.1 [Product Perspective](#21-product-perspective)
  * 2.2 [Product Functions](#22-product-functions)
  * 2.3 [Product Constraints](#23-product-constraints)
  * 2.4 [User Characteristics](#24-user-characteristics)
  * 2.5 [Assumptions and Dependencies](#25-assumptions-and-dependencies)
  * 2.6 [Apportioning of Requirements](#26-apportioning-of-requirements)
* 3 [Requirements](#3-requirements)
  * 3.1 [External Interfaces](#31-external-interfaces)
    * 3.1.1 [User Interfaces](#311-user-interfaces)
    * 3.1.2 [Hardware Interfaces](#312-hardware-interfaces)
    * 3.1.3 [Software Interfaces](#313-software-interfaces)
  * 3.2 [Functional](#32-functional)
  * 3.3 [Quality of Service](#33-quality-of-service)
    * 3.3.1 [Performance](#331-performance)
    * 3.3.2 [Security](#332-security)
    * 3.3.3 [Reliability](#333-reliability)
    * 3.3.4 [Availability](#334-availability)
  * 3.4 [Compliance](#34-compliance)
  * 3.5 [Design and Implementation](#35-design-and-implementation)
    * 3.5.1 [Installation](#351-installation)
    * 3.5.2 [Distribution](#352-distribution)
    * 3.5.3 [Maintainability](#353-maintainability)
    * 3.5.4 [Reusability](#354-reusability)
    * 3.5.5 [Portability](#355-portability)
    * 3.5.6 [Cost](#356-cost)
    * 3.5.7 [Deadline](#357-deadline)
    * 3.5.8 [Proof of Concept](#358-proof-of-concept)
* 4 [Verification](#4-verification)
  * 4.1 [Verification Methods](#41-verification-methods)
  * 4.2 [Test Plan Summary](#42-test-plan-summary)
* 5 [Appendixes](#5-appendixes)
  * Appendix A: [Glossary of Terms](#appendix-a-glossary-of-terms)
  * Appendix B: [Future Enhancements](#appendix-b-future-enhancements)
  * Appendix C: [Tools and Technologies](#appendix-c-tools-and-technologies)
  * Appendix D: [Document Control](#appendix-d-document-control)

---

## Revision History
| Name              | Date         | Reason For Changes              | Version   |
|-------------------|--------------|----------------------------------|-----------|
| J. Kruskie  | 2025-04-23   | Initial draft completed | 0.1       |

## 1. Introduction

This section provides an overview of the Software Requirements Specification (SRS) for the CheckED project. It introduces the document’s purpose, the scope of the software system, relevant definitions, references, and a guide to understanding the rest of this document.

### 1.1 Document Purpose

This document defines the functional and non-functional requirements for *CheckED*, a classroom inventory tracking system designed for educational environments. The purpose of this SRS is to outline a clear, structured vision of the system's features, interactions, and constraints to guide the student development team and stakeholders throughout the project lifecycle.

The intended audience includes:
- Students and faculty involved in the development and use of the system
- School IT staff responsible for system deployment and integration
- Reviewers providing feedback or grading the software project
- Future maintainers or contributors to the CheckED system

### 1.2 Product Scope

*CheckED* is a classroom asset management and inventory tracking solution that utilizes NFC technology to allow students to "check out" devices and materials by tapping their phones. The system will include a web-based administrative portal and a mobile application that interfaces with NFC tags placed on classroom devices.

Key goals and objectives of the product include:
- Streamlining the device checkout process using NFC-enabled smartphones
- Automatically associating students with checked-out items via Active Directory integration
- Providing a user-friendly interface for educators to monitor inventory status
- Supporting manual data entry and override options for flexibility
- Tracking parts, tools, and other educational resources in real time

By implementing CheckED, educators will gain an efficient, auditable, and accessible method to manage classroom resources while offering students hands-on experience with real-world software and hardware integration.

### 1.3 Definitions, Acronyms and Abbreviations

| Term | Definition |
|------|------------|
| NFC | Near Field Communication – a short-range wireless technology enabling data exchange between devices |
| AD | Active Directory – a Microsoft directory service used for user and device management |
| UI | User Interface |
| UX | User Experience |
| API | Application Programming Interface |
| SRS | Software Requirements Specification |

### 1.4 References

- IEEE Std 830-1998: IEEE Recommended Practice for Software Requirements Specifications  
- Microsoft Active Directory Documentation: https://docs.microsoft.com/en-us/windows-server/identity/ad-ds  
- NFC Forum Specifications: https://nfc-forum.org/our-work/specifications/  

### 1.5 Document Overview

The rest of this document is organized as follows:

- **Section 2: Product Overview** – Describes the context, functionality, constraints, users, and assumptions behind CheckED.
- **Section 3: Requirements** – Specifies detailed functional and non-functional requirements, interfaces, performance targets, and implementation constraints.
- **Section 4: Verification** – Describes how the system's features and behaviors will be verified.
- **Section 5: Appendices** – Contains supporting information or documentation not covered elsewhere in the SRS.

## 2. Product Overview

This section describes the general factors affecting the CheckED system and its requirements. It provides the context, functionality, user considerations, assumptions, and constraints relevant to the product. Specific technical and functional requirements are covered in Section 3.

### 2.1 Product Perspective

CheckED is a new, self-contained software product designed for classroom environments. It is not a replacement or continuation of an existing system. Instead, it introduces a novel integration of NFC technology with mobile and web-based applications for inventory tracking and device management in educational settings.

The product will consist of two main components:
- A **mobile application** that allows students to check out and return equipment by tapping NFC tags on classroom devices.
- A **web-based administrative portal** for educators and IT staff to manage inventory, view check-out logs, configure devices, and manually input data if needed.

CheckED will integrate with the school’s **local Active Directory (AD)** to validate users and associate check-outs with verified student accounts. It will also support manual override functionality for cases where NFC or AD connectivity is unavailable.

The system operates independently but may interact with institutional hardware (e.g., NFC-enabled devices, classroom computers) and directory services (e.g., AD servers). These external components must be accounted for in design and deployment planning.

### 2.2 Product Functions

CheckED will support the following core functions:

- **NFC-Based Check-Out:** Allow students to check out devices or materials by tapping their phones on NFC-tagged items.
- **User Authentication via AD:** Authenticate student identities using local Active Directory integration.
- **Manual Check-Out/Check-In:** Enable teachers or staff to manually check items in or out when needed.
- **Inventory Management:** Track status and location of devices, tools, and parts across the classroom inventory.
- **Administrative Portal:** Provide a user-friendly dashboard for educators to monitor and manage inventory activities.
- **Check-Out History:** Maintain logs of all check-outs and returns for accountability and auditing.
- **Notifications (Optional):** Notify users or admins when items are overdue or inventory thresholds are reached.

### 2.3 Product Constraints

The development and deployment of CheckED are subject to the following constraints:

- **Hardware Compatibility:** Mobile app requires NFC-capable smartphones; NFC tags must be compatible with selected devices.
- **Active Directory Integration:** The system must support and conform to the local AD environment for authentication.
- **Network Availability:** AD queries and real-time sync features require local network access; offline mode fallback is recommended.
- **Platform Limitations:** Web portal must be compatible with modern browsers; mobile app should be built for Android (iOS support may be delayed).
- **Educational Setting:** System must be usable in school settings with varied technical skill levels among users.

### 2.4 User Characteristics

The primary user classes for CheckED are as follows:

- **Students**
  - Use the mobile app to check out and return devices.
  - Typically possess basic smartphone literacy.
  - May have limited technical knowledge.

- **Teachers**
  - Use the web portal to manage check-outs, view logs, and track inventory.
  - May also assist with manual check-ins/outs.
  - Require ease-of-use and minimal training.

- **IT Staff**
  - Responsible for setup, integration with AD, and system maintenance.
  - Have advanced technical knowledge.
  - May configure hardware interfaces and user access rights.

### 2.5 Assumptions and Dependencies

The following assumptions and dependencies may impact system design and implementation:

- **NFC Tags:** Tags are assumed to be pre-programmed or easily configurable with asset IDs.
- **Active Directory:** School’s AD server is accessible on the network and contains up-to-date user information.
- **Mobile Devices:** Students will use personal or school-issued NFC-capable smartphones.
- **Internet Access:** While the system may support offline check-outs, core features assume network connectivity.
- **Software Stack:** Project will likely use common educational technologies (e.g., Firebase, Node.js, or .NET Core).

### 2.6 Apportioning of Requirements

Initial apportioning of requirements is as follows:

| Function                      | Component             |
|------------------------------|-----------------------|
| NFC Check-Out/Check-In       | Mobile App            |
| AD Authentication            | Web Backend, Mobile   |
| Manual Entry                 | Web Portal            |
| Inventory Viewing            | Web Portal            |
| Historical Logging           | Backend Database      |
| Notifications (Future Scope) | Web & Mobile (v2)     |

Certain features, such as notifications and iOS support, may be delayed until later iterations or future versions of the system. Initial development will focus on the Android platform and core functionality.

### 3.1 External Interfaces

This section defines the interfaces between CheckED and users, hardware components, and external software systems. These interfaces govern how users interact with the system, how the software communicates with physical devices, and how it integrates with other software components such as Active Directory.

#### 3.1.1 User Interfaces

CheckED will consist of two primary user-facing interfaces:

- **Mobile Application UI**
  - Enables students to check out and return items via NFC.
  - Displays success or error messages upon scanning.
  - Prompts for login or manual check-out in case of NFC failure.
  - Responsive design to accommodate a variety of Android devices.
  - Basic UI elements: buttons for actions (Check-Out, Return), list views for scanned items, and confirmation modals.

- **Web-Based Administrative Portal UI**
  - Dashboard for teachers and IT staff.
  - Displays inventory overview, active check-outs, and student lookup.
  - Interfaces for manually checking items in or out.
  - Search and filtering options for devices and users.
  - UI will conform to basic accessibility standards and use intuitive layout patterns.
  - Screen layouts will prioritize clarity and quick access to core functions.

##### Usability and Convenience Requirements:
- Interfaces should require minimal training.
- Actions must provide immediate feedback (e.g., “Check-Out Successful”).
- Mobile app should cache necessary data for offline use and sync when online.

#### 3.1.2 Hardware Interfaces

The CheckED system interacts with the following hardware:

- **NFC Tags**
  - Standard ISO/IEC 14443 NFC tags programmed with unique device IDs.
  - Must be readable by most modern Android smartphones.

- **Student Mobile Devices**
  - Android smartphones with NFC capability (API level 19+ recommended).
  - Device must support foreground dispatch to read tags in-app.
  - Optionally use vibration or audio feedback to confirm a scan.

- **School Infrastructure**
  - School Wi-Fi or local network to connect mobile devices to the backend.
  - Optionally used by the web portal for accessing the inventory system and AD.

#### 3.1.3 Software Interfaces

The following software interfaces are essential for CheckED’s functionality:

- **Active Directory Integration**
  - Authentication and user lookup via LDAP protocol.
  - Requires AD server access within the local network environment.
  - System will validate student identity and fetch basic profile data.

- **Backend Database**
  - Likely a relational database (e.g., PostgreSQL or SQLite).
  - Stores user check-out history, item metadata, and current inventory status.
  - Supports read/write operations via secure API endpoints.

- **Web API**
  - RESTful API for mobile app to communicate with the backend.
  - Handles requests such as `POST /checkout`, `GET /inventory`, `POST /return`.
  - API will support token-based authentication for secure access.

- **Push Notification Service (Future Scope)**
  - May use Firebase Cloud Messaging (FCM) or similar to notify users/admins about overdue items or system alerts.


### 3.2 Functional

This section outlines the functional requirements of the CheckED system. Each requirement is uniquely identified and written to be clear, testable, and implementation-ready.

#### FR-001: NFC-Based Check-Out
- **Description:** The system shall allow students to check out an item by tapping their NFC-enabled smartphone on the item’s NFC tag.
- **Input:** NFC tag with a unique device ID.
- **Output:** Confirmation message on mobile app, updated status in backend database.
- **Conditions:** Requires student to be authenticated and item to be available.

#### FR-002: NFC-Based Check-In
- **Description:** The system shall allow students to return an item by scanning its NFC tag.
- **Input:** NFC tag scan.
- **Output:** Confirmation of return, update inventory status to "available".

#### FR-003: AD-Based User Authentication
- **Description:** The system shall authenticate users against the local Active Directory (AD) server upon login.
- **Input:** Student username and password.
- **Output:** Access token/session and user details if credentials are valid.

#### FR-004: Manual Check-Out / Check-In
- **Description:** Teachers and staff shall be able to manually check items in or out via the web portal.
- **Input:** Item ID, student selection from directory or manual input.
- **Output:** Inventory update, record added to check-out log.

#### FR-005: Inventory Dashboard
- **Description:** The system shall display all items in inventory, including their availability status and assigned user (if checked out).
- **Output:** Tabular or grid view with filters for category, availability, or user.

#### FR-006: Check-Out History and Logs
- **Description:** The system shall maintain a timestamped log of all check-outs and check-ins.
- **Output:** Exportable history table accessible from the admin portal.

#### FR-007: User Search and Filtering
- **Description:** Admins shall be able to search for users and filter inventory based on check-out status or user.
- **Input:** Search term or filter selection.
- **Output:** Filtered list or user details page.

#### FR-008: Offline Mode for Mobile App
- **Description:** The mobile application shall cache necessary data and allow check-out/check-in while offline, syncing when reconnected.
- **Constraints:** Must queue transactions and resolve conflicts during sync.

#### FR-009: Overdue Notification System (Planned)
- **Description:** The system shall notify users and/or admins when items are overdue.
- **Output:** Mobile push notification or email (future enhancement).
- **Note:** Implementation may be postponed to version 2.0.

#### FR-010: Admin Override
- **Description:** Admin users shall have the ability to override inventory records in the case of discrepancies.
- **Input:** Manual entry with admin authentication.
- **Output:** Modified inventory record with audit trail entry.

#### FR-011: System Audit Trail
- **Description:** The system shall log all administrative actions (e.g., overrides, deletions) with timestamps and user IDs.
- **Purpose:** Ensure accountability and support audits.

#### FR-012: Multi-Role Access Control
- **Description:** The system shall support role-based access controls (e.g., Student, Teacher, Admin).
- **Effect:** Restricts or grants access to features based on role.

### 3.3 Quality of Service

This section defines non-functional requirements related to the quality of the software, including performance benchmarks, security measures, and system reliability.

#### 3.3.1 Performance

- **QR-001:** The mobile app shall process NFC scans and confirm check-out or check-in within 2 seconds under normal network conditions.
- **QR-002:** The system shall be able to support simultaneous active sessions for up to 50 users without degradation of response times beyond 3 seconds.
- **QR-003:** Inventory search and filtering functions in the web portal shall return results within 2 seconds for inventories up to 1,000 items.

#### 3.3.2 Security

- **QR-004:** All communication between clients (web and mobile) and the server shall be encrypted using HTTPS (TLS 1.2 or higher).
- **QR-005:** Authentication credentials shall not be stored in plaintext and must be handled securely (e.g., hashed and salted passwords or secure token exchange).
- **QR-006:** The system shall integrate with the local Active Directory to verify user identity before allowing access to core features.
- **QR-007:** Role-based access controls shall prevent unauthorized access to administrative or inventory modification functions.
- **QR-008:** Admin override and manual changes to inventory shall be logged with user ID, timestamp, and a description of the change.

#### 3.3.3 Reliability

- **QR-009:** The system shall have a target uptime of 99% during school operational hours (8 AM – 4 PM, Monday through Friday).
- **QR-010:** In the event of network disconnection, the mobile application shall continue to function in offline mode and queue operations for later synchronization.
- **QR-011:** The system shall validate data integrity on synchronization to prevent duplicate or conflicting check-out entries.

#### 3.3.4 Availability

- **QR-012:** The system shall be accessible from school premises during operational hours, with backend servers running on a local or school-hosted network.
- **QR-013:** In case of system failure, a manual override process must be documented and available to staff.
- **QR-014:** System backups shall be performed daily to prevent data loss.

### 3.4 Compliance

This section outlines the standards, procedures, and regulations that CheckED must comply with, particularly in an educational and administrative environment.

#### CR-001: Data Privacy Compliance
- The system shall comply with local educational data privacy policies (e.g., FERPA in the U.S. if applicable).
- Personal student data retrieved via Active Directory must not be exposed to unauthorized users.
- Logs shall exclude sensitive data unless necessary for audit and traceability, and access to logs must be role-restricted.

#### CR-002: Audit Logging
- The system shall maintain an audit log of all administrative actions, including:
  - Manual overrides
  - Item deletions or adjustments
  - User access level changes
- Logs shall include timestamp, user ID, action description, and affected item or record ID.

#### CR-003: Data Naming and Consistency
- Inventory records shall follow a consistent naming convention for device IDs, categories, and user associations.
- Tags and records must be uniquely identifiable across the entire system.

#### CR-004: Report Formatting
- The system shall allow export of check-out histories and inventory summaries in a standard format (e.g., CSV or PDF).
- Reports shall include date range filters, user-based filters, and sorting by status or item type.

#### CR-005: Accessibility
- The web-based interface shall comply with WCAG 2.1 Level AA guidelines to ensure accessibility for users with visual or motor impairments.

#### CR-006: Network and Authentication Protocols
- Active Directory integration shall use secure protocols (e.g., LDAPS) when possible.
- Authentication methods must conform to best practices for educational IT systems and avoid hardcoding credentials or bypassing AD policies.

### 3.5 Design and Implementation

This section details considerations and constraints related to the implementation, deployment, and long-term maintenance of the CheckED system.

#### 3.5.1 Installation

- The web portal shall be deployable on a school-hosted server or cloud-based service (e.g., Azure, AWS) with access to the local Active Directory environment.
- The mobile application shall be installable via APK (for Android) or through managed deployment tools used by the school.
- The installation process shall include:
  - Configuration of database connections and AD credentials
  - Setup scripts or containerization (e.g., Docker) for ease of deployment
  - Post-installation verification checklist

#### 3.5.2 Distribution

- The system shall support distributed use across multiple classrooms or labs.
- Each mobile device shall communicate with the same centralized database to ensure consistent tracking of assets.
- The system must support simultaneous access from multiple clients (e.g., students checking out devices, teachers reviewing logs).
- Future versions may support distributed synchronization for schools with multiple campuses.

#### 3.5.3 Maintainability

- The codebase shall be modular, with clear separation between frontend, backend, and database logic.
- Comments and documentation shall be included for all public functions and API endpoints.
- Configuration files shall be externalized to support environment-specific changes without code modification.
- An admin panel shall allow for in-system adjustments to item categories, user roles, and tag associations without requiring code changes.

#### 3.5.4 Reusability

- Components such as the NFC reader handler, authentication module, and inventory logic shall be implemented as reusable services or modules.
- The system architecture shall allow core components to be repurposed in similar inventory or tracking applications (e.g., library book checkouts, lab tool reservations).

#### 3.5.5 Portability

- The mobile app shall target Android OS, API level 21+ (Lollipop and up), and be compatible with major NFC-capable devices.
- The web portal shall be fully responsive and compatible with modern browsers (Chrome, Edge, Firefox).
- Backend services shall be OS-agnostic and containerized for deployment on Linux or Windows environments.

#### 3.5.6 Cost

- The project is student-developed and cost-sensitive; no proprietary libraries or licensed tools should be used unless provided by the school.
- Open-source frameworks and tools shall be prioritized (e.g., Node.js, React, PostgreSQL, Firebase for prototyping).
- NFC tags and test devices will be budgeted and provided by the classroom or school.

#### 3.5.7 Deadline

- The MVP (Minimum Viable Product) must be completed by **[Insert Deadline Here]**, in time for classroom testing.
- Major development phases:
  - Requirements and design: 2 weeks
  - Implementation: 4–6 weeks
  - Testing and deployment: 2 weeks
- Stretch features (e.g., iOS app, notifications) may be deferred to a later release.

#### 3.5.8 Proof of Concept

- A proof-of-concept system shall be demonstrated by mid-project to validate:
  - NFC-based item detection and check-out
  - AD-based login authentication
  - Basic inventory listing and status tracking
- This prototype shall include a testable mobile app and local backend service and serve as the foundation for future development.

## 4. Verification

The purpose of the verification process is to provide objective evidence that the CheckED system meets all specified requirements. Each requirement defined in Section 3 will be verified through appropriate testing, inspection, or demonstration. Verification activities will be conducted by the student development team and supervised by faculty or IT staff.

### 4.1 Verification Methods

| Requirement Type        | Verification Method        | Description |
|-------------------------|----------------------------|-------------|
| Functional (3.2)        | Functional Testing          | Test each user story and requirement using real or simulated inputs (e.g., tap NFC tag, simulate AD login). |
| Interfaces (3.1)        | Interface Testing           | Test mobile/web UIs for usability; verify communication with NFC hardware and AD software. |
| Performance (3.3.1)     | Performance Testing         | Measure response times for scanning, searching, and logging under typical and peak loads. |
| Security (3.3.2)        | Security Testing / Code Review | Verify secure communication (HTTPS), access controls, and credential handling. |
| Reliability (3.3.3)     | Stress Testing / Fault Injection | Simulate connectivity loss, invalid scans, or concurrent check-outs. |
| Availability (3.3.4)    | Monitoring / Recovery Drills | Ensure the system can resume operation after restarts and properly handle backups. |
| Compliance (3.4)        | Documentation Review        | Confirm adherence to data handling, naming conventions, reporting formats, and accessibility guidelines. |
| Design Constraints (3.5)| Review and Demonstration     | Validate modularity, portability, and installability through code walkthroughs and system setup demos. |

### 4.2 Test Plan Summary

- **Unit Tests**: Core functions such as tag reading, check-out logic, and AD integration will be unit tested by student developers.
- **Integration Tests**: Simulate real-world usage combining mobile and web components, using actual school devices and users.
- **User Acceptance Testing (UAT)**: Final system will be reviewed by educators and tested by students under supervision before deployment.

---

## 5. Appendixes

This section includes any supporting material that is referenced or relevant to the SRS but not detailed elsewhere.

### Appendix A: Glossary of Terms

| Term         | Description |
|--------------|-------------|
| NFC          | Near Field Communication technology used for short-range wireless interactions. |
| AD (Active Directory) | Directory service by Microsoft used for authentication and access management. |
| API          | Application Programming Interface – a set of functions and protocols for building software. |
| UI / UX      | User Interface / User Experience – design and interaction aspects of the application. |
| MVP          | Minimum Viable Product – the simplest version of the product with core features working. |

### Appendix B: Future Enhancements

- iOS support for the mobile app.
- Overdue return notifications (push/email).
- Multi-classroom device grouping and filtering.
- Analytics dashboard for usage insights.

### Appendix C: Tools and Technologies

- **Frontend**: React (web), Kotlin or Java (Android)
- **Backend**: Node.js or .NET Core, Express
- **Database**: PostgreSQL or Firebase (for prototyping)
- **Auth**: LDAP/Active Directory
- **Deployment**: Docker, GitHub Actions (CI/CD)

### Appendix D: Document Control

This document is managed by the student development team. Future revisions should be logged in the Revision History table at the beginning of this SRS.
