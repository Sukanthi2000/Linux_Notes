
Welcome to the world of **Linux file permissions** — a simple yet powerful system that protects your files and keeps your system secure.

---

## 🔐 What Are File Permissions?

Every file and directory in Linux has a set of permissions that define **who** can do **what** with them.
Permissions determine whether you can **read**, **write**, or **execute** a file.

Each file has:

* **Owner (u)** → usually the creator
* **Group (g)** → a set of users
* **Others (o)** → everyone else

Example:

```bash
ls -l
```

Output:

```
-rwxr-xr--
```

Let’s break it down:

| Position | Permission Type | Meaning                                     |
| -------- | --------------- | ------------------------------------------- |
| 1st      | `-`             | File type (`-` for file, `d` for directory) |
| 2–4      | `rwx`           | Owner permissions                           |
| 5–7      | `r-x`           | Group permissions                           |
| 8–10     | `r--`           | Others permissions                          |

So in the example above:

* **Owner** can read, write, and execute
* **Group** can read and execute
* **Others** can only read

---

## ⚙️ Permission Values

Each permission type has a numeric value:

| Symbol | Value | Meaning |
| ------ | ----- | ------- |
| `r`    | 4     | Read    |
| `w`    | 2     | Write   |
| `x`    | 1     | Execute |

Add them up to set combined permissions:

* `7` = read + write + execute
* `6` = read + write
* `5` = read + execute
* `4` = read-only

Example:

```bash
chmod 755 script.sh
```

Translates to:

```
rwxr-xr-x
```

✅ Owner: all permissions
✅ Group: read & execute
✅ Others: read & execute

---

## 🛠️ Commands Cheat Sheet

| Command | Description                 | Example                    |
| ------- | --------------------------- | -------------------------- |
| `ls -l` | List files with permissions | `ls -l`                    |
| `chmod` | Change file permissions     | `chmod 644 file.txt`       |
| `chown` | Change file owner           | `sudo chown user file.txt` |
| `chgrp` | Change file group           | `sudo chgrp devs file.txt` |

---

## 🧩 Changing Permissions

### Symbolic Method

```bash
chmod u+x script.sh   # Add execute permission to user
chmod g-w file.txt    # Remove write permission from group
chmod o=r report.log  # Set read-only for others
```

### Numeric Method

```bash
chmod 755 script.sh   # rwx for owner, r-x for group and others
chmod 644 notes.txt   # rw for owner, r for everyone else
```

---

## 👑 Ownership Commands

Linux permissions depend on **who owns the file** and **which group** it belongs to.

```bash
chown user file.txt      # Change owner
chgrp developers file.txt # Change group
chown user:group file.txt # Change both
```

---

## 🚨 Common Mistakes & Fixes

| Problem                   | Cause                       | Fix                            |
| ------------------------- | --------------------------- | ------------------------------ |
| `Permission denied`       | File isn’t executable       | `chmod +x filename`            |
| `Cannot edit file`        | You don’t have write access | `chmod u+w filename`           |
| `Operation not permitted` | You’re not the owner        | `sudo chown youruser filename` |
| `Command not found`       | No execute permission       | `chmod +x script.sh`           |

---

## 🧠 Pro Tips

* Never use `chmod 777` — it gives *everyone* full access (a major security risk).
* Use `sudo` wisely — root access overrides permissions, but mistakes can break your system.
* Automate safe defaults using `umask`.
* Check permissions regularly using `ls -l` or `stat filename`.

---

## 🧭 Quick Recap

| Type    | Symbol | Numeric | Description      |
| ------- | ------ | ------- | ---------------- |
| Read    | `r`    | 4       | View contents    |
| Write   | `w`    | 2       | Modify or delete |
| Execute | `x`    | 1       | Run or enter     |

---

## 🏁 Example Workflow

```bash
# Create a script
echo "echo Hello Linux" > hello.sh

# Make it executable
chmod 755 hello.sh

# Verify permissions
ls -l hello.sh
# Output: -rwxr-xr-x

# Run the script
./hello.sh
# Output: Hello Linux
```

Now you’ve mastered file permissions — no more “Permission denied” headaches! 🎉

---

### ✍️ Author

Created by **Sukanthi R** — helping developers decode Linux, one command at a time.

If you found this helpful, ⭐ the repo and share it with your fellow Linux explorers!

---


