# Coding Standard Guide

本指南提供團隊一致遵守的開發規範，目標是降低溝通成本、提升程式碼品質、減少部署風險，並協助新成員快速進入專案。

## 文件導覽

| 文件 | 用途 |
|---|---|
| [CONTRIBUTING.md](CONTRIBUTING.md) | 團隊共同開發流程、Git、Commit、PR、Review、測試與文件規範 |
| [JavaScript / TypeScript](docs/languages/javascript-typescript.md) | Node.js、Bun、ESLint、型別與測試規範 |
| [Python](docs/languages/python.md) | Python、Ruff、型別註記、虛擬環境與測試規範 |
| [Go](docs/languages/go.md) | Go modules、gofmt、錯誤處理、Context、Concurrency 與測試規範 |
| [Java](docs/languages/java.md) | Java、Maven / Gradle、例外處理、測試與分層規範 |
| [Kotlin](docs/languages/kotlin.md) | Kotlin、Gradle、Null Safety、Coroutine 與測試規範 |
| [Release Process](docs/release-process.md) | CalVer 版本規則、發版檢查與回滾原則 |
| [ADR](docs/adr/README.md) | 技術決策紀錄的使用方式與範本 |

## 使用原則

- 新專案應先閱讀 `CONTRIBUTING.md`，再依技術棧閱讀對應語言規範。
- 專案若已有工具設定檔，實際檢查規則以設定檔為準。
- 規範應保持簡短、可執行，避免只描述抽象原則。
- 若規範不符合實際開發情境，應提出調整並更新文件。

## 維護方式

- 新增語言時，在 `docs/languages/` 新增對應文件，並更新本頁導覽。
- 修改開發流程、部署流程、工具版本或重要設計決策時，應同步更新相關文件。
- 重要且長期影響架構的決策，應使用 ADR 留存背景、取捨與結果。
