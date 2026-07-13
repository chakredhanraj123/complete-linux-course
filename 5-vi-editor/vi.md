# VI Editor (Vim) Cheat Sheet

## 📌 What is VI Editor?

**VI (Visual Editor)** is a command-line text editor available on almost every Linux and Unix system. It is widely used by Linux administrators, DevOps engineers, and developers to create and edit configuration files directly from the terminal.

> **Note:** `vim` (Vi Improved) is an enhanced version of the original `vi` editor with additional features like syntax highlighting, multiple undo levels, and plugins.

---

# VI Editor Modes

VI editor works in **three different modes**.

| Mode | Description |
|------|-------------|
| **Normal Mode** | Default mode used for navigation, deleting, copying, pasting, and executing commands. |
| **Insert Mode** | Used for typing and editing text. Press `i` to enter and `Esc` to return to Normal mode. |
| **Command Mode** | Used to save, quit, search, and execute editor commands. Press `:` from Normal mode to enter Command mode. |

---

# Basic Navigation

| Shortcut | Description |
|----------|-------------|
| `h` | Move cursor left |
| `l` | Move cursor right |
| `j` | Move cursor down |
| `k` | Move cursor up |
| `0` | Move to the beginning of the line |
| `^` | Move to the first non-blank character |
| `$` | Move to the end of the line |
| `w` | Move to the beginning of the next word |
| `b` | Move to the beginning of the previous word |
| `gg` | Go to the beginning of the file |
| `G` | Go to the end of the file |
| `:n` | Go to line number **n** (Example: `:25`) |

---

# Insert Mode Shortcuts

| Shortcut | Description |
|----------|-------------|
| `i` | Insert before the cursor |
| `I` | Insert at the beginning of the line |
| `a` | Append after the cursor |
| `A` | Append at the end of the line |
| `o` | Open a new line below the current line |
| `O` | Open a new line above the current line |
| `Esc` | Exit Insert mode and return to Normal mode |

---

# Editing Text

| Shortcut | Description |
|----------|-------------|
| `x` | Delete the character under the cursor |
| `X` | Delete the character before the cursor |
| `dw` | Delete one word |
| `dd` | Delete the current line |
| `d$` | Delete from the cursor to the end of the line |
| `d0` | Delete from the cursor to the beginning of the line |
| `D` | Delete from the cursor to the end of the line (same as `d$`) |
| `u` | Undo the last change |
| `Ctrl + r` | Redo the last undone change |
| `yy` | Copy (yank) the current line |
| `yw` | Copy one word |
| `p` | Paste after the cursor |
| `P` | Paste before the cursor |

---

# Search and Replace

| Shortcut | Description |
|----------|-------------|
| `/pattern` | Search forward for a word or pattern |
| `?pattern` | Search backward for a word or pattern |
| `n` | Move to the next search result |
| `N` | Move to the previous search result |
| `:%s/old/new/g` | Replace all occurrences of **old** with **new** in the entire file |
| `:s/old/new/g` | Replace all occurrences in the current line |

---

# Working with Files

| Shortcut | Description |
|----------|-------------|
| `:e filename` | Open another file |
| `:w` | Save the current file |
| `:wq` | Save and quit |
| `:q!` | Quit without saving changes |
| `:split filename` | Split the window horizontally and open another file |
| `:vsplit filename` | Split the window vertically and open another file |
| `Ctrl + w + w` | Switch between split windows |

---

# Most Frequently Used Commands

| Command | Purpose |
|---------|---------|
| `vi filename` | Open or create a file |
| `i` | Start editing |
| `Esc` | Stop editing |
| `:w` | Save |
| `:wq` | Save and Exit |
| `:q!` | Exit without saving |
| `dd` | Delete line |
| `yy` | Copy line |
| `p` | Paste |
| `u` | Undo |
| `/text` | Search text |

---

# Example Workflow

```bash
vi notes.txt
```

1. Press **`i`** to enter Insert mode.
2. Type your content.
3. Press **`Esc`** to return to Normal mode.
4. Type **`:wq`** and press **Enter** to save and exit.

---

# Why Learn VI Editor?

- Available on almost every Linux and Unix system.
- Essential for Linux System Administrators and DevOps Engineers.
- Lightweight and fast terminal-based editor.
- Commonly used to edit configuration files, scripts, and log files.
- Works efficiently even on remote servers over SSH.

---

## Quick Revision

- **Normal Mode** → Navigation and commands
- **Insert Mode** → Editing text
- **Command Mode** → Save, Quit, Search
- **`Esc`** → Return to Normal mode
- **`:wq`** → Save and Exit
- **`:q!`** → Exit without saving
- **`dd`** → Delete line
- **`yy`** → Copy line
- **`p`** → Paste
- **`u`** → Undo
- **`Ctrl + r`** → Redo

---

## Summary

The **VI Editor** is one of the most important command-line editors in Linux. By understanding its three modes and mastering common navigation, editing, search, and file management commands, you can efficiently edit files on local and remote Linux systems. Learning VI is an essential skill for every Linux user, System Administrator, and DevOps Engineer.
