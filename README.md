# Trekster.web 🌐

**Trekster.web** is a web-based extension of the Trekster finance ecosystem. Built on ASP.NET Core, it provides a secure and scalable platform for managing personal finances via a web interface.

---

## ✨ Key Features
* **Comprehensive Finance Management:** Web interface for tracking income, expenses, and budget categories.
* **Advanced Logging:** Multi-layered logging system using **Serilog** and **log4net** for maximum traceability.
* **Data Persistence:** Leveraging **Entity Framework Core** for efficient database operations.
* **Quality Assurance:** Extensive automated testing suite to ensure system reliability using **xUnit**.

## 🛠 Tech Stack
* **Framework:** ASP.NET Core (C#)
* **OR/M:** Entity Framework Core
* **Database:** PostgreSQL
* **Testing:** xUnit (Advanced automated testing)
* **Logging:** Serilog & log4net

## 📂 Project Structure
* **`/Trekster_web`** — Main source code of the web application.
* **`/docs`** — Project documentation, including `SRS.md`, application presentation (`Trekster.web.pdf`), and UML entity relationship diagrams.

## ⚙️ Setup & Installation
1. Clone the repository.
2. Update the connection string in `appsettings.json` to point to your **PostgreSQL** instance.
3. Apply database migrations using Entity Framework Core.
4. Open the solution in **Visual Studio 2022** or use the .NET CLI to run the project.
