Here are the commonly used `scp` (secure copy) commands for transferring files between your local machine and a remote EC2 instance (both directions):

---

### ✅ **From EC2 (Remote) to Local:**

```bash
scp -i /path/to/key.pem ec2-user@<EC2-PUBLIC-IP>:/remote/path/to/file /local/destination/path
```

**Example:**

```bash
scp -i ~/keys/my-ec2-key.pem ec2-user@3.120.45.67:/home/ec2-user/data.txt ~/Downloads/
```

---

### ✅ **From Local to EC2 (Remote):**

```bash
scp -i /path/to/key.pem /local/path/to/file ec2-user@<EC2-PUBLIC-IP>:/remote/destination/path
```

**Example:**

```bash
scp -i ~/keys/my-ec2-key.pem ~/Documents/app.zip ec2-user@3.120.45.67:/home/ec2-user/
```

---

### ⚠️ Notes:

* Replace `ec2-user` with the correct username (`ubuntu` for Ubuntu instances).
* Ensure the destination directory has the right permissions.
* `-i` flag is for your PEM private key used to access the EC2 instance.
* If you're copying **directories**, add `-r`:

```bash
scp -i /path/to/key.pem -r /local/folder ec2-user@<EC2-IP>:/remote/path/
```

- ---------------------------------------------------
To **move files from an EC2 instance to your local machine**, you should run the `scp` command **from your local computer’s terminal**, not from inside the EC2 instance.

---

### ✅ **Steps to do it correctly:**

1. **Open Terminal on your local machine** (e.g., macOS, Linux, or WSL/PowerShell on Windows).
2. **Run this command from your local terminal** (replace the paths if needed):

```bash
scp -i ~/Downloads/mydevopsmumbai.pem ec2-user@15.206.27.150:/home/ec2-user/DEVOPS.zip .
```

---

### 📌 Breakdown:

* `scp`: Secure copy
* `-i ~/Downloads/mydevopsmumbai.pem`: Path to your **private key file**
* `ec2-user@15.206.27.150:/home/ec2-user/DEVOPS.zip`: **Remote file** on your EC2 instance
* `.`: Copy it to your **current local directory**

> 💡 Tip: You can replace `.` with a full local path like `~/Documents/` if you want it to land in a specific folder.

---

Would you like help setting up file transfers between **two EC2 instances** or automating the copy?
- ------------------------------------------------------------
If you're getting a **"Permission denied (publickey)"** error when running `scp` **from your local machine**, here are the most common causes and how to fix them:

---

### 🔒 **1. Incorrect or missing `.pem` file**

**Error message:**

```
Permission denied (publickey)
```

#### ✅ Fix:

* Make sure the file path is **correct** and the file has the **right permissions**.

```bash
chmod 400 ~/Downloads/mydevopsmumbai.pem
```

This ensures only your user can read the key — required by SSH.

---

### 📁 **2. Wrong username in the command**

If your EC2 instance is Amazon Linux or RHEL, the user is likely `ec2-user`. For Ubuntu, it's `ubuntu`.

#### ✅ Fix:

Double-check you’re using the correct user:

```bash
scp -i ~/Downloads/mydevopsmumbai.pem ec2-user@15.206.27.150:/home/ec2-user/DEVOPS.zip .
```

Try `ubuntu@15.206.27.150` if it's an Ubuntu server.

---

### 🔐 **3. Key doesn't match the instance**

If you're using the wrong `.pem` file — one that **wasn’t used to launch that EC2 instance** — authentication will fail.

#### ✅ Fix:

Make sure the `.pem` file you're using matches the key pair associated with the EC2 instance.

---

### 🧪 **Test with SSH:**

Try connecting directly via SSH:

```bash
ssh -i ~/Downloads/mydevopsmumbai.pem ec2-user@15.206.27.150
```

* If that fails, the issue is definitely with the key or username.
* If it succeeds, then `scp` should work with the same parameters.

---

Would you like to paste the exact command and error you're getting so I can troubleshoot more precisely?
- --------------------------------------------------------
