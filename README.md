# Trekster.web 🌐

**Trekster.web** is a robust web-based application within the Trekster finance ecosystem. Built on **ASP.NET Core**, it offers a secure and scalable platform for managing personal finances, supported by comprehensive SDLC documentation and a multi-layered testing strategy.

---

## ✨ Key Features
* **Financial Management:** Full-cycle tracking of income, expenses, and budget categories.
* **Professional QA Suite:** Advanced automated testing covering Unit, Integration, and UI (Selenium) levels.
* **Advanced Logging:** Hybrid logging architecture using **Serilog** and **log4net** for enterprise-grade traceability.
* **Data Persistence:** Optimized database operations using **Entity Framework Core** and **PostgreSQL**.
* **SDLC Documentation:** Thorough project planning, including Mitigation Plans, SRS, and UI/UX Prototyping.

## 🛠 Tech Stack
* **Backend:** ASP.NET Core (C#), Entity Framework Core
* **Database:** PostgreSQL
* **Testing:** xUnit (Unit & Integration), Selenium (UI Automation)
* **Logging:** Serilog & log4net
* **Analysis:** StyleCop.Analyzers



## 📂 Project Structure
* **`/src`** — Contains all source code and testing suites.
  * **`/Trekster_web`** — Core web application logic and UI.
  * **`/Testing`** — Automated tests (xUnit, Selenium), manual test cases, and defect tracking lists.
* **`/docs`** — Extensive project documentation.
  * `Project charter.pdf` & `Requirements Engineering.md` — Project definition and SRS.
  * `Diagrams & monitoring models.md` — Data, Resiliency, and Monitoring models.
  * `UIUX Design and Prototyping.pdf` — Interface design assets.
  * `Mitigation plan.md` — Security and risk management.
  * `Trekster.web.pdf` — Project presentation.

## ⚙️ Setup & Installation
1. **Clone** the repository.
2. **Database:** Ensure PostgreSQL is running and update the connection string in `appsettings.json`.
3. **Migrations:** Apply database migrations via Entity Framework Core.
4. **Testing:** Explore the `/src/Testing` folder for automated test execution instructions.
5. **Run:** Open the solution in **Visual Studio 2022** and press `F5`.

---
