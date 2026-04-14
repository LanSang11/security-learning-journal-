# 《从零手写 Python 多线程目录扫描器：解决编码、死锁与进度反馈》

## 1. 引言：为什么重复造轮子？
- **痛点驱动**: 现有工具（如 dirsearch）在某些场景下不够灵活，我想深入理解其底层原理。
- **学习目标**: 掌握多线程编程、网络请求处理、异常控制流等核心技能。
- **成果预览**: 最终得到一个功能完整、稳定可靠的 `my_scanner_pro.py`。

## 2. 核心挑战与我的解决方案 (这是文章的核心价值！)
### 挑战 1: 多线程任务分发与管理
- **问题**: 如何高效地将成千上万的路径分发给多个线程，避免重复或遗漏？
- **我的方案**: 使用 `queue.Queue` 作为线程安全的任务池。
- **关键代码片段**:
    ```python
    # 创建任务队列
    task_queue = queue.Queue()
    for path in wordlist:
        task_queue.put(base_url + path)
    ```

### 挑战 2: 编码地狱 (UnicodeDecodeError)
- **问题**: 目标网站返回的响应体编码五花八门（UTF-8, GBK, ISO-8859-1...），直接 `.text` 会报错。
- **我的方案**: 尝试多种编码，并优雅降级。
- **关键代码片段**:
    ```python
    def safe_decode(response):
        for encoding in ['utf-8', 'gbk', 'iso-8859-1']:
            try:
                return response.content.decode(encoding)
            except UnicodeDecodeError:
                continue
        return response.content.decode('utf-8', errors='ignore') # 最后手段
    ```

### 挑战 3: 主线程被阻塞 (假死/无进度)
- **问题**: 主线程如何知道所有工作线程都完成了？如何实时显示进度？
- **我的方案**: 使用 `threading.Event` 或计数器来同步。
- **关键代码片段**:
    ```python
    # 简单的计数器方案
    completed_tasks = 0
    lock = threading.Lock()

    def worker():
        global completed_tasks
        while not task_queue.empty():
            # ... do work ...
            with lock:
                completed_tasks += 1
                print(f"\r[+] Progress: {completed_tasks}/{total_tasks}", end="")
    ```

## 3. 最终效果展示
- **命令行截图**: 展示扫描器运行时的实时进度条和发现的有效路径。
- **结果输出**: 展示 `found.txt` 文件的内容。

## 4. 总结与未来展望
- **收获**: 不仅得到了一个工具，更深刻理解了并发编程的陷阱与模式。
- **优化方向**: 加入更多功能，如递归扫描、自定义Header、速率限制等。
