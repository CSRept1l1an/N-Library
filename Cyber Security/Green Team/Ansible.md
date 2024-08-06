## 1. Introduction
**Definition:**
Ansible is an open-source automation tool used for configuration management, application deployment, task automation, and orchestration. It allows you to define and manage infrastructure as code, ensuring consistent and repeatable configurations across multiple systems.

**Key Features:**
- **Agentless:** Ansible does not require any agent software to be installed on managed nodes. It uses SSH for communication, which simplifies management and reduces overhead.
- **Simple Syntax:** Ansible uses a simple, human-readable YAML syntax for playbooks, making it easy to write and understand.
- **Idempotency:** Ansible ensures that changes are only applied when necessary, preventing unintended alterations and ensuring systems are in the desired state.
- **Extensible:** Ansible supports a wide range of modules and plugins, allowing for extensive customization and integration with other tools and services.
- **Powerful Orchestration:** Ansible can manage complex deployments and coordinate multiple systems simultaneously, making it ideal for orchestration tasks.

**Use Cases:**
- **Configuration Management:** Automate the setup and maintenance of system configurations across servers, ensuring consistency and reducing manual effort.
- **Application Deployment:** Simplify the deployment of applications by automating tasks such as package installation, service configuration, and code deployment.
- **Continuous Delivery:** Integrate Ansible with CI/CD pipelines to automate the deployment of updates and changes, ensuring rapid and reliable delivery.
- **Infrastructure as Code (IaC):** Define and manage infrastructure resources using Ansible playbooks, enabling version control, reproducibility, and collaboration.
- **Cloud Provisioning:** Automate the provisioning and management of cloud resources on platforms like AWS, Azure, and Google Cloud.
- **Security and Compliance:** Ensure systems comply with security policies and standards by automating audits, patches, and compliance checks.

## 2. Basic Concepts

### Inventory
- **Definition:**
  An inventory in Ansible is a file that contains information about the hosts that Ansible manages. It can be as simple as a list of IP addresses or hostnames, or it can be a more complex configuration that includes groups and variables.

- **Syntax Example:**
  - **INI Format:**
```ini
[webservers]
web1.example.com
web2.example.com

[databases]
db1.example.com
db2.example.com
```

  - **YAML Format:**
```yaml
all:
  hosts:
	web1.example.com:
	web2.example.com:
  children:
	databases:
	  hosts:
		db1.example.com:
		db2.example.com:
```

### Playbooks
- **Definition:**
  Playbooks are Ansible's configuration, deployment, and orchestration language. They are expressed in YAML and allow you to describe policies that your remote systems should enforce or a set of steps in a general IT process.

- **YAML Structure:**
```yaml
- name: Ensure web servers are configured
  hosts: webservers
  tasks:
	- name: Install Nginx
	  apt:
		name: nginx
	    state: present

	- name: Start Nginx service
	  service:
	    name: nginx
	    state: started
```

### Modules
- **Definition:**
  Modules are the building blocks of Ansible. Each module is essentially a tool that Ansible runs to perform specific tasks such as installing packages, managing services, or manipulating files.

- **Common Modules:**
  - `ping`: Test connectivity to hosts.
  - `command`: Execute commands on remote nodes.
  - `copy`: Copy files to remote locations.
  - `file`: Manage file properties.
  - `service`: Manage services.

### Roles
- **Definition:**
  Roles are a way of organizing playbooks and other files in a standardized file structure. They enable you to reuse and share code more easily by grouping tasks, files, templates, and variables.

- **Structure:**
```text
my_role/
├── tasks/
│   └── main.yml
├── files/
├── templates/
├── vars/
│   └── main.yml
├── defaults/
│   └── main.yml
├── handlers/
│   └── main.yml
└── meta/
  └── main.yml
```

## 3. Installation and Configuration
### Installing Ansible

- **On [[Ubuntu]]:**
```bash
sudo apt update
sudo apt install ansible
```

- **On [[CentOS]]:**
```bash
sudo yum install epel-release
sudo yum install ansible
```

- **On macOS (using Homebrew):**
```bash
brew install ansible
```

- **Via Pip ([[Python|Python]] Package Installer):**
```bash
pip install ansible
```

#### Configuration

- **Configuration File (`ansible.cfg`):**
  The `ansible.cfg` file allows you to configure settings such as inventory location, logging, and SSH options. This file can be placed in several locations, including the current directory, the user's home directory, or globally.

- **Basic `ansible.cfg` Example:**
```ini
[defaults]
inventory = ./inventory
remote_user = your_username
private_key_file = ~/.ssh/id_rsa
host_key_checking = False
retry_files_enabled = False

[privilege_escalation]
become = True
become_method = sudo
become_user = root
```

- **Common Configuration Options:**
- **`inventory`:** Path to the inventory file.
- **`remote_user`:** Default SSH user.
- **`private_key_file`:** Path to the SSH private key.
- **`host_key_checking`:** Disable SSH host key checking (useful for dynamic hosts).
- **`retry_files_enabled`:** Disable creation of retry files.
- **`become`:** Enable privilege escalation.
- **`become_method`:** Method for privilege escalation (e.g., `sudo`).
- **`become_user`:** User to become when using privilege escalation.