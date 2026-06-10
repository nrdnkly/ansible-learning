# Day 03 - My First Ansible Playbook

## 🎯 Objective

Today I learned how to create and run my first Ansible Playbook.

Instead of executing ad-hoc commands, I used a Playbook to automate tasks on my local machine.

## 📚 What I Learned

* What an Ansible Playbook is
* YAML syntax basics
* Playbook structure
* Tasks and modules
* Running Playbooks with `ansible-playbook`
* Understanding idempotency

## 📁 Project Structure

```bash
day03-first-playbook/
├── create-file.yml
└── README.md
```

## Playbook

```yaml
---
- name: My First Playbook
  hosts: localhost
  connection: local
  gather_facts: false

  tasks:
    - name: Create a file
      ansible.builtin.file:
        path: /tmp/ansible-day03.txt
        state: touch

    - name: Write content to file
      ansible.builtin.copy:
        dest: /tmp/ansible-day03.txt
        content: |
          Hello from Ansible!
          Day 03 - First Playbook
```

## Run the Playbook

```bash
ansible-playbook create-file.yml
```

## Verify the Result

```bash
cat /tmp/ansible-day03.txt
```

Expected output:

```text
Hello from Ansible!
Day 03 - First Playbook
```

## Key Takeaways

✅ Learned the structure of an Ansible Playbook

✅ Executed tasks on localhost

✅ Used built-in Ansible modules

✅ Automated file creation and content management

✅ Understood the concept of idempotency

## Progress

| Day | Topic                   | Status |
| --- | ----------------------- | ------ |
| 01  | Introduction to Ansible | ✅      |
| 02  | Inventory & SSH Basics  | ✅      |
| 03  | First Playbook          | ✅      |
| 04  | Variables               | ⏳      |
| 05  | Facts                   | ⏳      |
| 06  | Templates               | ⏳      |

---

🚀 Ansible Learning Journey – Day 03 Complete

