# COPY ONE FILE TO ANOTHER
To copy content from one file to another in `vi` or using shell commands, here’s how you can do it:

### Method 1: **Using `vi` (or `vim`) Editor**

1. **Open the source file in `vi`**:

   ```bash
   vi source_file.html
   ```

2. **Copy content from the source file**:

   * **Visual Mode**: Position your cursor at the beginning of the text you want to copy.
   * Press `v` to enter **visual mode** (character-wise).
   * Move the cursor to the end of the content you want to copy.
   * Press `y` to "yank" (copy) the selected content.

3. **Open the target file in `vi`**:

   ```bash
   vi target_file.html
   ```

4. **Paste content in the target file**:

   * Move the cursor to the location where you want to paste.
   * Press `p` to paste the content.

5. **Save the changes**:

   * Type `:w` to save the file.
   * Type `:q` to quit `vi`, or `:wq` to save and quit at the same time.

---

### Method 2: **Using Shell Commands (Without `vi`)**

If you want to copy content directly from one file to another, you can use the following shell commands:

1. **Copy content from one file to another**:

   ```bash
   cp source_file.html target_file.html
   ```

2. **Append content from one file to another**:
   If you just want to append content (rather than overwrite), use:

   ```bash
   cat source_file.html >> target_file.html
   ```

3. **Copy a specific part of the file using `head` or `tail`**:
   If you want to copy specific lines, you can use commands like `head` or `tail`. For example, to copy the first 10 lines:

   ```bash
   head -n 10 source_file.html >> target_file.html
   ```

4. **Using `sed` or `awk` for more advanced selection**:
   For more fine-grained control over copying content based on patterns, you can use `sed` or `awk`.

   Example: Copy lines between a specific range of line numbers:

   ```bash
   sed -n '5,10p' source_file.html >> target_file.html
   ```

---

### Method 3: **Using `scp` for Remote Copying**

If you're copying from one remote system to another:

```bash
scp user@remote:/path/to/source_file.html /path/to/target_file.html
```

---
- -------------------------------------------------------------------------------------------------------------
To **delete all the content in a file using `vi` (or `vim`)**, follow these steps:

---

### 🔥 Steps to Delete All Content in `vi`:

1. Open the file in `vi`:

   ```bash
   vi filename.txt
   ```

2. Once inside `vi`, press:

   ```
   Esc
   ```

3. Then type the following and press **Enter**:

   ```
   :%d
   ```

   * `:` — enters command mode
   * `%` — means the **entire file**
   * `d` — means **delete**

4. (Optional) To save and exit:

   ```
   :wq
   ```

   or just exit without saving:

   ```
   :q!
   ```

---

✅ **Summary:**

* `:%d` → Deletes all lines in the file
* `:wq` → Saves and quits

- -------------------------------------------------------------------
To delete a file that was created with `vi` (or any file) from the directory, you can use the `rm` command in the terminal.

Here’s how you can delete the file:

### 1. **Delete a File Using `rm`**

To delete a file in the terminal:

```bash
rm filename.html
```

Replace `filename.html` with the actual name of the file you want to delete.

### 2. **Force Delete the File**

If the file is write-protected, or you’re not prompted for confirmation, use the `-f` option to force delete:

```bash
rm -f filename.html
```

### 3. **Delete a Directory and Its Contents**

If you want to delete a directory (and its contents), use the `-r` (recursive) option:

```bash
rm -r directory_name
```

If the directory contains files that are write-protected, and you want to avoid confirmation prompts, use `-rf`:

```bash
rm -rf directory_name
```

### 4. **Interactive Deletion**

If you want to confirm each file deletion before it's removed, use the `-i` option:

```bash
rm -i filename.html
```

### 5. **Deleting Inside `vi` (While Editing a File)**

If you're inside `vi` and want to delete the file without leaving the editor:

1. Press `Esc` to ensure you're in command mode.
2. Type `:q!` to quit without saving, if you haven't saved the file.
3. If you've saved the file and want to delete it after quitting, exit `vi` using `:wq` and then use the `rm` command outside `vi` to remove the file.

---
- ---------------------------------------------------------
# If i want my code back
If you've deleted content while editing a file in `vi` (or `vim`), whether you can recover it depends on **how and when** you deleted it:

---

### 🛠️ **Case 1: You haven't saved (`:w`) yet**

If you deleted text but **haven’t saved the file**, you can undo the changes:

* Press `u` (in normal mode) — this undoes the last change.
* You can keep pressing `u` to undo multiple steps.
* To redo something you undid: press `Ctrl + r`.

✅ You can recover the deleted content **as long as you haven’t written (`:w`) and quit (`:q`)**.

---

### 🛠️ **Case 2: You saved and quit (`:wq`)**

Once you've saved and exited, **recovery is difficult**. `vi` does not keep a backup by default.

Possible options:

* If a **backup or swap file** exists (e.g., `.filename.swp`), `vi` may offer to recover it when you open the file again.
* Example prompt:

  ```
  E325: ATTENTION
  Found a swap file by the name ".file.txt.swp"
  ```

  In that case, you can choose `[R]ecover`.

---

### 🛠️ **Case 3: Use OS recovery options (if available)**

* Check your system’s temp or backup folders.
* Use file recovery tools like `extundelete` (Linux ext filesystems), `TestDisk`, etc., if the file was overwritten.

---

### ✏️ Tip for Future

Enable backups in `.vimrc`:

```vim
set backup
set backupdir=~/.vim/backups
```

---
- ---------------------------------------------------------------
