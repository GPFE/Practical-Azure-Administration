# 🧭 Fix Missing `~/clouddrive` in Cloud Shell

If you see no `~/clouddrive` folder, Cloud Shell is running in **ephemeral mode** ("No storage account required").

In this mode:
- No Azure File Share is mounted
- `~/clouddrive` is unavailable
- Files in `$HOME` are lost when the session ends or times out

## Quick Fix (restore persistent storage)

1. In Cloud Shell, click **⚙️ Settings**
2. Select **Reset user settings**
3. Confirm with **Reset**
4. Wait for Cloud Shell to restart
5. On setup, choose **Mount storage account**

Cloud Shell will mount storage again and restore `~/clouddrive` for persistent files across sessions.

---

_← [Back to Lesson 2](02-cloud-shell-in-action.md)_
