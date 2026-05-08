# 🎯 Practice Task 4 — Read, Predict, and Extend an ARM Template

> ⏱️ ~8 minutes &nbsp;|&nbsp; 🎯 Task

---

## 🧑‍💻 Your Mission

You already deployed a storage account once.  
Now practice reading and extending a template quickly.

---

## ✅ Task Checklist

```
☐  Exercise 1 — Predict what a template does (before deploy)
☐  Exercise 2 — Fill missing fields (tags + output)
☐  Exercise 3 — Validate, what-if, and deploy
☐  Exercise 4 — Verify output and tag values
```

---

## 🧪 Exercise 1 — Predict First

Read this snippet:

```json
"parameters": {
  "storageAccountName": { "type": "string" },
  "location": {
    "type": "string",
    "defaultValue": "[resourceGroup().location]"
  },
  "environmentTag": {
    "type": "string",
    "defaultValue": "lab"
  }
}
```

Write down your prediction:
- Which value is required?
- Which values are optional?
- What value should `environmentTag` become if you pass nothing?

---

## 🧪 Exercise 2 — Fill Missing Fields

Open your `azuredeploy.json` from Practice Task 3 and add the missing parts below.

```json
"tags": {
  "environment": "TODO"
},
"outputs": {
  "storageAccountName": {
    "type": "string",
    "value": "[parameters('storageAccountName')]"
  },
  "storageBlobEndpoint": {
    "type": "string",
    "value": "TODO"
  }
}
```

Guides:
- Tag value should come from `environmentTag` parameter
- Blob endpoint output can be read from ARM `reference(...)` function

---

## 🧪 Exercise 3 — Validate, What-If, Deploy

Run:

1. `az deployment group validate`
2. `az deployment group what-if`
3. `az deployment group create`

Expected what-if behavior:

```text
Either + Create (first run) or ~ Modify (if resource already exists)
```

---

## 🧪 Exercise 4 — Verify

Check:

- Output `storageBlobEndpoint` is returned
- Resource tag `environment` exists and equals `lab` (or your override)

Visual target:

```mermaid
flowchart LR
    A[Template] --> B[Storage Account]
    A --> C[Outputs]
    B --> D[Tag: environment=lab]
    C --> E[storageAccountName]
    C --> F[storageBlobEndpoint]
```

---

## ✅ Done? Check Your Answers

→ [View Solution 4](13-solution-4-arm-template-reading.md)

---

_← [Back to Course Map](../README.md)_
