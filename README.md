# AWS Command Line

## EC2 — Connect Using SSH

### 1. Connect to EC2 from CMD / Git Bash

Use the following SSH command:

```bash
ssh -i ~/Downloads/aws_test_login.pem ubuntu@65.0.71.177
```

### Command Breakdown

```text
ssh
```

Connect to a remote server using SSH.

```text
-i ~/Downloads/aws_test_login.pem
```

Specifies the private SSH key (`.pem`) used for authentication.

```text
ubuntu@65.0.71.177
```

* `ubuntu` → EC2 server username
* `65.0.71.177` → EC2 public IP address

---

## 2. Fix `.pem` Permission

If SSH shows a permission-related warning, run:

```bash
chmod 400 ~/Downloads/aws_test_login.pem
```

Then connect again:

```bash
ssh -i ~/Downloads/aws_test_login.pem ubuntu@65.0.71.177
```

---

## 3. Switch to Root User

After connecting to the EC2 server:

```bash
sudo su -
```

This switches the current shell to the **root user**.

You can verify the current user with:

```bash
whoami
```

Expected output:

```text
root
```

---

## 4. Useful Commands

### Check current user

```bash
whoami
```

### Ubuntu Software OR Package Update
```bash
   sudo apt update
````

### Ubuntu Install Java
 ```bash
   apt install openjdk-21-jdk
 ```
### Ubuntu Install Python
```bash
   python3 -m hhtp.server 8000
```
### Ubuntu Install Jenkein

```
   sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
     https://pkg.jenkins.io/debian/jenkins.io-2026.key
   echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
     https://pkg.jenkins.io/debian binary/ | sudo tee \
     /etc/apt/sources.list.d/jenkins.list > /dev/null
   sudo apt update
   sudo apt install jenkins
```

### Jenkein status Check with ubuntu 
 ```bash
 systemctl status jenkins
```

### Jenkein setUp with AWS 
 ```bash 
 root@ip-172-31-8-121:~# cat /var/lib/jenkins/secrets/initialAdminPassword

83c02525803944648bbde78c9a60f160

```

### Check current directory

```bash
pwd
```

### List files

```bash
ls
```

Detailed file list:

```bash
ls -la
```

### Move to a directory

```bash
cd /path/to/directory
```

### Go to home directory

```bash
cd ~
```

### Go back one directory

```bash
cd ..
```

### Clear terminal

```bash
clear
```

---

## 5. Exit Root User

To return from the root shell:

```bash
exit
```

If you want to disconnect from the EC2 server completely:

```bash
exit
```

---

## SSH Quick Reference

```bash
# Connect to EC2
ssh -i ~/Downloads/aws_test_login.pem ubuntu@65.0.71.177

# Switch to root
sudo su -

# Check current user
whoami

# Exit root
exit

# Disconnect from EC2
exit
```

## Notes

* Keep the `.pem` private key secure.
* Do not upload the `.pem` file to GitHub.
* Do not share your private key with anyone.
* The EC2 public IP can change if the instance does not use an Elastic IP.
* Replace the IP address with the current EC2 public IP when necessary.
