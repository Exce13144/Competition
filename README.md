# 第三届长城杯 · 半决赛 Pwn 赛题归档

本仓库归档「第三届长城杯」半决赛 Pwn 方向的赛题附件，便于赛后复盘与学习交流。

> 说明：赛题版权归赛事主办方所有，本仓库仅作技术学习与赛后研究之用，请勿用于任何商业用途。

## 题目列表

| 题目 | 类型 | 附件 | 备注 |
| --- | --- | --- | --- |
| catchme | Pwn | `catchme/catchme`、`catchme/libc-2.27.so` | 自带 libc 2.27 |
| easy_rw_revenge | Pwn | `easy_rw_revenge/pwn`、`proxy`、`ld-linux-x86-64.so.2`、`libc.so.6` | 自带 loader + libc |
| minidb | Pwn | `minidb/pwn`、`minidb/libc.so.6` | 自带 libc |

## 目录结构

```
.
├── README.md
├── catchme/
│   ├── catchme            # 题目二进制
│   └── libc-2.27.so       # 对应 libc
├── easy_rw_revenge/
│   ├── pwn                # 题目二进制
│   ├── proxy              # 附带的 proxy 程序
│   ├── ld-linux-x86-64.so.2
│   └── libc.so.6
├── minidb/
│   ├── pwn
│   └── libc.so.6
└── original-zips/         # 原始附件包（未改动，便于校验）
    ├── catchme.zip
    ├── easy_rw_revenge.zip
    └── minidb.zip
```

## 使用提示

各题目目录均已附带出题方提供的 libc / loader，建议直接用对应的 libc 运行，避免本地环境版本差异导致调试结果不一致：

```bash
# 方式一：指定 loader 与 libc 运行
./ld-linux-x86-64.so.2 --library-path . ./pwn

# 方式二：用 patchelf 改写二进制（建议先备份副本）
patchelf --set-interpreter ./ld-linux-x86-64.so.2 --set-rpath . ./pwn
```

对于只提供 libc 的题目，可用 `pwninit` 自动补齐 loader 与调试环境：

```bash
pwninit --bin ./pwn --libc ./libc.so.6
```

## 免责声明

本仓库内容仅用于 CTF 学习、赛后复盘与漏洞研究交流。使用者应自行遵守相关法律法规，不得将相关信息用于未授权的攻击行为。
