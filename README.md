# Assignment Scripts Documentation

This repository contains setup scripts for **Assignment 10**, **Assignment 11**, and **Assignment 12**. Each script automates the installation and configuration of a web server and deployment environment for Node.js applications.

---

## 📁 Assignment 10

### 🔧 Script Overview

This script installs and starts the Nginx web server, installs Git, and sets up Node.js version 18.

### 🖥️ Script

```bash
#!/bin/bash
apt-get update
apt-get upgrade
apt-get install -y nginx
systemct1 start nginx
systemct1 enable nginx
apt-get install -y git
curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -
apt-get install -y nodejs
````

### ⚠️ Notes

* There is a **typo** in the script: `systemct1` should be `systemctl`. Make sure to correct it before running.
* This script **does not run any app**, it only sets up the environment.

---

## 📁 Assignment 11 & 12

### 🔧 Script Overview

This script builds upon Assignment 10 by:

* Installing required packages
* Cloning a GitHub repository
* Installing Node.js dependencies
* Running a Node.js application

### 🖥️ Script

```bash
#!/bin/bash
apt-get update
apt-get upgrade
apt-get install -y nginx
systemctl start nginx
systemctl enable nginx
apt-get install -y git
curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -
apt-get install -y nodejs
git clone https://github.com/dhOOpmon/ASS-9.git
cd ASS-9
npm install
node index.js
```


# Assignment 12 – NGINX Reverse Proxy Configuration

This repository contains a snippet of an NGINX configuration used in **Assignment 12** to set up a reverse proxy to forward HTTP requests from NGINX to a backend service running on `localhost:4000`.

## Description

The following NGINX directives configure a reverse proxy:

```nginx
proxy_pass http://localhost:4000;
proxy_http_version 1.1;
proxy_set_header Upgrade $http_upgrade;
proxy_set_header Connection 'Upgrade';
proxy_set_header Host $host;
proxy_cache_bypass $http_upgrade;
```

### Purpose

This configuration is used to:

* Forward incoming client requests to a backend server running on port `4000`.
* Enable support for WebSocket connections (via `Upgrade` and `Connection` headers).
* Preserve the original `Host` header.
* Prevent caching of upgraded connections (commonly used for real-time communication).

## Use Case

This setup is typically used in Node.js applications using frameworks like Express or NestJS, where the server runs on a different port (like 4000) and NGINX acts as a frontend reverse proxy.

## Prerequisites

* NGINX must be installed and running.
* A backend service (e.g., Node.js) must be running on `localhost:4000`.

## Installation

1. Add the provided configuration block inside a server block in your NGINX config (e.g., `/etc/nginx/sites-available/default` or your custom site config).
2. Test the configuration:

   ```bash
   sudo nginx -t
   ```
3. Reload NGINX:

   ```bash
   sudo systemctl reload nginx
   ```

## Notes

* Make sure to correct the typo in `Upgarde`. It should be `Upgrade`:

  ```nginx
  proxy_set_header Upgrade $http_upgrade;
  ```


### 📦 Repository Used

* [`ASS-9`](https://github.com/dhOOpmon/ASS-9): A Node.js project that is cloned and executed by the script.

### ✅ Output

If successful, this script will start a Node.js server using the `index.js` file in the `ASS-9` repository.

---

## 💡 Tips

* Always run the scripts with `sudo` if needed.
* Ensure the system has network access to download packages and clone the repository.

