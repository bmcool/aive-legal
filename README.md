# AIve Legal

公開的法律文件靜態頁面（隱私政策等），透過 GitHub Pages 部署。

## 結構

```
aive-legal/
├── index.html          自動跳轉到 privacy-policy.html
├── privacy-policy.html 隱私權政策（自帶 CSS）
└── README.md
```

## 部署

GitHub Settings → Pages → Source: `Deploy from a branch` → Branch: `main` / `(root)`

部署後 URL：`https://<github-username>.github.io/aive-legal/privacy-policy.html`

此 URL 填入 Play Console「應用程式內容 → 隱私權政策」欄位。

## 維護

源頭是 `AIve-App/apps/aive_flutter/store/privacy-policy.md`，修改流程：

1. 編輯 `store/privacy-policy.md`（含「最後更新日期」）
2. `pandoc store/privacy-policy.md -o /tmp/_body.html` 產 body fragment
3. 重新 wrap 成 HTML（用 Claude 跑或自己手動），覆寫 `store/legal/privacy-policy.html`
4. 把更新後的 HTML 複製到此 repo，commit + push
