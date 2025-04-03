# AWS Infrastructure Setup and Monitoring

## Overview
This document outlines the steps taken to set up and monitor AWS services, including EC2, RDS, SNS, and CloudWatch.

---

## 1️⃣ EC2 Instance Setup
- Launched an EC2 instance (Amazon Linux 2023)
- Installed MariaDB client for database connectivity:
  ```sh
  sudo yum install -y mariadb
  ```
---

![EC2](Assignment_no1%20Images/EC2.png)

## 2️⃣ RDS Instance Setup
- Created an **Amazon RDS** instance (MySQL/MariaDB)
- Configured **Security Groups** to allow inbound connections from EC2
- Admin database connection:
  ```sh
  mariadb -h <RDS_ENDPOINT> -u <DB_ADMIN> -p
  ```
- Creation of User in Admin:
  ```sql
  CREATE USER '--username--'@'%' IDENTIFIED BY '--password--';
  GRANT ALL PRIVILEGES ON *.* TO '--username--'@'&' WITH GRANT OPTION;
  FLUSH PRIVILEGES;
  SELECT user, host FROM mysql.user;
  ```
- Create database table in Admin add all privileges to user database:
  ```sql
  CREATE DATABASE mydatabase;
  GRANT ALL PRIVILEGES ON mydatabase.* TO 'database-1'@'%';
  FLUSH PRIVILEGES;
  ```
- Connect to user database:
  ```sh
  mariadb -h <RDS_ENDPOINT> -u <DB_USER> -p
  ```
- Display all available databases:
  ```sql
  SHOW DATABASES;
  ```
- Select the database you want to use:
  ```sql
  USE mydatabase;
  ```
- Populated a database:
  ```sql
  CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50),
    EMAIL VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );
  ```
---

![RDS_SETUP](Assignment_no1%20Images/STEP01.png)
![RDS_SETUP](Assignment_no1%20Images/STEP02.png)
![RDS_SETUP](Assignment_no1%20Images/STEP03.png)
![RDS_SETUP](Assignment_no1%20Images/STEP04.png)
![RDS_SETUP](Assignment_no1%20Images/RDS.png)

## 3️⃣ SNS (Simple Notification Service) Setup
- Created an SNS **Topic** for notifications
- Subscribed an **email endpoint** to receive alerts
- Configured SNS to notify on **RDS Alarm Triggers**
- 
---

![SNS](Assignment_no1%20Images/SNS_Topic.png)

## 4️⃣ CloudWatch Monitoring & Alarm Setup
### ✅ **CloudWatch Monitoring for RDS**
- Enabled **CloudWatch metrics** for RDS
- Monitored **Free Storage Space**, CPU Utilization, and Active Connections

### 🔔 **Alarm Setup for Database Size**
- Created an **alarm** when database size **exceeds** **60 KB**
- Set **threshold value**:
  ```plaintext
  61440 (60KB in bytes)
- Defined an **SNS notification** for alerts

**Alarm Description:**
> This alarm monitors the database size on the RDS instance. If the database size exceeds 60KB, notifications will be sent via SNS to alert the responsible team. Immediate action is required to optimize storage or increase the allocated space.

---

![Cloudwatch](Assignment_no1%20Images/Cloudwatch.png)
![Trigger](Assignment_no1%20Images/Alarm_triggers.png)
![Notification](Assignment_no1%20Images/Notification.png)

## 5️⃣ Stopping and Deleting AWS Resources
### 🔹 **Stopping EC2 & RDS**
- EC2 can be **stopped** to avoid charges
- **Stopped RDS still incurs storage costs**

### 🔥 **Deleting RDS to avoid charges**
- RDS was **deleted** after selecting the "Delete Storage" option
- Storage volume was also deleted

---

## Summary ✅
This setup ensured a working **EC2-RDS-SNS-CloudWatch** integration for database monitoring and notifications. The alarm setup helps in proactive monitoring of RDS storage space.
