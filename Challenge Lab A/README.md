# Challenge A  : User Management 
This lab simulates a real-world scenario where a Linux administrator is tasked with setting up a server for a fast-growing company. The company has hired 9 new employees across 3 newly created departments: Engineering, Sales, and IS.

The main goal of the lab is to create and manage users, groups, directories, and permissions to ensure that each department has secure access to its resources while maintaining proper administrative control.

## **Requirements**

1. Have a Linux machine or VM with administrative (root/sudo) privileges.
2. Connect to the machine using a terminal or SSH session to perform tasks.

## **Implementation Steps**

### Step 1: Creating Directories and Groups

Create directories for each department and corresponding groups:

```bash
sudo mkdir /Engineering
sudo mkdir /Sales
sudo mkdir /IS

sudo groupadd Engineering
sudo groupadd Sales
sudo groupadd IS
```
### Step 2: Creating Administrative Users

Create one admin user for each department with Bash shell and assign the primary group:
```bash
sudo useradd -m -s /bin/bash -g Engineering eng_admin
sudo useradd -m -s /bin/bash -g Sales sales_admin
sudo useradd -m -s /bin/bash -g IS is_admin

sudo passwd eng_admin
sudo passwd sales_admin
sudo passwd is_admin
```

### Step 3: Creating Regular Users

Create two additional users for each department:

```bash
# Engineering users
sudo useradd -m -s /bin/bash -g Engineering eng_user1
sudo useradd -m -s /bin/bash -g Engineering eng_user2

# Sales users
sudo useradd -m -s /bin/bash -g Sales sales_user1
sudo useradd -m -s /bin/bash -g Sales sales_user2

# IS users
sudo useradd -m -s /bin/bash -g IS is_user1
sudo useradd -m -s /bin/bash -g IS is_user2
```
