To check whether your **Downloads** folder has a `.pem` file in Linux, you can use the following command:

```bash
ls ~/Downloads/*.pem
```

### What this does:

* `ls`: Lists files.
* `~/Downloads/`: Refers to your Downloads folder.
* `*.pem`: Matches any file with a `.pem` extension.

### If you want a clearer message (e.g., exists or not), use:

```bash
if ls ~/Downloads/*.pem 1> /dev/null 2>&1; then
    echo ".pem file exists in Downloads"
else
    echo "No .pem file found in Downloads"
fi
```

Would you like to search subdirectories too?
- -----------------------------------------------------
To **search for a `.pem` file** on your local Linux system, you can use the `find` command:

---

### 🔍 Search from your home directory:

```bash
find ~ -type f -name "*.pem"
```

This will look for all files ending in `.pem` under your home folder.

---

### 🔍 Search from the root directory (more thorough, but slower):

```bash
sudo find / -type f -name "*.pem" 2>/dev/null
```

* `sudo`: Required for access to some system folders.
* `2>/dev/null`: Hides permission-denied errors.

---

### 🔍 Search with partial name (e.g., "devops")

```bash
find ~ -type f -iname "*devops*.pem"
```

* `-iname`: Case-insensitive match
* `*devops*`: Wildcards before and after “devops”

---

Once found, you can use the path it returns in your `scp` or `ssh` command.

Would you like help locating it based on your browser’s download history or common folders like `Downloads`?
- -----------------------------------------------------
