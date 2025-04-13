---
title: Using John the Ripper and Hashcat to Process RAR Files
date: 2025-04-13 15:10:07
tags:
    - John the Ripper
    - Hashcat
    - RAR
    - 密碼破解
    - 教學
---

# 一、必要工具與前置準備

## 1.1. 安裝 John the Ripper

- 下載並安裝 John the Ripper（建議使用社群版 Jumbo，它已包含支援多種加密格式的工具，例如 `rar2john`）。
- 確認在命令行中 `john` 與 `rar2john` 指令可正常執行。

## 1.2. 安裝 Hashcat

- 下載並安裝 Hashcat（建議使用支援 GPU 加速的版本，可大幅提升破解速度）。
- 準備一份適用的字典檔，例如常見的 wordlist，或考慮使用 Hashcat 的規則、暴力破解等攻擊模式。

# 二、使用 John the Ripper 處理 RAR 檔案

## 2.1. 從 RAR 檔案提取 Hash

RAR 檔案中的密碼資訊需要先轉換成可供破解程式識別的 Hash 格式。John the Ripper 附帶的 `rar2john` 工具可以完成此工作：

```bash
rar2john archive.rar > archive.hash
```

## 2.2 利用 John 進行破解
使用 John the Ripper 來嘗試破解 Hash，基本指令如下：

```bash
john archive.hash
```
破解完成後，可以使用以下指令來顯示破解結果：

```bash
john --show archive.hash
```
若需要指定自定義字典檔，請使用 --wordlist 參數：

```bash
john --wordlist=your_wordlist.txt archive.hash
```
破解成效取決於密碼的複雜性及字典檔案的品質。

## 2.3 執行 Hashcat 破解
針對 RAR3 格式的壓縮檔，Hashcat 使用模式 -m 23800：
- 若處理其他舊版 RAR 格式，請參照 Hashcat 官方文件確認對應的模式。

```bash
hashcat -m 23800 archive.hash your_wordlist.txt

hashcat -m 23800 -a 3 archive.hash

hashcat -m 23800 -a 3 archive.hash ?d?d?d?d?d?d?d?d?d?d
```

參數說明：

- -m 23800：指定使用針對 RAR3 格式的 Hash 模式。

- archive.hash：事先利用 rar2john 提取的 Hash 文件。

- your_wordlist.txt：包含可能密碼的字典檔案。
- -a : 暴力解
- ?d : mask attck中代表數字(?a : 代表全部)