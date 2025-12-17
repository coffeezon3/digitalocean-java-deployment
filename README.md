Demo Project: Create Server and Deploy Java Application on DigitalOcean

Module: 5 – Cloud & Infrastructure as a Service (IaaS) Basics
Bootcamp: TWN DEV Bootcamp

📌 Project Overview

This project demonstrates how to set up a cloud server on DigitalOcean and deploy a Java application built with Gradle. The focus is on basic cloud infrastructure concepts, Linux server administration, security best practices, and application deployment.

🛠️ Technologies Used

Cloud Provider: DigitalOcean

Operating System: Linux (Ubuntu)

Programming Language: Java

Build Tool: Gradle

Infrastructure Type: Infrastructure as a Service (IaaS)

🎯 Project Goals

Create and configure a server (Droplet) on DigitalOcean

Set up a secure Linux environment

Apply security best practices (non-root user, SSH)

Deploy and run a Java Gradle application on the server

🚀 Project Steps
1. Create a DigitalOcean Droplet

Created a new Droplet via the DigitalOcean dashboard

Selected Ubuntu Linux as the operating system

Configured SSH key authentication

Chose an appropriate Droplet size for the demo application

2. Initial Server Setup

Connected to the Droplet via SSH

Updated system packages:

sudo apt update && sudo apt upgrade -y
3. Create and Configure a Linux User (Security Best Practice)

Created a new non-root user

Added the user to the sudo group

Configured SSH access for the new user

Disabled root login via SSH

4. Install Java and Gradle

Installed Java (OpenJDK)

Verified Java installation

Installed Gradle or used Gradle Wrapper provided by the project

5. Deploy the Java Application

Copied the project files to the Droplet (via Git or SCP)

Built the application using Gradle:

./gradlew build

Ran the Java application on the server

6. Application Verification

Verified that the application runs successfully

Checked logs and console output

🔐 Security Considerations

SSH key-based authentication

Disabled root SSH login

Used a dedicated Linux user for deployment

Applied system updates

📚 What I Learned

Basics of cloud infrastructure using DigitalOcean

Linux server administration fundamentals

Secure server setup best practices

Deploying Java applications in a cloud environment

📎 Possible Improvements

Use Docker for containerized deployment

Add firewall rules (UFW)

Automate setup with shell scripts or Ansible

Set up CI/CD pipeline

