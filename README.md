# 🚀 Azure Redis Authentication System

A simple **user authentication system** built using:

- **Azure Virtual Machine (Ubuntu)**
- **Azure Cache for Redis** (stores username–password pairs)
- **Node.js + Express** backend
- **HTML Frontend** served directly from Node.js

This project demonstrates how to integrate Azure resources with a lightweight web application and Redis-based authentication.

---

## 📌 Features

✔ Register new users  
✔ Login using username/password  
✔ Remove existing users  
✔ View all registered users  
✔ Secure data storage using Azure Cache for Redis (TLS 6380)

---

## 1. Azure Virtual Machine Setup

### Create Ubuntu VM
1. Open **Azure Portal**
2. Search → **Virtual Machines**
3. Click **Create → Azure Virtual Machine**
4. Choose:
   - Image: **Ubuntu 22.04 LTS**
   - Size: **Standard B1s**
   - Authentication: Password or SSH Key
5. Deploy the VM

### Allow App Port (3000)
Go to:

**VM → Networking → Add Inbound Port Rule**

- Port: **3000**
- Protocol: **TCP**
- Action: **Allow**

---

## 2. Azure Cache for Redis Setup

### Create Redis Instance
1. Azure Portal → **Create Resource**
2. Search: **Azure Cache for Redis**
3. Select:
   - Tier: **Basic C0 or C1**
   - Access: **Public**
   - TLS: **Enabled**

### Get Redis Credentials
Go to:

**Redis → Access Keys**

Copy:
- Hostname  
- Primary Key  

(Used in `app.js` to connect Redis with Node.js)

---

## 3. Connect to VM (Using puTTY)

```bash
Azureuser@135.235.136.230
```

Install dependencies:

```bash
sudo apt update
sudo apt install -y nodejs npm redis-tools
```

---

## 4. Project Folder Structure

```
~/Backend/
 ├── app.js
 ├── Redis.html
 └── node_modules/
```

---

## 5. Run the Backend

Start the server:

```bash
cd ~/Backend
node app.js
```

Expected logs:

```
Server running on port 3000
Redis: connected
Redis: ready
```

---

## 6. Access Frontend

Open your browser:

```
http://135.235.136.230:3000/Redis.html
```

This UI allows registration, login, removing users, and viewing all users.

---

## 7. API Testing (Optional)

### Register User
```bash
curl -X POST http://localhost:3000/register \
  -H "Content-Type: application/json" \
  -d '{"username":"alex","password":"pass"}'
```

### Login
```bash
curl -X POST http://localhost:3000/login \
  -H "Content-Type: application/json" \
  -d '{"username":"alex","password":"pass"}'
```

### Remove User
```bash
curl -X POST http://localhost:3000/remove \
  -H "Content-Type: application/json" \
  -d '{"username":"alex"}'
```

### Show All Users
```bash
curl http://localhost:3000/users
```

## Technologies Used

- Azure Virtual Machine  
- Azure Cache for Redis  
- Node.js  
- Express.js  
- HTML / CSS / JavaScript  
- Redis (ioredis client)


## Contributor
Alexyesudass S  

