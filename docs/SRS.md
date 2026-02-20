# Trekster

Trekster is a simple and user-friendly application for personal finance tracking, designed to optimize and streamline personal fund management. Trekster allows users to manually enter expense and income data, as well as view information grouped by categories and currencies.

# Functional Requirements

The application defines two types of users: **Authorized User** and **Non-authorized User**.

A non-authorized user can:
- Register
- Log in
- Reset password

An authorized user can:
- View a dashboard with key metrics (account balances, expense-to-income ratio, remaining funds)
- Set the reporting period (daily, weekly, monthly, yearly)
- Filter transactions by date, category, account, or amount
- Create transactions (expenses or income)
- View expense and income analytics via charts (e.g., pie charts or bar charts)
- Export transaction data to files (CSV, Excel)
- View accounts and the balance of each
- Add new accounts
- View transaction history
- Edit transaction history
- View monthly reports on income and expenses
- Configure accounts and categories (deleting and editing)
- Manage categories

# Non-functional Requirements
- Interface language: Ukrainian (with the possibility of adding other languages in the future)
- Interface design: Static, without responsive support
- The program does not require Internet access
- The program must provide an instant response to user actions (less than 2 seconds for request execution)
- Stability: Support for stable operation even with a large amount of data (thousands of transactions)
- Minimal resource consumption (CPU, RAM) to ensure compatibility with mid-range hardware
- Scalability: Ability to handle a large number of accounts and transactions without performance degradation
- User Interface: Simple and intuitive interface for users without prior experience with similar software
- Data Preservation: Regular automatic saving of changes to the database to prevent data loss
- Compatibility: Support for major file formats for export (CSV, Excel)

# Roles

| Role | Description |
|------------------|--------------------------------------------------------------------------------------|
| Authorized User | Can edit account data and delete the account. View expense-to-income and balance-to-income ratios. Add, edit, and delete transactions. View accounts and their balances. Add, edit, and delete accounts. View transaction history. View monthly income and expense reports sorted by category. Add, edit, and delete categories. |
| Non-authorized User | Can register, log in, and reset password |

## Use Case Diagram

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/use.jpg" alt="Use case"/>
</p>

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

# Concurrency Patterns usage

<p align="center">
	<img src="https://github.com/yvoznyak/ooap_trekster/blob/main/Concurency%20Patterns%20usage/add_transaction.png" alt="Concurency Patterns usage" height="450"/>
</p>

<p align="center">
	<img src="https://github.com/yvoznyak/ooap_trekster/blob/main/Concurency%20Patterns%20usage/edit_account.png" alt="Concurency Patterns usage" height="450"/>
</p>

<p align="center">
	<img src="https://github.com/yvoznyak/ooap_trekster/blob/main/Concurency%20Patterns%20usage/manage_categories.png" alt="Concurency Patterns usage" height="450"/>
</p>

<p align="center">
	<img src="https://github.com/yvoznyak/ooap_trekster/blob/main/Concurency%20Patterns%20usage/user_authorization.png" alt="Concurency Patterns usage" height="450"/>
</p>

<p align="center">
	<img src="https://github.com/yvoznyak/ooap_trekster/blob/main/Concurency%20Patterns%20usage/view_reports.png" alt="Concurency Patterns usage" height="450"/>
</p>

# Account Management System

| Use case | Description |
|-------------------|--------------------------------------------------------|
| Registration | Sign up for the system (Create a new user) |
| Log in | Access the system |
| Log out | Exit the system |
| Password Reset | Change user password |

# Finance Management System

| Use case | Description |
|-------------------|--------------------------------------------------------|
| View expense/balance to total income ratio | User sees a chart showing the percentage share of total expenses and balance relative to total income |
| Add transaction | Add a transaction to the system by selecting a category, amount, currency, and account |
| View accounts | User sees a list of all accounts and their current balances |
| Add account | User can add an account by entering the initial amount and currency |
| Delete account | User can delete an account and all associated transactions |
| View transaction history | User sees a list of all transactions and their details |
| Edit transaction history | User can edit category, amount, currency, account, and date |
| View income and expense reports | User sees reports grouped by categories |
| View categories | User sees a list of all their categories |
| Add category | User can add a category by selecting its type |
| Edit category | User can edit a category in the system |
| Delete category | User can delete a category and all associated transactions |


