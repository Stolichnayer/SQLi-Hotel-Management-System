# SQL Injection in tushar-2223 Hotel Management System
<table>
  <tr>
    <td>
      <h3> https://github.com/tushar-2223/Hotel-Management-System </h3>
    </td>
  </tr>
</table>

## 📜 Description
Hotel Management System up to commit bb1f3b3666124b888f1e4bcf51b6fba9fbb01d15 contains an authenticated SQL Injection vulnerability in the room reservation functionality.

The vulnerability exists in the `POST /<directory>/home.php` endpoint, where user-controlled POST parameters (such as Name, Email, and other reservation fields) are directly concatenated into an SQL INSERT query without proper input sanitization or the use of prepared statements.
An authenticated attacker can inject arbitrary SQL code, leading to unauthorized database interaction. The issue was confirmed using a time-based blind SQL injection technique.

## 🔍 Affected Versions

| Status       | Commit         |
|--------------|-----------------|
| 🔴 Vulnerable |   `≤ bb1f3b3666124b888f1e4bcf51b6fba9fbb01d15`      | 

## 🛠️ Steps to Reproduce

#### 1️⃣ Log in to the application as a valid user
#### 2️⃣ Navigate to the room reservation functionality
#### 3️⃣ Intercept the following request:
```
POST /<directory>/home.php
```
#### 4️⃣ Inject a time-based SQL payload into a vulnerable POST parameter (e.g. Name):
```
Name=Alex'%2b(select*from(select(sleep(10)))a)%2b'
```
#### 5️⃣ Send the request
#### 6️⃣ Observe the server response delay increasing from approximately 20 ms to 10,019 ms, confirming SQL injection execution:

<img src="/Normal.png" >

<img src="/Injection.png">

## ⚠️ Disclaimer
This project is intended for **educational and ethical research purposes only**. Unauthorized testing on systems without explicit permission is illegal. Use responsibly and only on systems you own or have permission to test.

## 🧑‍💻 Discovery

This vulnerability was discovered by **Alex Perrakis** (Stolichnayer).

## 🔗 References:
- [Hotel Management System Repository](https://github.com/tushar-2223/Hotel-Management-System)

