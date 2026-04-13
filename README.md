# security-learning-journal-
记录日志
# 🎯 60天求职导向学习计划 ( - 基于历史实践)

> **核心理念**：将每一次漏洞复现、每一个脚本编写，都视为一个“微型项目”，最终打包成简历中的“项目经验”。

## 目标岗位
- 初中级网络安全工程师（代码魔方）
- 安全服务工程师（东琳电子）
- 信息搜集实习生（校招）

## 我的核心优势（基于历史实践）
- **工程能力**：已独立开发并优化 `my_scanner_pro_vX.py` 多线程目录扫描器，解决编码、死锁、进度反馈等工程问题。
- **漏洞基础**：已在 Yakit 靶场系统性地复现 XSS, SQLi, CSRF 等 OWASP Top 10 漏洞。
- **自动化思维**：习惯使用 Python 脚本 (`csrf_poc.py`) 替代手动操作，提升效率。

## 核心能力映射与行动计划

| 招聘要求关键词 | 我的当前进度 | 行动计划 (产出物) | 计划完成日 |
|----------------|--------------|-------------------|------------|
| **OWASP Top 10** | ✅ 已掌握 XSS, SQLi, CSRF 的原理与复现 | **产出**: 将每个漏洞整理为 `day-XX-<vuln>.md` 技术笔记，并附上 PoC 代码。 | Day 15 |
| **Python/Shell 脚本** | ✅ `my_scanner_pro_vX.py` (目录扫描), `csrf_poc.py` | **产出**: 1. 优化 `csrf_poc.py` 为通用工具。<br>2. 开发 `idor_poc.py` (越权检测)。 | Day 30 |
| **SRC提交经验** | ⏳ 准备中 | **产出**: 在 [PortSwigger Web Security Academy](https://portswigger.net/web-security) 或公开靶场完成一次完整漏洞报告提交。 | Day 30 |
| **信息搜集工具** | ⏳ Fofa/Hunter 未实操 | **产出**: 使用 Fofa 语法搜索特定资产，导出清单 `asset-list.csv`，并写一篇《信息搜集入门：从Fofa到资产测绘》博客。 | Day 26 |
| **技术博客** | ⏳ 第一篇草稿待写 | **产出**: 将 `my_scanner_pro_vX.py` 的开发历程写成博客《从零手写...》，发布至 FreeBuf/GitHub。 | Day 15 |

## 📅 本周重点（Day 8–12）：巩固成果，打造作品集

- [x] **CSRF PoC 脚本验证成功** (`csrf_poc.py`)
- [ ] **【关键】创建 GitHub 仓库 `web-vuln-pocs`**
    - 上传 `csrf_poc.py`, `attack.html`
    - 创建 `README.md`，描述漏洞原理、复现步骤、修复建议。
    - **这是你简历上的第一个“项目”！**
- [ ] **撰写第一篇技术博客草稿**
    - 主题：二选一
        - A. **《从零复现CSRF：一次成功的状态篡改攻击》** (聚焦漏洞)
        - B. **《从零手写 Python 多线程目录扫描器》** (聚焦工程)
    - 平台：FreeBuf + GitHub Pages

## 📅 下周预告（Day 13–20）：向“越权漏洞”发起冲击

- **学习目标**: 掌握 IDOR (Insecure Direct Object Reference) 漏洞。
- **Yakit 靶场**: 寻找 `订单详情页面（爆破 / 遍历订单号...）` 或 `Web 后台 用户容器页面`。
- **产出**: `day-16-idor.md` + `idor_poc.py` (自动遍历ID并检测响应差异)。
