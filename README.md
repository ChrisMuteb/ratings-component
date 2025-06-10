# Ratings Component – Static Frontend Hosting with Jenkins CI/CD + AWS S3

A responsive HTML/CSS project featuring modern **rating card layouts** built with Bootstrap and deployed automatically to AWS S3 using Jenkins.

---

## 🚀 Live Site

🖥️ Hosted on: [http://ratings-component.s3-website-eu-west-1.amazonaws.com](http://ratings-component.s3-website-eu-west-1.amazonaws.com/)

🌍 Region: `eu-west-1` (Ireland)

---

## 📦 Features

- ⚡️ Responsive design using **Bootstrap 5**
- 🎨 Icon support with **Bootstrap Icons**
- 🏗️ CI/CD pipeline using **Jenkins**
- ☁️ Static site hosted on **AWS S3**
- 🔐 Secure pipeline with **Jenkins credentials** for AWS keys

---

## 🛠️ Tech Stack

| Layer          | Technology                      |
| -------------- | ------------------------------- |
| Frontend       | HTML, CSS, Bootstrap            |
| Icons          | Bootstrap Icons (SVG-based)     |
| CI/CD          | Jenkins (Declarative Pipeline)  |
| Hosting        | AWS S3 (Static Website Hosting) |
| Infrastructure | EC2 (Jenkins host)              |

---

## 🔄 Deployment Pipeline (Jenkins)

1. **Code pushed to GitHub**
2. **Jenkins pipeline triggered** automatically or manually
3. Source code is synced to an S3 bucket:

   ```bash
   aws s3 sync . s3://ratings-component --delete --exclude ".git/*"

   ```
