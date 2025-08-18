# Ansible Drift All-in-One 🚀

This project is an **all-in-one Ansible automation kit** that helps you quickly set up and configure different types of applications (Java, Node.js, PHP, React) with **Nginx reverse proxy** and service management.  
It’s designed to be simple, modular, and extendable — a perfect starting point for learning Ansible or automating multi-stack environments.

---

## 📂 Project Structure
```

.
├── project-setup.yml               # Main playbook
├── local-host                      # Inventory file (runs on localhost by default)
└── roles/
└── project-setup/
├── tasks/                  # Main automation tasks
├── handlers/               # Handlers for service restarts/reloads
├── vars/                   # Default variables
├── templates/              # Nginx & service templates for each stack
│   ├── java-nginx.conf.j2
│   ├── java-sample.service.j2
│   ├── nodejs-nginx.conf.j2
│   ├── php-nginx.conf.j2
│   └── react-nginx.conf.j2
└── defaults/               # Default role variables

````

---

## ✨ What This Project Does
- 📦 Automates **environment setup** using Ansible roles.  
- 🌐 Configures **Nginx** as a reverse proxy for multiple app types (Java, Node.js, PHP, React).  
- ⚙️ Creates and manages **systemd service files** (example: `java-sample.service`).  
- 🐳 Includes a `.docker.env` template to integrate container-based setups.  
- 🛠️ Fully modular: you can extend tasks, handlers, and templates for your own applications.  

---

## 🛠️ Prerequisites
Before you begin, make sure you have:
- **Ansible** installed (v2.9+ recommended)  
- **Python 3.x** installed  
- A target machine (or just your localhost) with **sudo access**  

Install Ansible:
```bash
sudo apt update && sudo apt install ansible -y
````

---

## 🚀 How to Use

### 1. Clone the Repository

```bash
git clone https://github.com/<your-username>/ansible-drift-all-in-one.git
cd ansible-drift-all-in-one
```

### 2. Check Inventory

By default, the inventory (`local-host`) is set to run on your localhost.
You can update it with remote server IPs if you want to deploy elsewhere.

Example (`local-host`):

```
[all]
127.0.0.1 ansible_connection=local
```

### 3. Run the Playbook

```bash
ansible-playbook -i local-host project-setup.yml
```

This will execute the `project-setup` role and configure the environment.

---

## 🔧 Customization

### Configure Application Type

Inside `roles/project-setup/templates/`, you’ll find pre-built templates for:

* `java-nginx.conf.j2`
* `nodejs-nginx.conf.j2`
* `php-nginx.conf.j2`
* `react-nginx.conf.j2`

You can edit these templates to match your own app’s ports, domains, or service details.

### Add New Roles

Want to support another stack?
Just create a new template + service file, and include it in the tasks.

---

## 📚 Example: Setting up a Java App

1. Place your `.jar` file in the target server.
2. Edit `java-sample.service.j2` to point to your `.jar`.
3. Run the playbook:

   ```bash
   ansible-playbook -i local-host project-setup.yml
   ```
4. Your Java app will be running behind Nginx.

---

