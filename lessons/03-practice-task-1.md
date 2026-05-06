# 🎯 Practice Task 1 — Explore & Navigate Cloud Shell

> **+200 XP** &nbsp;|&nbsp; ⏱️ ~5 minutes &nbsp;|&nbsp; 🎯 Task

---

## 🧑‍💻 Your Mission

You've just landed in Cloud Shell for the first time.  
Complete the tasks below **without peeking at the solution**!

---

## 📋 Task Checklist

```
☐  Task 1 — Open Cloud Shell
☐  Task 2 — Identify your Azure account and subscription
☐  Task 3 — Explore the CloudDrive
☐  Task 4 — Create a folder and a file
☐  Task 5 — Verify persistence
```

---

## 📝 Task Details

### Task 1 — Open Cloud Shell

Open Azure Cloud Shell using **any** of the three methods you learned:

```
Method A: https://shell.azure.com
Method B: Azure Portal → click the >_ icon in the top bar
Method C: Microsoft Learn → click "Try it" in a code snippet
```

Select **Bash** as your shell when prompted.

---

### Task 2 — Identify Your Account and Subscription

Run the commands needed to answer these questions:

```
❓ What is your Azure account email / username?
❓ What is the name of your active subscription?
❓ What is the subscription ID?
```

> 💡 Hint: `az account` is your friend here.

---

### Task 3 — Explore the CloudDrive

Answer these questions by exploring the filesystem:

```
❓ What is the full path of the CloudDrive mount point?
❓ What files and folders already exist inside it?
❓ How much space is available? (hint: try `df -h`)
```

---

### Task 4 — Create a Folder and a File

Inside your CloudDrive, create the following structure:

```
~/clouddrive/
└── myadmin/
    └── hello.txt    ← containing the text "Hello, Cloud Shell!"
```

Use only shell commands — no file uploads!

---

### Task 5 — Verify Persistence

1. **Close** your Cloud Shell session (click the ✕ button)
2. Wait 10 seconds
3. **Open** a brand-new Cloud Shell session
4. Navigate to `~/clouddrive/myadmin/` and confirm `hello.txt` is still there
5. Print its contents

```
Expected output:
Hello, Cloud Shell!
```

---

## 💡 Tips

- Stuck on Task 2? Run `az --help` or `az account --help`
- Stuck on Task 4? You need `mkdir` and either `echo` or a text editor
- Remember: everything **outside** `~/clouddrive` is temporary!

---

## ✅ Done? Check Your Answers

→ [View Solution 1](04-solution-1.md)

---

_← [Back to Course Map](../README.md)_
