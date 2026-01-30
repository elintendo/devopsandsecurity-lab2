> **Student ID placeholder:** `<st6>`

# Task 1 - Prerequisites

I bought two vms on timeweb cloud

![[Pasted image 20260130122257.png]]
![[Pasted image 20260130122303.png]]


# Task 2 – SCM Theory (Ansible)

### 1. Ansible Directory Structure – What is it and What is it for

### `ansible.cfg`
- **What**: Main Ansible configuration file.
- **For**: Controls Ansible behavior (inventory path, roles path, SSH options, privilege escalation, logging, etc.).

### `inventory/` folder
- **What**: Contains inventory files (hosts and groups).
- **For**: Defines managed nodes and their grouping (e.g., prod, staging).

### `roles/` folder
- **What**: Collection of reusable Ansible roles.
- **For**: Organizes automation into modular, reusable components.

### `roles/<role>/tasks/`
- **What**: YAML files with task definitions.
- **For**: Defines the main actions executed by the role.

### `roles/<role>/defaults/` and `group_vars/`
- **defaults/**  
  - **What**: Default variables for a role.
  - **For**: Provides safe, overridable values.
- **group_vars/**  
  - **What**: Variables assigned to inventory groups.
  - **For**: Apply configuration to groups of hosts.

### `roles/<role>/handlers/`
- **What**: Special tasks triggered by `notify`.
- **For**: Run actions only when changes occur (e.g., restart a service).

### `roles/<role>/templates/`
- **What**: Jinja2 template files (`.j2`).
- **For**: Generate dynamic configuration files.

### `roles/<role>/files/`
- **What**: Static files.
- **For**: Copy files directly to managed nodes.

### `roles/<role>/vars/`
- **What**: Role variables with higher priority.
- **For**: Define values that should rarely be overridden.

### `roles/<role>/meta/`
- **What**: Role metadata.
- **For**: Declare role dependencies and metadata info.

### `playbooks/` folder
- **What**: YAML playbooks.
- **For**: Orchestrates roles and tasks across hosts.

---

### 2. Most Important `ansible.cfg` Parameters

| Parameter | Explanation |
|--------|------------|
| `inventory` | Default inventory file or directory |
| `roles_path` | Location where Ansible searches for roles |
| `remote_user` | Default SSH user |
| `private_key_file` | SSH private key path |
| `host_key_checking` | Enables/disables SSH host key checking |
| `retry_files_enabled` | Enables retry files on failure |
| `forks` | Number of parallel connections |
| `become` | Enables privilege escalation |
| `become_method` | Method for privilege escalation (sudo, su) |
| `log_path` | Path for Ansible logs |
| `stdout_callback` | Output formatting style |

---

### 3. Difference Between Variable Definitions

### `roles/<role>/defaults/main.yml`
- **Lowest precedence**
- Intended for **configurable defaults**
- Easily overridden
- Best practice for tunable values

### `roles/<role>/vars/main.yml`
- **Higher precedence**
- Intended for **internal role variables**
- Difficult to override
- Used when values must be enforced

### `playbook/group_vars/`
- **Higher than role defaults**
- Applied to inventory groups
- Best for environment-specific configuration (prod, dev)

---

### 4. Ansible Variable Precedence (Low → High)

1. Role defaults (`roles/.../defaults`)
2. Inventory variables
3. Group variables (`group_vars`)
4. Host variables (`host_vars`)
5. Playbook variables
6. Role variables (`roles/.../vars`)
7. Block variables
8. Task variables
9. Registered variables
10. Extra vars (`-e` on CLI) **(highest priority)**

# Task 3
![[Pasted image 20260130121900.png]]![[Pasted image 20260130121908.png]]

I chose Light: 
Ansible Vault (definitely a good choice)
pulling git repository (dive repo)

advanced:
Apache Web Server

The code is on 