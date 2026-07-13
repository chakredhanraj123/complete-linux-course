# 📁 File Management in Linux

## 📖 Overview

File management is one of the most fundamental tasks in Linux. It includes creating, viewing, copying, moving, renaming, and deleting files and directories. Linux provides powerful command-line utilities to perform these operations efficiently.

---

# 📂 File and Directory Management

| Command | Description |
|---------|-------------|
| `ls` | List files and directories in the current location. |
| `cd /path/to/directory` | Change the current working directory. |
| `pwd` | Display the current working directory. |
| `mkdir new_folder` | Create a new directory. |
| `rmdir empty_folder` | Remove an empty directory. |
| `rm file.txt` | Delete a file. |
| `rm -r folder` | Delete a directory and its contents recursively. |
| `cp file1.txt file2.txt` | Copy a file. |
| `cp -r dir1 dir2` | Copy a directory recursively. |
| `mv old_name new_name` | Move or rename a file or directory. |

---

# 📄 File Viewing and Editing

| Command | Description |
|---------|-------------|
| `cat file.txt` | Display the contents of a file. |
| `tac file.txt` | Display file contents in reverse order. |
| `less file.txt` | View a file with scrolling support. |
| `more file.txt` | View a file one page at a time (forward only). |
| `head -n 10 file.txt` | Display the first 10 lines of a file. |
| `tail -n 10 file.txt` | Display the last 10 lines of a file. |
| `nano file.txt` | Open the file in the Nano text editor. |
| `vi file.txt` | Open the file in the Vi editor. |
| `echo "Hello" > file.txt` | Write text to a file (overwrites existing content). |
| `echo "Hello" >> file.txt` | Append text to a file without overwriting existing content. |

---

# 💡 Best Practices

- Always verify your current directory using `pwd` before deleting files.
- Use `cp` to create a backup before modifying important files.
- Be cautious while using `rm -r`, as it permanently deletes directories and their contents.
- Use `less` instead of `cat` to read large files.
- Use `tail -f logfile.log` to monitor log files in real time.

---

# 📝 Summary

Linux file management commands help users efficiently create, view, edit, copy, move, rename, and delete files and directories. These commands are essential for Linux users, System Administrators, DevOps Engineers, and Cloud Engineers, and are used daily in system administration and automation.

---
