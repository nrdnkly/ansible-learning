# Day 02 - Inventory & SSH Basics

## Overview

Today I learned how Ansible manages hosts using inventory files and how to execute commands on managed systems. Since I currently have only one machine available, I used my local computer as the managed host.

---

## What is an Inventory?

Ansible uses an inventory file to define the hosts it manages.

Example inventory:

```ini
[local]
localhost ansible_connection=local
```

In this configuration:

* `localhost` is the target host.
* `ansible_connection=local` tells Ansible to run commands directly on the local machine instead of connecting via SSH.

---

## Testing Connectivity

I verified that Ansible could communicate with the host using the ping module.

```bash
ansible all -i inventory/hosts.ini -m ping
```

Expected output:

```json
localhost | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

This confirms that Ansible is correctly configured and can manage the target host.

---

## Running Ad-Hoc Commands

Ansible allows quick command execution without creating a playbook.

### Display Hostname

```bash
ansible all -i inventory/hosts.ini -m command -a "hostname"
```

### Check Disk Usage

```bash
ansible all -i inventory/hosts.ini -m command -a "df -h"
```

### Check System Uptime

```bash
ansible all -i inventory/hosts.ini -m command -a "uptime"
```

### Display Current User

```bash
ansible all -i inventory/hosts.ini -m command -a "whoami"
```

---

## Understanding Ad-Hoc Commands

General syntax:

```bash
ansible <host-pattern> -m <module> -a "<arguments>"
```

Example:

```bash
ansible all -m command -a "uptime"
```

Where:

* `all` = target hosts
* `command` = Ansible module
* `uptime` = command executed on the host

---

## Modules Used Today

### ping

Tests connectivity between Ansible and the managed host.

```bash
ansible all -m ping
```

### command

Executes commands on the target host.

```bash
ansible all -m command -a "hostname"
```

---

## Key Takeaways

Today I learned:

* What an Ansible inventory file is.
* How hosts are defined inside an inventory.
* The difference between local and SSH connections.
* How to run ad-hoc commands.
* How to test connectivity using the ping module.
* Basic Ansible command syntax.

---

## Next Step

In Day 03, I will learn Playbooks and start automating tasks using YAML files instead of executing commands manually.