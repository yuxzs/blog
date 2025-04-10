---
title: TRON Transaction Fee Calculation
date: 2025-04-10 11:41:57
tags:
---

# 虛擬貨幣轉帳手續費計算（TRON Transaction Fee Calculation）

在 TRON 區塊鏈上進行轉帳，不論是 TRX 還是 USDT，轉帳時都會產生手續費。這些費用主要透過「寬頻（Bandwidth）」與「能量（Energy）」來支付，若資源不足，則會額外扣除 TRX 作為補充費用，因此了解手續費的計算方式相當重要。

## TRON 手續費計價方式
| 資源類型 | TRX 換算比例 |
|---------|--------------|
| Bandwidth | 1 Bandwidth = 0.001 TRX |
| Energy    | 1 Energy = 0.00021 TRX |

---

## TRX 轉帳資源消耗
- Bandwidth：265
- Energy：0

---

## USDT 轉帳資源消耗
| 狀態 | Bandwidth | Energy |
|------|-----------|--------|
| 對方錢包已有 USDT | 345 | 64,285 |
| 對方錢包沒有 USDT | 345 | 130,285 |

---

## 免費 Bandwidth 說明
每個 TRON 錢包每天都會免費獲得 600 Bandwidth，並且會隨時間自動回復。用戶可透過 [TronScan](https://tronscan.org/) 查詢當前剩餘的 Bandwidth 與 Energy 數量。

---

## 小提醒
若 Bandwidth 或 Energy 不足，系統會直接扣除 TRX 作為手續費。因此，建議在進行大額或頻繁轉帳前，先評估資源使用狀況，能有效節省 TRX，降低轉帳成本。
