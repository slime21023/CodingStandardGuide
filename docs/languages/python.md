# Python Guide

適用於 Python 應用程式、服務與工具專案。

## 環境與套件

- 專案應固定 Python 版本，並寫入 `.python-version`、`pyproject.toml` 或 README。
- 建議使用 `uv` 管理環境與依賴；若專案使用其他工具，應在 README 說明。
- lockfile 若由專案工具產生，應納入版控。
- 不提交本機虛擬環境目錄，例如 `.venv/`。

## 格式與檢查

- 使用 Ruff 或 Pyrefly 作為 linter；若專案同時使用兩者，應在 README 說明各自負責的檢查範圍。
- Python 格式化建議使用 Ruff format，或依專案既有 formatter 設定執行。
- 工具設定應放在 `pyproject.toml`。
- CI 應執行 lint、format check、type check 與測試。
- 可自動修正的格式問題，應使用工具修正。

## 型別與命名

- 對外函式、共用模組、複雜資料結構應加上型別註記。
- 變數、函式、模組使用 `snake_case`。
- 類別使用 `PascalCase`。
- 常數使用 `UPPER_SNAKE_CASE`。
- 避免以過度簡短的名稱降低可讀性，迴圈索引等明確情境除外。

## 程式設計原則

- 函式應保持單一責任，避免同時處理 I/O、商業邏輯與格式轉換。
- 對外部輸入應明確驗證，不假設資料一定正確。
- 避免使用 mutable default arguments。
- 例外處理應精準捕捉，不使用裸 `except`。
- 不在函式中隱性修改全域狀態，除非該行為是明確設計。

## 測試

- 建議使用 pytest。
- 測試名稱應描述預期行為。
- bug fix 應新增回歸測試。
- 測試資料應由 fixture 或 factory 建立，避免依賴本機狀態。
- 外部服務呼叫應使用 mock、stub 或測試環境隔離。
