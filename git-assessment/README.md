# Git & NGINX Practical Assessment

---

# Practical 1 – Git Installation, Configuration & First Repository

## Objective
Install Git, configure user details, create a repository and make the first commit.

## Commands Used

```bash
sudo apt update
sudo apt install git
git --version
git config --global user.name "Kashish Sharma"
git config --global user.email "kashishsharma1504@gmail.com"
mkdir git-training
cd git-training
git init
```

## Create Files

Create README.md

```bash
nano README.md
```

Add content:

```
# Git Training Project
Name: Kashish Sharma
```

Create Python file

```bash
nano app.py
```

Add content:

```python
print("Hello Git from Kashish")
```

## Commit Files

```bash
git add README.md app.py
git commit -m "Initial commit: add README and app.py"
git log
```

Screenshot: `practical-1.md`

---

# Practical 2 – Branching, Commit & Pull Request Workflow

## Objective
Create a new branch and add a calculator module.

## Create Branch

```bash
git branch feature-add-calculator
git checkout feature-add-calculator
```

## Create Calculator File

```bash
nano calculator.py
```

Add content:

```python
def add(a,b):
    return a+b

def subtract(a,b):
    return a-b
```

## Commit Changes

```bash
git add calculator.py
git commit -m "Add calculator module"
```

## Update README

```bash
nano README.md
git add README.md
git commit -m "Update README with calculator module"
```

## Push Branch to GitHub

```bash
git remote add origin https://github.com/username/git-training.git
git push -u origin feature-add-calculator
```

Screenshot: `practical-2.md`

---

# Practical 3 – Git Stash, Undo & History

## Objective
Save temporary changes and manage commit history.

## Modify File

```bash
nano app.py
```

Add line:

```python
print("Testing stash feature")
```

## Stash Changes

```bash
git status
git stash
git stash list
git stash pop
```

## Undo Commit

```bash
git revert HEAD
git commit --amend -m "Updated commit message"
git reset --soft HEAD~1
```

Screenshot: `practical-3.md`

---

# Practical 4 – NGINX Static Website Hosting

## Install NGINX

```bash
sudo apt update
sudo apt install nginx
```

## Start Service

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

## Create Website Directories

```bash
sudo mkdir -p /var/www/app1
sudo mkdir -p /var/www/app2
```

## Create HTML Files

App1

```bash
sudo nano /var/www/app1/index.html
```

Add content:

```html
<h1>Welcome to App1</h1>
```

App2

```bash
sudo nano /var/www/app2/index.html
```

Add content:

```html
<h1>Welcome to App2</h1>
```

Restart NGINX

```bash
sudo systemctl restart nginx
```

Screenshot: `practical-4.md`

---

# Practical 5 – Reverse Proxy with Docker Backend

## Run Docker Container

```bash
docker run -d -p 8080:80 nginx
```

## Configure Reverse Proxy

Edit configuration:

```bash
sudo nano /etc/nginx/sites-available/default
```

Add:

```nginx
location /backend {
    proxy_pass http://127.0.0.1:8080;
}
```

Restart NGINX

```bash
sudo systemctl restart nginx
```

Screenshot: `prcatical-5.md`

---

# Practical 6 – SSL & Load Balancing

## Install Certbot

```bash
sudo apt install certbot python3-certbot-nginx
```

## Generate SSL Certificate

```bash
sudo certbot --nginx
```

## Load Balancing Configuration

```nginx
upstream backend_servers {
    server 127.0.0.1:8081;
    server 127.0.0.1:8082;
}

server {
    listen 80;

    location / {
        proxy_pass http://backend_servers;
    }
}
```

Screenshot: `practical-6.md`

---

# Conclusion

This assessment demonstrated practical implementation of:

- Git repository setup and version control
- Branching and pull request workflow
- Git stash and commit history management
- NGINX static website hosting
- Reverse proxy configuration
- SSL security and load balancing

These tasks represent real-world DevOps practices using Git and NGINX.
---

# Section B – Short Answer Questions

## 1. What is Git?

Git is a distributed version control system used to track changes in source code during software development. It allows multiple developers to collaborate on a project and manage code history efficiently.

---

## 2. What is a Git Repository?

A Git repository is a storage location where project files and their version history are maintained. It contains all commits, branches, and configuration files required for version control.

---

## 3. What is Git Stash?

Git stash temporarily saves uncommitted changes so that you can work on something else without committing those changes. The saved changes can later be restored using `git stash pop`.

Example:

```
git stash
git stash pop
```

---

## 4. Difference Between Git Reset and Git Revert

| Git Reset | Git Revert |
|-----------|------------|
| Removes commits from history | Creates a new commit that undoes changes |
| Used for local history changes | Safe for shared repositories |
| Alters commit history | Preserves commit history |

---

## 5. What is Branching in Git?

Branching allows developers to create separate versions of a project to work on new features or fixes without affecting the main codebase.

Example:

```
git branch feature-branch
git checkout feature-branch
```

---

## 6. What is a Pull Request?

A Pull Request (PR) is used in GitHub to request merging changes from one branch into another. It allows team members to review, discuss, and approve changes before merging.

---

## 7. What is NGINX?

NGINX is a high-performance web server used for serving websites, reverse proxying, load balancing, and caching. It is widely used for hosting web applications and handling large amounts of traffic.

---

## 8. What is a Reverse Proxy?

A reverse proxy is a server that forwards client requests to backend servers and returns the response back to the client. It helps with load balancing, security, and scalability.

Example NGINX configuration:

```
location /backend {
    proxy_pass http://127.0.0.1:8080;
}
```

---

## 9. What is Load Balancing?

Load balancing distributes incoming network traffic across multiple servers to ensure high availability and improved performance.

Example configuration:

```
upstream backend_servers {
    server 127.0.0.1:8081;
    server 127.0.0.1:8082;
}
```

---

## 10. What is SSL?

SSL (Secure Sockets Layer) is a security protocol that encrypts communication between a client and a server. It ensures secure data transmission over the internet and is commonly used for HTTPS websites.
