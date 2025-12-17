# DigitalOcean Java Deployment

**Demo Projekt:** Java-Anwendung auf einem DigitalOcean-Droplet deployen

## Technologien

* Java
* Gradle
* Ubuntu Linux
* DigitalOcean

## Projektstruktur

```
digitalocean-java-deployment/
├── src/main/java/Main.java
├── build.gradle
├── .gitignore
└── README.md
```

* `src/main/java` → Quellcode
* `build.gradle` → Gradle Build-Konfiguration
* `.gitignore` → ignoriert Build-Artefakte, `.jar`, IntelliJ-Dateien

---

## Server Setup (DigitalOcean)

1. Droplet auf DigitalOcean erstellen (Ubuntu)
2. Neuen User anlegen (Security Best Practice):

```bash
adduser demo
usermod -aG sudo demo
```

3. SSH-Key für `demo` einrichten:

```bash
# lokal erzeugen
ssh-keygen -t ed25519 -C "demo@digitalocean"
# öffentlichen Key auf Droplet kopieren
scp ~/.ssh/id_ed25519.pub demo@<DROPLET_IP>:/home/demo/.ssh/authorized_keys
```

---

## Projekt Deployment

1. **Repo klonen**

```bash
git clone git@github.com:coffeezon3/digitalocean-java-deployment.git
cd digitalocean-java-deployment
```

2. **Build erzeugen**

```bash
gradle build
```

* `.jar` Datei liegt in `build/libs/digitalocean-java-deployment-1.0.0.jar`

3. **JAR auf Droplet kopieren**

```bash
scp build/libs/digitalocean-java-deployment-1.0.0.jar demo@<DROPLET_IP>:/home/demo/
```

4. **Auf Droplet ausführen**

```bash
ssh demo@<DROPLET_IP>
java -jar digitalocean-java-deployment-1.0.0.jar
```

* Ausgabe: `Hello DigitalOcean!`

---

## Hinweise

* `.jar` Dateien werden nicht ins Repo gepusht – sie können jederzeit mit Gradle gebaut werden
* Sicherheitsbestpractice: kein Root-Zugriff für tägliche Nutzung, eigener User für Deployment
* Repo enthält nur Quellcode und Konfiguration; Build-Artefakte werden lokal oder auf Droplet erzeugt

Demo Project: Create Server and Deploy Java Application on DigitalOcean
---------------------------------------------
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

