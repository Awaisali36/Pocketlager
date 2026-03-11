# PocketLedger

A personal finance web app for tracking income, expenses, budgets, and spending habits. Built with Flask and MongoDB.

---

## About the System

PocketLedger lets you manage your money in one place. Add income and expenses with tags and payment methods, set monthly budgets by category, and view charts and reports to understand where your money goes. It supports user accounts, light/dark themes, multiple currencies, and optional email notifications.

### Features

- **Dashboard** — Overview of income, expenses, balance, and recent transactions
- **Transactions** — Add, edit, and delete income and expense records with tags and payment methods
- **Budgets** — Set monthly budgets by category and track progress
- **Reports** — Charts for monthly trends, category breakdowns, payment methods, and cash flow
- **Settings** — Themes, currencies, date formats, and email preferences
- **Admin** — User management and system logs (protected area)

---

## Tech Stack

- **Backend:** Python, Flask
- **Database:** MongoDB
- **Frontend:** HTML, CSS, JavaScript, Bootstrap 5, Chart.js
- **Deployment:** Docker, Gunicorn (Linux/macOS), Waitress (Windows)

---

## How to Run

**Prerequisites:** [Docker](https://www.docker.com/products/docker-desktop/) and [Docker Compose](https://docs.docker.com/compose/install/)

1. Copy the environment file:
   ```sh
   cp .env.example .env
   ```

2. Edit `.env` and set at least:
   - `SECRET_KEY` — Strong random string for sessions
   - `ADMIN_SETUP_CODE` — Code used to create the first admin
   - `ADMIN_PASSWORD` — Password for sensitive admin actions  
   - `RESEND_API_KEY` — Optional, for email notifications

3. Start the app:
   ```sh
   docker-compose up -d --build
   ```

4. Open [http://localhost:5000](http://localhost:5000)

5. Visit `/initialize-admin` and enter your `ADMIN_SETUP_CODE` to create the first admin account.

---

## Manual Setup (Without Docker)

1. Create a virtual environment and install dependencies:
   ```sh
   python3 -m venv venv
   source venv/bin/activate   # Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```

2. Run MongoDB locally or configure `MONGO_URI` in `.env`.

3. Run the app:
   ```sh
   gunicorn --bind 0.0.0.0:5000 "app:app"   # Linux/macOS
   python run_server.py                      # Windows
   ```
