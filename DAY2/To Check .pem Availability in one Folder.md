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

