# 🌐 Apache Web Server – Installation, Configuration & Authentication

This report documents a freelance assignment where I set up and tested an **Apache Web Server** on Kali Linux. The goal was to configure the server, serve custom content, implement basic authentication, and validate access using log files and testing tools.

---

## 📌 Objectives

- Install and configure Apache Web Server on Kali Linux  
- Modify key configuration directives (ServerName, ServerAdmin, etc.)  
- Create and serve a custom HTML webpage  
- Set up directory-level authentication using `.htaccess` and `.htpasswd`  
- Verify server functionality through browser-based testing  
- Review Apache logs for access insights  

---

## 🛠️ Tools & Environment

| Tool        | Purpose                                |
|-------------|----------------------------------------|
| Apache2     | Open-source web server                 |
| Kali Linux  | Host OS for server configuration       |
| `htpasswd`  | Tool to create hashed password files   |
| Web Browser | Client-side testing                    |
| Terminal    | Configuration and monitoring           |

---

## ⚙️ Key Configuration Steps

### 1. 📦 Install Apache
```bash
sudo apt update
sudo apt install apache2
```
### 2. 🛠 Modify Apache Config

Edit Apache’s config to set:

`ServerName`: `www.looneytunes.com` \
`ServerAdmin`: `root@looneytunes.com` \
`ServerSignature`: `Email`

```
sudo nano /etc/apache2/apache2.conf
```
Also add www.`looneytunes.com` to `/etc/hosts` for local DNS resolution.



## 📄 Create a Simple Web Page

```bash
sudo nano /var/www/html/index.html
```

```html
<h1>Welcome to Our Website</h1>
<p>We are excited to have you here!</p>
<a href="/userauth/index.html">Click here for Authenticated Access</a>
```

---

## 🔐 Configure Basic Authentication

### 1. Create Auth Directory

```bash
sudo mkdir /var/www/html/userauth
```

### 2. Add Protected Page

```html
<h1>Welcome Authenticated User!</h1>
```

### 3. Enable `.htaccess` and `.htpasswd`

Create `/var/www/html/userauth/.htaccess`:

```
AuthName "Member's Only!"
AuthUserFile /var/www/html/userauth/.htpasswd
AuthType Basic
Require valid-user
```

Generate credentials:

```bash
sudo htpasswd -c /var/www/html/userauth/.htpasswd test
# Set password as: P@ssw0rd
```

Allow override in Apache:

```bash
sudo nano /etc/apache2/apache2.conf
```

Inside:

```apache
<Directory /var/www/html/userauth>
    AllowOverride All
</Directory>
```

Restart Apache:

```bash
sudo service apache2 restart
```

---

## 🔍 Testing & Verification

* Open browser and go to `http://www.looneytunes.com`
* Click the Auth link → You should be prompted for credentials
* Enter: `test` / `P@ssw0rd`

---

## 📊 Log Analysis

Checked Apache logs for access patterns:

* `/var/log/apache2/access.log`
* `/var/log/apache2/error.log`

These logs helped verify:

* Page access
* Auth attempts
* Server status

---

## 📄 Report

[📥 View Full PDF Report](./Apache.pdf)

---

## 💡 What I Learned

* Real-world Apache setup on Kali
* Importance of directory-based access controls
* Use of `.htaccess` and `.htpasswd` for authentication
* How server logs can aid in incident monitoring

> 🧠 This project helped strengthen my understanding of Linux-based server configuration, security testing, and authentication mechanisms in web environments.