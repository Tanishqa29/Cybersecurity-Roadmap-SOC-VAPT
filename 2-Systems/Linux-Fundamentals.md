# 🐧 1. LINUX FUNDAMENTALS (Detailed + Commands)

---

## 📂 File & Directory Commands

| Command | Use                                |
|--------|------------------------------------|
| `ls`    | List files                         |
| `ls -l` | Detailed list (permissions, owner) |
| `ls -a` | Hidden files                       |
| `cd`    | Change directory                   |
| `pwd`   | Current path                       |
| `mkdir` | Create directory                   |
| `rmdir` | Delete empty directory             |

---

## 📄 File Handling

| Command            | Use                 |
|--------------------|---------------------|
| `touch file.txt`   | Create file         |
| `cp a.txt b.txt`   | Copy file           |
| `mv a.txt b.txt`   | Move/rename         |
| `rm file.txt`      | Delete file         |
| `rm -rf dir` ⚠️    | Force delete folder |

---

## 👁️ File Viewing

| Command              | Use                       |
|----------------------|---------------------------|
| `cat`                | View file                 |
| `less`               | Scroll view               |
| `head -n 5`          | First 5 lines             |
| `tail -n 5`          | Last 5 lines              |
| `tail -f log.txt` 🔥 | Live logs (SOC important) |

---

## 🔍 Search & Filtering

| Command                   | Use         |
|---------------------------|-------------|
| `grep "error" file.txt`   | Search text |
| `find / -name file.txt`   | Find file   |
| `locate file.txt`         | Fast search |

---

## 👤 Users & Permissions (VERY IMPORTANT 🔥)

### 👉 Check permissions

```bash
ls -l
