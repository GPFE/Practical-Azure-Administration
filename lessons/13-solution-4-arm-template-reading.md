# ✅ Solution 4 — Read, Predict, and Extend an ARM Template

> **Review your answers below.**

---

## 🧭 How to Use This Solution

Use this page to check your reasoning, not just your final output.

When comparing:
1. Check whether your predictions about required/optional parameters were correct
2. Confirm your expressions for `tags` and `outputs` match ARM syntax
3. Verify your command sequence stayed safe (`validate` → `what-if` → `create`)

---

## Exercise 1 — Prediction ✅

From the snippet:

- Required: `storageAccountName` (no default)
- Optional: `location` and `environmentTag` (both have defaults)
- `environmentTag` default: `lab`

---

## Exercise 2 — Filled Fields ✅

Updated resource + outputs:

```json
"tags": {
  "environment": "[parameters('environmentTag')]"
},
"outputs": {
  "storageAccountName": {
    "type": "string",
    "value": "[parameters('storageAccountName')]"
  },
  "storageBlobEndpoint": {
    "type": "string",
    "value": "[reference(resourceId('Microsoft.Storage/storageAccounts', parameters('storageAccountName'))).primaryEndpoints.blob]"
  }
}
```

---

## Exercise 3 — Validate, What-If, Deploy ✅

```bash
az deployment group validate \
  --resource-group rg-iac-lab \
  --template-file azuredeploy.json \
  --parameters @azuredeploy.parameters.json \
  --parameters environmentTag=lab

az deployment group what-if \
  --resource-group rg-iac-lab \
  --template-file azuredeploy.json \
  --parameters @azuredeploy.parameters.json \
  --parameters environmentTag=lab

az deployment group create \
  --name deploy-storage-iac-tags \
  --resource-group rg-iac-lab \
  --template-file azuredeploy.json \
  --parameters @azuredeploy.parameters.json \
  --parameters environmentTag=lab
```

---

## Exercise 4 — Verify ✅

```bash
az deployment group show \
  --name deploy-storage-iac-tags \
  --resource-group rg-iac-lab \
  --query "properties.outputs" \
  --output jsonc

az storage account show \
  --name stiaclab001xyz \
  --resource-group rg-iac-lab \
  --query "tags" \
  --output jsonc
```

Expected:
- outputs contain `storageAccountName` and `storageBlobEndpoint`
- tags include `"environment": "lab"` (or your override)

---

## 🏆 Progress Check

| Task | Status |
|------|--------|
| Exercise 1 — Predict behavior | ✅ Done |
| Exercise 2 — Fill missing fields | ✅ Done |
| Exercise 3 — Validate/what-if/deploy | ✅ Done |
| Exercise 4 — Verify outputs and tags | ✅ Done |
| **All exercises completed** | **🎉 Excellent work!** |

---

**→ [Back to Course Map](../README.md)**
