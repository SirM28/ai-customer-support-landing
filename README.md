# AI-Powered Customer Support Landing Page

## 🚀 Project Title
**The Future of AI-Powered Customer Support**

## 👨‍💻 Author
**Mayowa Oladunni**  
*Lead Cloud Engineer*

## 📖 Project Description
This project is a professional and dynamic landing page deployed on a cloud-hosted Ubuntu server. It showcases technical proficiency in full-stack web development, cloud infrastructure, reverse proxy setup, and HTTPS security using Let's Encrypt.

We are reimagining customer support with AI that truly understands and resolves queries in real-time. Our platform leverages natural language processing and machine learning to provide faster, smarter, and more human-like support at scale.

---

## 💡 Features
- Responsive landing page using **Tailwind CSS**
- Animated content load using `@keyframes`
- Reverse proxy with **Nginx** to a **Node.js/Express** server
- Deployed on **AWS EC2 (Ubuntu)**
- **SSL** enabled with **Certbot (Let's Encrypt)**

---

## 🛠️ Setup Instructions

### 1. Provision Server
- Cloud Provider: AWS (EC2)
- OS: Ubuntu 20.04 LTS

### 2. Install Dependencies
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install nginx nodejs npm git curl ufw -y
```

### 3. Set Up Node.js Server
```bash
mkdir app && cd app
npm init -y
npm install express
```

Create `index.js`:
```js
const express = require('express');
const path = require('path');
const app = express();

app.use(express.static(path.join(__dirname, 'public')));

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => console.log(`Server running on port ${PORT}`));
```

### 4. Start with PM2
```bash
sudo npm install pm2 -g
pm2 start index.js
pm2 startup
pm2 save
```

### 5. Set Up Nginx Reverse Proxy
```bash
sudo nano /etc/nginx/sites-available/default
```
Paste:
```nginx
server {
    listen 80 default_server;
    listen [::]:80 default_server;

    server_name mcustomersupportai.work.gd;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```
Then:
```bash
sudo nginx -t
sudo systemctl reload nginx
```

### 6. Enable HTTPS with Certbot
```bash
sudo apt install certbot python3-certbot-nginx -y
sudo certbot --nginx -d mcustomersupportai.work.gd
```

### 7. Firewall Setup
```bash
sudo ufw allow 'Nginx Full'
sudo ufw allow OpenSSH
sudo ufw enable
```

---

## 🌐 Live Link
🔗 https://mcustomersupportai.work.gd

---

## 📁 File Structure
```
app/
├── index.js
├── public/
│   └── index.html
```

---

## 📸 Screenshot
![Screenshot of deployed landing page](./Screenshot (377).png)

---

## 🧠 Skills Demonstrated
- Cloud Engineering
- Linux Server Provisioning
- Web Server (Nginx)
- Reverse Proxy Configuration
- SSL/HTTPS
- Node.js Web App Deployment

---

## 📬 Contact
**Email:** mayowaoladunni12@gmail.com

---

## ✅ Submission Info
Submitted for the AltSchool of Engineering Tinyuka Second Semester Project – Cloud Engineering Track.

