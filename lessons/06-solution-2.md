# ✅ Solution 2 — Code Editor & Saving Scripts

> **Review your answers below.**

---

## Task 1 — Open the Cloud Shell Editor ✅

**Method A — Toolbar icon:**

```
Cloud Shell toolbar  →  click the { } curly-braces icon
```

**Method B — Command (Classic mode required):**

```bash
# Open an existing file
code ~/clouddrive/myadmin/hello.txt

# Open a new file
code ~/clouddrive/myadmin/vm-status.sh
```

> ⚠️ If `code` gives an error, switch to Classic mode:  
> **`...`** (More) → **Settings** → **Go to Classic version**

The editor opens as an overlay panel inside your browser:

```
┌────────────────────────────────────────────────────────────┐
│  vm-status.sh                                    [ ✕ ]    │
├────────────────────────────────────────────────────────────┤
│  1  #!/bin/bash                                            │
│  2                                                         │
│  3  echo "=== VM Status Report ==="                        │
│  4  az vm list --show-details \                            │
│  5    --query "[].{Name:name, State:powerState}" \         │
│  6    --output table                                       │
│  7  echo "=== End of Report ==="                           │
│                                                            │
│  Ctrl+S Save  │  Ctrl+Q Close                             │
└────────────────────────────────────────────────────────────┘
```

---

## Task 2 — Write the Bash Script ✅

The complete script:

```bash
#!/bin/bash

echo "=== VM Status Report ==="
az vm list --show-details \
  --query "[].{Name:name, State:powerState}" \
  --output table
echo "=== End of Report ==="
```

Type (or paste) this into the editor for the file `~/clouddrive/myadmin/vm-status.sh`.

---

## Task 3 — Save the Script ✅

Inside the editor, press:

```
Ctrl + S   (Windows / Linux)
Cmd  + S   (macOS)
```

Confirm from the terminal:

```bash
ls -la ~/clouddrive/myadmin/
```

**Expected output:**
```
total 8
drwxr-xr-x 2 user user  0 May  7 10:30 .
drwxr-xr-x 3 user user  0 May  7 10:15 ..
-rw-r--r-- 1 user user 20 May  7 10:20 hello.txt
-rw-r--r-- 1 user user 98 May  7 10:30 vm-status.sh   ✅
```

---

## Task 4 — Close Editor and Run the Script ✅

```bash
# Make it executable
chmod +x ~/clouddrive/myadmin/vm-status.sh

# Run it
~/clouddrive/myadmin/vm-status.sh
```

**Example output:**
```
=== VM Status Report ===
Name           State
-------------  --------------
contoso-vm01   VM running
contoso-vm02   VM deallocated
contoso-web01  VM running
=== End of Report ===
```

> 💡 If you have no VMs, the table will be empty — that's fine! The script still runs correctly.

---

## Task 5 — Edit the Script and Verify Persistence ✅

Re-open the editor:

```bash
code ~/clouddrive/myadmin/vm-status.sh
```

Updated script (add the `date` line):

```bash
#!/bin/bash

echo "=== VM Status Report ==="
echo "Report generated: $(date)"
az vm list --show-details \
  --query "[].{Name:name, State:powerState}" \
  --output table
echo "=== End of Report ==="
```

Save with `Ctrl+S`, close the editor, then run:

```bash
~/clouddrive/myadmin/vm-status.sh
```

**Expected output:**
```
=== VM Status Report ===
Report generated: Wed May  7 10:32:00 UTC 2025
Name           State
-------------  --------------
contoso-vm01   VM running
contoso-vm02   VM deallocated
contoso-web01  VM running
=== End of Report ===
```

---

## 🔑 The Big Picture

```
Write script in editor
        │
        │  Ctrl+S
        ▼
Saved to ~/clouddrive/  ──► backed by Azure File Share
        │
        │  chmod +x
        ▼
Execute from terminal
        │
        │  re-open with: code filename
        ▼
Edit & save again ──► changes persist immediately
```

> ✅ **Key takeaway:** The Cloud Shell editor lets you create and maintain scripts directly in your browser, stored persistently on your CloudDrive. No local IDE, no syncing — just open Cloud Shell from anywhere and your scripts are ready.

---

## 🏆 Score Check

| Task | Points |
|------|--------|
| Task 1 — Opened the Cloud Shell editor | ✅ +40 XP |
| Task 2 — Wrote a Bash script | ✅ +40 XP |
| Task 3 — Saved to CloudDrive | ✅ +40 XP |
| Task 4 — Made executable and ran | ✅ +40 XP |
| Task 5 — Edited and verified persistence | ✅ +40 XP |
| **Total** | **+200 XP** |

---

## 🎉 Module Complete!

```
Azure Cloud Shell module
████████████████████ 100%   +800 XP total

 🏅 Achievement Unlocked: Cloud Shell Rookie
```

You can now:
- ✅ Open Cloud Shell from anywhere
- ✅ Navigate and use the CloudDrive
- ✅ Run Azure CLI commands
- ✅ Create and edit scripts with the code editor
- ✅ Persist your work across sessions

---

**→ [Back to Course Map](../README.md)**

---

_More modules coming soon!_
