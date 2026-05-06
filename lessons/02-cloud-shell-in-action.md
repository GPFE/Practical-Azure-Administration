# 🛠️ Lesson 2 — Cloud Shell in Action

> **+100 XP** &nbsp;|&nbsp; ⏱️ ~6 minutes &nbsp;|&nbsp; 🛠️ Practical

---

## 🎯 Learning Goal

By the end of this lesson you will be able to:

- [ ] Open Cloud Shell from the Azure Portal
- [ ] Navigate the CloudDrive
- [ ] Upload, download, and manage files
- [ ] Mount an Azure File Share
- [ ] Run Azure CLI commands to inspect resources

---

## 🧑‍💻 The Scenario

> You are an IT admin on call. You're visiting family — no admin workstation, just a laptop with a browser. Your team reports a VM went non-responsive during maintenance. You need to diagnose and fix it — **right now**.

```
You (laptop + browser)
         │
         │ login to portal.azure.com
         ▼
  Azure Portal  ──>_──►  Cloud Shell
                               │
              ┌────────────────┼────────────────┐
              │                │                │
       CloudDrive       Azure CLI          Diagnostic
       (your files)    (your tools)         Scripts
```

No VPN. No installed tools. Just a browser. Let's go. 🚀

---

## Step 1 — Open Cloud Shell

1. Go to [portal.azure.com](https://portal.azure.com)
2. Sign in with your Azure account
3. Click the **`>_`** icon in the top navigation bar

```
┌──────────────────────────────────────────────────────────────┐
│  Microsoft Azure                    🔔  ?  ⚙️  👤  [>_]     │  ◄── click this
└──────────────────────────────────────────────────────────────┘
```

4. A panel slides up at the bottom of your browser — that's Cloud Shell!
5. Select **Bash** when prompted

> 💡 Alternatively, go straight to [shell.azure.com](https://shell.azure.com)

---

## Step 2 — Get Your Bearings

Once the shell loads, you'll see something like:

```bash
Requesting a Cloud Shell... Succeeded.
Connecting terminal...

Welcome to Azure Cloud Shell

Type "az" to use Azure CLI
Type "help" to learn about Cloud Shell

user@Azure:~$
```

Try these orientation commands:

```bash
# Who am I in Azure?
az account show --output table

# What subscription am I in?
az account list --output table

# Where am I in the filesystem?
pwd
# → /home/user

# What's in my home directory?
ls -la
```

---

## Step 3 — The CloudDrive

Your persistent storage lives in `~/clouddrive`. Anything you save here survives session restarts.

```
~/
├── clouddrive/          ← persists between sessions (Azure File Share)
│   ├── scripts/
│   └── notes.txt
└── (everything else)    ← temporary, gone when session ends
```

```bash
# Navigate to your persistent storage
cd ~/clouddrive

# See what's there
ls -la

# Create a folder for your scripts
mkdir -p scripts
```

---

## Step 4 — Upload a File

Need to get a local file into Cloud Shell?

```
Your Local Machine
      │
      │  Upload via Cloud Shell toolbar
      ▼
┌───────────────────────────────────┐
│  Cloud Shell Toolbar              │
│  [ Upload/Download ] [ ⟳ ] [...] │  ◄── click the up-arrow icon
└───────────────────────────────────┘
      │
      ▼
  ~/clouddrive/  (your uploaded file lands here)
```

**Upload steps:**
1. Click the **⬆️ Upload/Download** button in the Cloud Shell toolbar
2. Select **Upload**
3. Browse to your local file and confirm
4. Your file appears in `~/clouddrive/`

---

## Step 5 — Mount an Azure File Share

A File Share lets you access scripts stored centrally — great for teams.

```bash
# List your storage accounts
az storage account list --output table

# Mount an existing file share (replace placeholders)
clouddrive mount \
  --subscription  "<subscription-id>" \
  --resource-group "<resource-group>" \
  --storage-account "<storage-account-name>" \
  --file-share "<file-share-name>"
```

After mounting, the File Share contents appear inside `~/clouddrive` automatically.

```
Azure Storage
  └── my-file-share/
        ├── diag-scripts/
        │     └── check-vm.sh   ←── accessible right here
        └── templates/
```

---

## Step 6 — Diagnose a VM with Azure CLI

Back to the scenario — let's find and fix that non-responsive VM.

```bash
# List all VMs in the subscription
az vm list --output table

# Check the power state of a specific VM
az vm get-instance-view \
  --resource-group "contoso-rg" \
  --name "contoso-vm01" \
  --query "instanceView.statuses[1]" \
  --output table
```

**Example output:**
```
Code                   DisplayStatus    Level
---------------------  ---------------  -------
PowerState/deallocated  VM deallocated   Info
```

The VM is deallocated (switched off). Start it:

```bash
# Start the VM
az vm start \
  --resource-group "contoso-rg" \
  --name "contoso-vm01"

# Confirm it's running
az vm get-instance-view \
  --resource-group "contoso-rg" \
  --name "contoso-vm01" \
  --query "instanceView.statuses[1].displayStatus" \
  --output tsv
# → VM running ✅
```

---

## Step 7 — Session Lifecycle

```
Open Cloud Shell
      │
      ▼
┌─────────────────────┐
│   Active Session    │◄────── you're here, commands run
└──────────┬──────────┘
           │
           │  20 minutes of inactivity
           ▼
┌─────────────────────┐
│  Session Terminated │  CloudDrive files are SAFE ✅
└──────────┬──────────┘  Temp files are GONE ❌
           │
           │  Open new session
           ▼
┌─────────────────────┐
│   Fresh Session     │◄────── CloudDrive re-mounts automatically
└─────────────────────┘
```

> ⚠️ **Important:** Long-running scripts (> 20 min) will be cut off. Use Azure Automation for those.

---

## 🧠 Recap

| Task | Command / Action |
|------|-----------------|
| Open Cloud Shell | Click `>_` in portal or visit shell.azure.com |
| Go to persistent storage | `cd ~/clouddrive` |
| Upload a file | Toolbar → Upload/Download → Upload |
| Mount a File Share | `clouddrive mount ...` |
| List VMs | `az vm list --output table` |
| Start a VM | `az vm start --resource-group ... --name ...` |

---

## 🏆 Lesson Complete!

```
+100 XP ████████████████████ 100%
```

**Next up →** [Practice Task 1 — Explore & Navigate](03-practice-task-1.md)

---

_← [Back to Course Map](../README.md)_
