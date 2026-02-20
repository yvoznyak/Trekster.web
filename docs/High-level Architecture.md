# High-level Architecture

## 1. Frontend
- **Technologies:** HTML, CSS, JavaScript
- **Main Components:**
  - **UI Components:** Interface for transaction entry, account, and balance viewing.
  - **Visualization:** Integration of chart libraries (e.g., Chart.js) for reporting.
  - **Report Generation:** Creation of custom reports based on input data and filters (period, category).
  - **Local Storage Interaction:** Saving data in local storage or a local database on the device.

## 2. Backend
- **Technologies:** PHP or Node.js (optional for feature expansion)
- **Main Components:**
  - **Data Processing:** Handling transactions, balances, and categories.
  - **Category and Account Management:** Adding, editing, and deleting accounts and categories.
  - **Database:** Local database (SQLite or other).
  - **Security:** Data encryption and protection via local authentication mechanisms.

## 3. Local Database
- **Technologies:** SQLite or other file-oriented formats.
- **Main Components:**
  - **Transaction Tables:** Information about income, expenses, categories, and transaction dates.
  - **Account Tables:** Information about accounts, balances, and multi-currency support.
  - **Access Interface:** Simple API for CRUD operations.

## 4. External Services (Optional)
- **Banking API Integration:** Potential synchronization with bank accounts for authorized users.
- **Data Export/Import:** Ability to export and import data in CSV or Excel formats.
- **Cloud Storage:** Optional cloud synchronization for multi-device access.

## 5. Security
- **Local Data Encryption:** All data is stored locally with optional database encryption.
- **Authentication:** Two-factor authentication for authorized users.
- **Data Backup:** Automatic creation of local backups to prevent data loss.

# High level architecture diagram

<p align="center">
	<img src="https://github.com/yvoznyak/ooap_trekster/blob/main/High%20level%20architecture%20diagram/trekster_architecture.png" alt="High-level Architecture" height="650"/>
</p>
