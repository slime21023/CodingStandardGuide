# Contributing Guide

本文件定義團隊共同開發流程。語言專屬規範請參考 `docs/languages/`。

## 開發環境

- 專案必須明確標示語言、套件管理器、資料庫與主要框架版本。
- 版本資訊應放入版控，例如 `.nvmrc`、`.python-version`、`package.json`、`pyproject.toml`、`pom.xml` 或 `build.gradle`。
- README 應包含安裝步驟、環境變數、資料庫初始化、測試資料與常見問題。
- 不依賴個人 IDE 設定作為唯一標準；格式化與檢查規則應納入專案設定。

## Branch 命名

格式：

```txt
<type>/<ticket-id>-<short-description>
```

範例：

```txt
feat/PROJ-123-add-login-api
fix/PROJ-456-resolve-payment-error
hotfix/PROJ-789-fix-production-login
docs/PROJ-101-update-setup-guide
```

常用 type：`feat`、`fix`、`hotfix`、`docs`、`test`、`refactor`、`chore`、`ci`、`release`。

## Commit Message

採用 Conventional Commits：

```txt
<type>(<scope>): <subject>
```

範例：

```txt
feat(auth): add login API
fix(order): prevent duplicate payment
docs(readme): update setup guide
test(payment): add refund cases
```

規則：

- 每個 commit 聚焦單一目的。
- subject 使用簡短明確的描述。
- 避免 `update`、`fix bug`、`wip` 等無法判斷內容的訊息。
- 若有對應 ticket，應在 commit、branch 或 PR 中關聯。

## Pull Request

PR 應包含：

- 修改目的與背景。
- 主要變更摘要。
- 驗證方式與結果。
- 影響範圍，例如 API、資料庫、部署、設定或文件。
- 截圖或錄影，若變更包含 UI。

合併前應確認：

- 必要測試與檢查已通過。
- blocking review comments 已處理。
- 文件、設定或部署說明已同步更新。
- PR 範圍合理，避免混入無關重構。

## Code Review

Review 目標是降低風險、提升品質與共享知識。

Comment 分類：

```txt
[blocking] 必須處理，否則不可合併
[suggestion] 建議調整，但不阻擋合併
[question] 需要釐清
[nit] 小問題，不影響合併
```

Review 原則：

- 針對程式碼與設計，不針對個人。
- 意見應具體、可執行，並說明原因。
- 主觀風格問題交由自動化工具處理。
- Author 應主動補充背景、取捨與驗證方式。

## 測試規範

- 修正 bug 時，應補上能重現問題的測試。
- 新功能應至少涵蓋主要成功路徑與重要失敗路徑。
- 測試資料應可重複建立，不依賴個人本機狀態。
- CI 中應執行格式檢查、靜態檢查與必要測試。

## 文件規範

以下情況應同步更新文件：

- 開發流程、部署流程或環境設定改變。
- 新增或替換主要工具、框架、服務。
- API、資料格式、權限或錯誤處理方式改變。
- 修改會影響其他成員操作方式的內容。
