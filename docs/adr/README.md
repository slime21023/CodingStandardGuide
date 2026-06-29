# Architecture Decision Records

ADR 用於記錄重要技術決策，讓團隊日後能理解背景、取捨與影響。

## 使用時機

以下情況應建立 ADR：

- 選擇主要技術方案或框架。
- 修改部署架構或資料儲存方式。
- 引入重大工具、平台或外部服務。
- 做出難以回復或長期影響維護成本的決策。
- 團隊曾討論多個方案，且需要留下取捨原因。

## 命名規則

```txt
docs/adr/0001-decision-title.md
```

規則：

- 編號使用四位數遞增。
- 檔名使用英文 kebab-case。
- 標題應清楚描述決策內容。

## 狀態

常用狀態：

- `Proposed`：提出中，尚未採納。
- `Accepted`：已採納。
- `Deprecated`：不再建議使用。
- `Superseded`：已被新的 ADR 取代。

## 範本

```markdown
# ADR 0001: Decision Title

## Status

Proposed / Accepted / Deprecated / Superseded

## Context

說明背景、問題與限制。

## Decision

說明最終決策。

## Consequences

說明影響、取捨與後續注意事項。

## Alternatives Considered

列出曾考慮但未採用的方案。
```
