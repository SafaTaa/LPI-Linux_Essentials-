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
### Step 4: Assigning Directory Ownership and Group

Assign each department directory to the admin user and set the group ownership:

```bash
sudo chown eng_admin:Engineering /Engineering
sudo chown sales_admin:Sales /Sales
sudo chown is_admin:IS /IS
```
### Step 5: Setting Directory Permissions

Configure directory permissions so that:

- Admin has full access
- Department users have full access
- Other users have no access
  
```bash
sudo chmod 770 /Engineering
sudo chmod 770 /Sales
sudo chmod 770 /IS
```
### Step 6: Creating Confidential Files

```bash
# Engineering
sudo touch /Engineering/confidential.txt
sudo chown eng_admin:Engineering /Engineering/confidential.txt
sudo chmod 640 /Engineering/confidential.txt
echo "This file contains confidential information for the department." | sudo tee /Engineering/confidential.txt

# Sales
sudo touch /Sales/confidential.txt
sudo chown sales_admin:Sales /Sales/confidential.txt
sudo chmod 640 /Sales/confidential.txt
echo "This file contains confidential information for the department." | sudo tee /Sales/confidential.txt

# IS
sudo touch /IS/confidential.txt
sudo chown is_admin:IS /IS/confidential.txt
sudo chmod 640 /IS/confidential.txt
echo "This file contains confidential information for the department." | sudo tee /IS/confidential.txt
```
### Step 7: Verification
Check that directories and files have the correct ownership and permissions:

```bash
ls -ld /Engineering /Sales /IS
ls -l /Engineering/confidential.txt
ls -l /Sales/confidential.txt
ls -l /IS/confidential.txt
```

After completing the lab, all department directories and confidential files are properly secured:

- Department administrators have full ownership and control.

- Department groups can read, write, and execute within their directories.

- Other users have no access to these directories or files.

By following these steps, the Linux server is configured so that each department has secure, controlled access to its resources, ensuring proper administrative control and confidentiality of department data

