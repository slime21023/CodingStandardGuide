# Go Guide

適用於 Go 服務、CLI、背景工作與共用函式庫。

## 環境與套件

- 專案應固定 Go 版本，並在 `go.mod` 或 README 中標示。
- dependency 應透過 Go modules 管理，`go.mod` 與 `go.sum` 必須納入版控。
- README 應說明建置、測試、本機執行與必要環境變數。
- 新增 dependency 前應確認用途、維護狀態、授權與標準函式庫是否已能滿足需求。
- 不提交本機產物，例如 binary、coverage report 或暫存檔。

## 格式與檢查

- 所有 Go 程式碼應通過 `gofmt` 或 `go fmt`。
- import 應由 `goimports` 或等效工具整理。
- CI 應執行 format check、`go test ./...` 與必要的 static analysis。
- 建議使用 `go vet` 與 `staticcheck` 檢查常見錯誤。
- 格式化與檢查規則應由專案工具設定控制，不依賴個人 IDE。

## 命名與結構

- package 名稱使用小寫、簡短且具語意的名稱，避免底線與過度縮寫。
- exported identifier 必須有清楚註解，註解應以 identifier 名稱開頭。
- 變數與函式使用 `camelCase`；exported type、function、constant 使用 `PascalCase`。
- interface 應優先定義在消費端，避免為了 mock 或抽象而提前建立大型 interface。
- package 應依職責切分，避免建立語意模糊的 `common`、`utils` 或 `helpers`。

## 錯誤與 Context

- 錯誤應明確處理，不使用 `_` 忽略重要錯誤。
- 回傳錯誤時應保留上下文，可使用 `%w` 包裝原始錯誤。
- 對外 API 邊界應轉換錯誤訊息，避免暴露敏感資訊或內部實作細節。
- 需要取消、逾時或跨服務追蹤的流程應傳遞 `context.Context`。
- `context.Context` 應作為函式第一個參數，且不應存入 struct 欄位。

## Concurrency

- goroutine 的生命週期應明確，避免產生無法停止或無人接收結果的 goroutine。
- channel 應用於協調與資料流，不作為全域共享狀態的替代品。
- shared state 應使用 `sync`、channel 或其他明確同步機制保護。
- 涉及 concurrency 的程式碼應考慮 cancellation、timeout、錯誤回傳與資源釋放。
- 需要檢查 data race 的情境應執行 `go test -race`。

## 測試

- 單元測試使用標準 `testing` package，必要時搭配專案既有 assertion 工具。
- 測試名稱應描述情境與預期行為。
- table-driven test 適用於多組輸入輸出，但測試案例名稱應清楚。
- bug fix 應新增回歸測試。
- 測試不應依賴執行順序、系統時間、本機檔案或外部服務狀態。