### Wireframes Description

#### 1. Main Page

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/main.jpg" alt="Main"/>
</p>

The initial window that opens upon application launch.
The total balance across all accounts is shown at the top, summarized separately by different currencies (e.g., UAH, USD, EUR, USDT).
The center of the window displays the share of expenses relative to total income and the share of the remaining balance relative to total income as percentages.
The top of the page contains a navigation menu with items: Home, Accounts, History, Income, Expenses, Settings.
An "Add Transaction" button is located at the bottom center, allowing the user to add a transaction.
The user selects the account, category (from dropdown lists), and enters the amount (input) in a new window:

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/add%20trans.jpg" alt="Add transaction"/>
</p>

#### 2. Accounts

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/accounts.jpg" alt="Accounts"/>
</p>

The window opened via the "Accounts" menu item.
This page displays all accounts sequentially with balances grouped by currency in the format: <<Account Name: Amount + Currency>>.
The top navigation menu remains accessible.
An "Add Account" button is located at the top.
In a new window, the user enters the account name (input), selects currencies (input), and enters amounts (input). A "Save" button at the bottom saves the new account:

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/add%20account.jpg" alt="Add account"/>
</p>

#### 3. History

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/history.jpg" alt="History"/>
</p>

The window opened via the "History" menu item.
Displays all transactions in chronological order in the format: <<Date, Account Name, Category, Amount, Currency>>.
Each transaction block is color-coded: blue for income, red for expenses.
Each block contains "Edit" and "Delete" buttons on the right side, which open a window for modifying or removing the transaction:

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/edit%20trans%201.jpg" alt="Edit transaction"/>
</p>

Users can change the account (dropdown list), category (dropdown list), and amount (input), then save or delete the transaction using the buttons at the bottom.

#### 4. Income

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/profit.jpg" alt="Income"/>
</p>

The window opened via the "Income" menu item.
Displays total income by category with summarized balances by currency for the current month in the format: <<Category: Amount + Currency>>.
A block at the bottom shows the summary for all currencies.

#### 5. Expenses

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/expense.jpg" alt="Expenses"/>
</p>

The window opened via the "Expenses" menu item.
Displays total expenses by category with summarized balances by currency for the current month in the format: <<Category: Amount + Currency>>.
A block at the bottom shows the summary for all currencies.

#### 6. Settings

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/settings%20main.jpg" alt="Settings"/>
</p>

The window opened via the "Settings" menu item.
Contains two main blocks: Accounts and Categories, which redirect the user to their respective configuration pages.

#### 7. Account Settings

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/settings%20acc.jpg" alt="Account Settings"/>
</p>

The window opened via the "Accounts" section in Settings.
Displays account blocks sequentially. Each block has "Edit" and "Delete" buttons that open a configuration window:

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/edit%20acc.jpg" alt="Edit Account"/>
</p>

Users can modify the account name (input) and balance. "Save" and "Delete" buttons execute the respective actions.

#### 8. Category Settings

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/settings%20cat.jpg" alt="Category Settings"/>
</p>

The window opened via the "Categories" section in Settings.
Displays category blocks sequentially. Each block has "Edit" and "Delete" buttons that open a configuration window:

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/settings%20cat%201.jpg" alt="Edit Category"/>
</p>

Users can modify the category name (input). "Save" and "Delete" buttons are at the bottom.
An "Add Category" button is available at the top of the main window to create a new category:

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/add%20cat.jpg" alt="Add Category"/>
</p>

#### 9. Authorization

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/login.jpg" alt="Authorization"/>
</p>

User logs in by entering an email address and password. If they don't have an account, they click "Register".

#### 10. Registration

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/register.jpg" alt="Registration"/>
</p>

User registers by entering an email address and password, then must confirm the email via a link sent to them.

## ER Diagram

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster_web/blob/main/docs/images/er.jpg" alt="ER Diagram"/>
</p>
