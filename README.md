# 📡 Cable/Network Service Management System

A simple Cable/Network Service Management System built with **Python + Frappe Framework**.  
This project allows users to register customers, select entertainment packages, record payments, and automatically activate services.

---

## 🚀 Features

- 📦 Package management (News, Sports, Kids, All-in-One, etc.)
- 👤 Customer registration with package selection
- 💳 Payment recording with amount, mode, and status
- 🔁 Auto-activation of customer service upon successful payment
- 🌐 Web forms for customer management and payment entry
- 🛠️ Fully script-driven (Doctypes and Web Forms created via code)
- 🔐 Login-protected customer & payment forms

---

## 🧰 Tech Stack

- [Frappe Framework](https://frappeframework.com/)
- Python
- MariaDB
- Redis
- Node.js & npm (for frontend assets)
- Ubuntu (WSL2 compatible)

---

## 📦 Getting Started

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/aqeeladil/frappe-cable-network-task.git
cd frappe-cable-network-task
```

### 2️⃣ Install Bench & Setup Environment

```bash
# Prerequisites
sudo apt update && sudo apt install -y python3-dev python3-pip redis-server mariadb-server libmariadb-dev build-essential wkhtmltopdf nodejs npm curl

# Install pipx and bench
python3 -m pip install --user pipx
python3 -m pipx ensurepath
pipx install frappe-bench
```

### 3️⃣ Create Bench and Site

```bash
bench init cable-bench --frappe-branch version-15
cd cable-bench
bench new-site cable.local  # set MySQL root password & admin password
```

### 4️⃣ Get the App

```bash
bench get-app cable_management ../cable-management-frappe
bench --site cable.local install-app cable_management
```

### 5️⃣ Generate Doctypes & Web Forms

```bash
python3 apps/cable_management/scripts/generate_doctypes.py
bench --site cable.local migrate
```

### 6️⃣ Start the Development Server

```bash
bench start
```

Visit: [http://localhost:8000](http://localhost:8000)

---

## 📦 Sample Web Form JSON Created

- `package_form.json`
- `customer_form.json`
- `payment_form.json`
- `status_view.json`

All are located under:
`apps/cable_management/cable_management/cable_management/web_form/`

## 🧠 Assumptions

- Frappe built-in authentication is used
- No role management, all users with login can access forms
- No client-side scripting — UI is purely server-driven
- Doctypes and Forms are code-defined for version control

---

## 🌐 Web Form URLs

| Form | URL | Login Required |
|------|-----|----------------|
| Customer Form | `/customer-form` | ✅ Yes |
| Payment Entry | `/payment-form` | ✅ Yes |
| Package Listing | `/package-form` | ❌ No |
| Customer Status View | `/status-view` | ✅ Yes |

---

