# Kotlin Guide

適用於 Kotlin 後端、Android 與共用函式庫。

## 環境與建置

- 專案應固定 Kotlin、JDK 與 Gradle 版本。
- 使用 Gradle wrapper，並將 wrapper 檔案納入版控。
- dependency 版本應集中管理，例如 version catalog。
- README 應說明建置、測試與本機執行方式。

## 格式與檢查

- 格式化與 lint 規則應納入專案設定。
- CI 應執行 compile、lint、test 與必要的 static analysis。
- import、縮排、換行與尾逗號規則交由工具處理。
- 不依賴個人 IDE 設定作為唯一標準。

## Null Safety

- 優先使用 Kotlin 型別系統表達 nullability。
- 避免使用 `!!`；必要時應能清楚證明不會為 null。
- Java interop 的 platform type 應在邊界處轉為明確 nullable 或 non-null 型別。
- 對外輸入應先驗證，再進入核心邏輯。

## Coroutine

- suspend function 應保持語意清楚，不隱藏阻塞 I/O。
- 避免在 coroutine 中執行未切換 dispatcher 的阻塞操作。
- 不使用全域 coroutine scope 處理需要生命週期管理的工作。
- 錯誤處理與 cancellation 行為應明確。

## 命名與結構

- class、interface、object、type 使用 `PascalCase`。
- function、property、local variable 使用 `camelCase`。
- constant 使用 `UPPER_SNAKE_CASE`.
- extension function 應放在語意清楚的模組中，避免建立難以追蹤的隱性行為。
- data class 應用於資料承載，不承擔複雜商業邏輯。

## 測試

- 單元測試應涵蓋核心邏輯與錯誤路徑。
- coroutine 測試應使用適合的 test dispatcher。
- bug fix 應新增回歸測試。
- 測試資料應可重複建立，不依賴本機狀態。
