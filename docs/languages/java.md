# Java Guide

適用於 Java 服務、應用程式與共用函式庫。

## 環境與建置

- 專案應固定 Java 版本，並在 README、`pom.xml` 或 `build.gradle` 中標示。
- 同一專案應明確採用 Maven 或 Gradle，不混用建置流程。
- wrapper 檔案應納入版控，例如 `mvnw` 或 `gradlew`。
- dependency 版本應集中管理，避免散落在多個模組中。

## 格式與檢查

- 格式化與靜態檢查規則應納入專案設定。
- CI 應執行 compile、test 與必要的 static analysis。
- import 順序、縮排與換行規則交由工具處理。
- 不以個人 IDE 設定作為團隊唯一標準。

## 命名與結構

- class、interface、enum 使用 `PascalCase`。
- method、field、local variable 使用 `camelCase`。
- constant 使用 `UPPER_SNAKE_CASE`.
- package 使用小寫，避免縮寫造成語意不清。
- 分層責任應明確，例如 controller、service、repository、domain。

## 例外與資料處理

- 不捕捉後忽略例外。
- 例外訊息應提供足夠排查資訊，但不得包含敏感資料。
- 對外 API 邊界應驗證輸入。
- 避免直接回傳或暴露可變內部集合。
- null 處理應明確，必要時使用 `Optional` 表示可能不存在的結果。

## 測試

- 單元測試應聚焦商業邏輯。
- 整合測試應涵蓋資料庫、外部服務或框架整合的重要路徑。
- bug fix 應新增回歸測試。
- 測試不應依賴執行順序。
- 測試資料應可重複建立與清理。
