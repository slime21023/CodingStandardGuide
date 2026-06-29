# Release Process

本文件定義團隊發版流程與 CalVer 版本規則。

## 版本規則

正式版本採 CalVer：

```txt
YYYY.MM.DD.N
```

規則：

- `YYYY.MM.DD` 為發版日期。
- `N` 為當日第幾次正式發版，從 `1` 開始。
- 同日 hotfix 使用相同日期並遞增 `N`。
- Git tag 使用 `vYYYY.MM.DD.N`。

範例：

```txt
2026.06.29.1
2026.06.29.2
v2026.06.29.1
```

## 發版前檢查

發版前應確認：

- 目標分支已合併所有預期變更。
- CI 必要檢查已通過。
- migration、環境變數、排程或外部服務變更已確認。
- Release note 已記錄主要變更、影響範圍與部署注意事項。
- 已確認回滾方式與負責人。

## Release Note

每次發版應至少包含：

- 版本號與發版日期。
- 新增功能。
- 修正問題。
- 破壞性變更或相容性注意事項。
- 部署步驟與回滾方式。

建議格式：

```markdown
# Release v2026.06.29.1

## Changes

- feat: add login API
- fix: prevent duplicate payment

## Deployment Notes

- Run database migration before deployment.

## Rollback

- Redeploy previous stable tag.
```

## 部署與回滾

- 部署應使用明確版本或 tag，不使用未固定的分支名稱。
- 部署完成後應確認服務健康狀態、錯誤率與關鍵流程。
- 若發現重大問題，應依事前定義的方式回滾至上一個穩定版本。
- 回滾後仍需建立修復任務，避免只以回滾作為最終處理。

## Hotfix

- hotfix 應只包含修復正式環境問題所需的最小變更。
- hotfix 仍需通過必要測試與 review。
- 同日多次 hotfix 依 CalVer 的 `N` 遞增。
- hotfix 合併後應同步回主要開發分支，避免修復遺失。
