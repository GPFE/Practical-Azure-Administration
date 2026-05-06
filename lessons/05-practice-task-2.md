# 🎯 Practice Task 2 — Code Editor & Saving Scripts

> **+200 XP** &nbsp;|&nbsp; ⏱️ ~5 minutes &nbsp;|&nbsp; 🎯 Task

---

## 🧑‍💻 Your Mission

In a real Azure admin scenario you'll often need to write, edit, and save reusable scripts directly in Cloud Shell — no need for a local IDE.

In this task you'll practice exactly that using the **built-in Cloud Shell code editor**.

---

## 📋 Task Checklist

```
☐  Task 1 — Open the Cloud Shell editor
☐  Task 2 — Write a Bash script
☐  Task 3 — Save the script to your CloudDrive
☐  Task 4 — Close the editor and run the script
☐  Task 5 — Edit the script and verify the change persists
```

---

## 📝 Task Details

### Task 1 — Open the Cloud Shell Editor

There are two ways to open the editor. Try both and pick the one you prefer:

**Method A — Toolbar icon:**
```
Cloud Shell toolbar  →  click the { } icon
```

**Method B — Command:**
```bash
code ~/clouddrive/myadmin/hello.txt
```

> ⚠️ **Note:** The `code` command only works in **Classic mode**.  
> To enable it: click the **`...`** (More) icon → **Settings** → **Go to Classic version**.

---

### Task 2 — Write a Bash Script

Using the editor, create a new file at:

```
~/clouddrive/myadmin/vm-status.sh
```

The script should:
1. Print a header line: `=== VM Status Report ===`
2. List all VMs in the subscription along with their power state
3. Print a footer line: `=== End of Report ===`

> 💡 Hint: You'll need `az vm list` and its `--show-details` flag.

---

### Task 3 — Save the Script

Save the file from within the editor.

```
Editor shortcut: Ctrl + S  (or  Cmd + S  on Mac)
```

Confirm the file was saved by checking it exists:

```bash
ls -la ~/clouddrive/myadmin/
```

---

### Task 4 — Close the Editor and Run the Script

1. Close the editor (click the **✕** on the editor panel, or press `Ctrl+Q`)
2. Make the script executable
3. Run it

```
Expected output:
=== VM Status Report ===
[...list of VMs and their power states...]
=== End of Report ===
```

> 💡 Hint: You need `chmod` before the script will run.

---

### Task 5 — Edit the Script and Verify Persistence

1. Re-open `vm-status.sh` in the editor
2. Add a second line to the header section that prints today's date and time
3. Save the file
4. Close the editor and run the script again

Verify your change is reflected in the output.

```
Expected output:
=== VM Status Report ===
Report generated: Wed May  7 10:32:00 UTC 2025
[...list of VMs and their power states...]
=== End of Report ===
```

---

## 💡 Tips

- The editor supports syntax highlighting for `.sh`, `.py`, `.json`, and more
- Use `Ctrl+S` to save, `Ctrl+Q` or the ✕ button to close
- You can also edit files directly in the terminal with `nano filename` or `vim filename`
- Remember: save to `~/clouddrive/` so the script survives session restarts!

---

## ✅ Done? Check Your Answers

→ [View Solution 2](06-solution-2.md)

---

_← [Back to Course Map](../README.md)_
