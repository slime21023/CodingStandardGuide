# JavaScript / TypeScript Guide

適用於 Node.js、Bun、前端與後端 TypeScript 專案。

## 環境與套件

- 專案應固定 Node.js 或 Bun 版本，並寫入 `.nvmrc`、`package.json` 或 README。
- 同一專案只使用一種主要 package manager，例如 npm、pnpm、yarn 或 bun。
- lockfile 必須納入版控，避免依賴版本漂移。
- 新增 dependency 前應確認用途、維護狀態與替代方案。

## 格式與檢查

- 使用 ESLint 作為靜態檢查工具。
- 格式化規則應由專案設定檔控制，不依賴個人 IDE。
- CI 應執行 lint、typecheck 與測試。
- 可自動修正的格式問題，應使用工具修正。

## TypeScript

- 優先使用 TypeScript；避免在新程式碼中使用未型別化的 JavaScript。
- 避免使用 `any`；必要時應限縮範圍並說明原因。
- 對外 API、共用函式、資料模型應明確定義型別。
- 使用 `unknown` 處理不可信輸入，驗證後再轉為具體型別。
- 避免以 type assertion 掩蓋型別問題。

## 命名與結構

- 檔案命名採專案既有慣例，常見為 `kebab-case` 或 `camelCase`。
- 變數與函式使用 `camelCase`。
- 類別、React component、type、interface 使用 `PascalCase`。
- 常數可使用 `UPPER_SNAKE_CASE`，但只用於真正固定不變的值。
- 模組應維持單一責任，避免大型共用工具檔持續膨脹。

## 錯誤處理

- 不吞掉錯誤；catch 後應處理、轉換或重新拋出。
- 對外錯誤訊息應避免暴露敏感資訊。
- 非同步流程必須處理 rejected promise。
- API 邊界應驗證輸入資料。

## 測試

- 新功能應補上單元測試或整合測試。
- bug fix 應包含能重現問題的測試。
- 測試名稱應描述行為，而不是實作細節。
- 避免依賴測試執行順序或共享可變狀態。
