# ✅ Solution 1 — Explore & Navigate Cloud Shell

> **Review your answers below. No shame in checking — that's how we learn!**

---

## Task 1 — Open Cloud Shell ✅

Any of these methods work:

| Method | Steps |
|--------|-------|
| Direct link | Go to [https://shell.azure.com](https://shell.azure.com) and sign in |
| Azure Portal | Sign in → click the **`>_`** icon in the top navigation bar |
| Microsoft Learn | Open any Learn module → click **"Try it"** next to a code block |

Select **Bash** when prompted for the shell experience.

---

## Task 2 — Identify Your Account and Subscription ✅

```bash
# Show the currently signed-in account
az account show --output table
```

**Example output:**
```
EnvironmentName    HomeTenantId    IsDefault    Name                    State    TenantId
-----------------  --------------  -----------  ----------------------  -------  ----------
AzureCloud         xxxxxxxx-...    True         My Azure Subscription   Enabled  xxxxxxxx-...
```

```bash
# List all subscriptions (useful if you have more than one)
az account list --output table
```

Your **account email** appears in the `user.name` field when you run:
```bash
az account show --query "user.name" --output tsv
```

---

## Task 3 — Explore the CloudDrive ✅

```bash
# Full path of the CloudDrive
echo $HOME/clouddrive
# → /home/<username>/clouddrive

# What's inside?
ls -la ~/clouddrive

# How much space is available?
df -h ~/clouddrive
```

**Example `df` output:**
```
Filesystem      Size  Used Avail Use% Mounted on
//storage...   5.0G  1.2G  3.8G  24% /home/user/clouddrive
```

> 💡 The CloudDrive is backed by an Azure File Share (5 GB by default on a free account).

---

## Task 4 — Create a Folder and a File ✅

```bash
# Create the folder
mkdir -p ~/clouddrive/myadmin

# Create the file with the required content
echo "Hello, Cloud Shell!" > ~/clouddrive/myadmin/hello.txt

# Verify the file was created
cat ~/clouddrive/myadmin/hello.txt
# → Hello, Cloud Shell!
```

**Resulting structure:**
```
~/clouddrive/
└── myadmin/
    └── hello.txt
```

---

## Task 5 — Verify Persistence ✅

After closing and reopening Cloud Shell:

```bash
# Navigate to the folder
cd ~/clouddrive/myadmin

# Confirm the file exists
ls -la
# → hello.txt

# Print its contents
cat hello.txt
# → Hello, Cloud Shell!
```

**What happened behind the scenes:**

```
Session 1 ends
      │
      │  Files in ~/clouddrive written to Azure File Share ✅
      ▼
Session 2 starts
      │
      │  Azure File Share re-mounted automatically at ~/clouddrive ✅
      ▼
cat hello.txt → "Hello, Cloud Shell!"
```

> ✅ **Key takeaway:** The CloudDrive persists because it is an Azure File Share, not local VM storage.

---

## 🏆 Progress Check

| Task | Status |
|------|--------|
| Task 1 — Opened Cloud Shell | ✅ Done |
| Task 2 — Identified account & subscription | ✅ Done |
| Task 3 — Explored CloudDrive | ✅ Done |
| Task 4 — Created folder & file | ✅ Done |
| Task 5 — Verified persistence | ✅ Done |
| **All tasks completed** | **🎉 Excellent work!** |

---

## ⏭️ Ready for the Next Challenge?

**Next up →** [Practice Task 2 — Code Editor & Scripts](05-practice-task-2.md)

---

_← [Back to Course Map](../README.md)_
