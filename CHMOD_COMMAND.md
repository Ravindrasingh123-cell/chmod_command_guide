# `chmod` Command Guide

The `chmod` command in Linux/Unix is used to **change file or directory permissions**. This guide covers:

- Understanding file permissions
- Symbolic and numeric modes
- How to view and change permissions
- Examples

---

##  1. Understanding File Permissions

Each file or directory has **three types of users**:

- **User (u)**: The owner
- **Group (g)**: Users in the file's group
- **Others (o)**: Everyone else

Each can have **three types of permissions**:
```
| Permission | Symbol | Description                |
|------------|--------|----------------------------|
| Read       | `r`    | View contents              |
| Write      | `w`    | Modify contents            |
| Execute    | `x`    | Run as a program/script    |

```

Use the `ls -l` for given directory contents  and `ls -ld` command for directory itself to view permissions:

```bash
ls -ld d1

Example output:

ravindrasinghnagarkoti@Ravindras-MacBook-Air ~ % ls -ld d1
drwxr-xr-x  3 ravindrasinghnagarkoti  staff  96 20 Aug 11:53 d1

Breakdown:

- : File type (- = file, d = directory)

rwx : User permissions

r-x : Group permissions

r-- : Others permissions

2. Numeric (Octal) Mode
Each permission has a number:

Permission	 Value
Read (r)	   4
Write (w)	   2
Execute (x)	   1

Add values to set permissions:

Permission Combo	Value
rwx	7 (4+2+1)
rw-	6 (4+2)
r--	4

So chmod 754 file.txt means:

7 → user: rwx

5 → group: r-x

4 → others: r--

✅ Example

chmod 755 myscript.sh
Output : rwxr-xr-x

3. Symbolic Mode
You can also change permissions with symbols:

Symbol	Meaning
+	Add
-	Remove
=	Set exact

✅ Examples

chmod u+x script.sh
Adds execute permission to user.

chmod g-w notes.txt
Removes write from group.

chmod o=r report.log
Sets others to read-only.



4. How to Check Current Permissions

Use:
ls -l filename
To view permissions on a directory and its contents:

ls -l /path/to/directory


5. How to Change Permissions

With numeric mode:

chmod 644 document.txt

With symbolic mode:

chmod u+w document.txt

To recursively change permissions (e.g., all files in a folder):

chmod -R 755 /path/to/folder


6. Tips
Use chmod carefully—giving 777 makes the file executable and writable by anyone.

For scripts, ensure they are executable: chmod +x script.sh

Combine with chown to manage ownership.

Common Use Cases

        Task	                     Command

Make script executable	       chmod +x script.sh
Remove write for others	       chmod o-w file.txt
Set read-only for all	       chmod 444 file.txt
Full access for user only	   chmod 700 secret.txt