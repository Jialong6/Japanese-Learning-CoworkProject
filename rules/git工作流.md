# Git 自动版本管理

## 自动 commit（每次文件改动后）

每当对项目文件执行写入或编辑操作后，立即执行 git commit。规则：

1. **触发时机：** 每次用 Write/Edit 工具修改了项目文件后，在回复用户之前先 commit
2. **commit 范围：** 只 add 刚刚改动的文件，不用 `git add -A`
3. **commit message 格式：** 用中文，简明说明改了哪个文件、做了什么
   - 例：`更新 错题本.md：添加 2026-04-02 练习记录，新增3个薄弱语法点`
   - 例：`新建 语法练习_2026-04-02_16-19课.md：生成60题复习练习卷`
   - 例：`更新 CLAUDE.md：词汇范围从第25课扩展到第30课`
4. **批量操作：** 如果一个命令流程中连续改了多个文件（如批改时更新错题本+错题精讲+错误模式库），可以合并为一次 commit，message 中列出所有改动
5. **不 commit 的情况：** 临时文件、.DS_Store、用户还没做完题的练习卷

## 每次任务完成后 push

每次 Jay 发消息、Claude 完成对应任务后，在回复用户之前执行：

1. 确保所有改动已 commit（上一步的自动 commit 应该已覆盖）
2. 执行 `git push origin main`
3. 如果 push 失败（认证问题等），告诉 Jay 具体错误，让 Jay 协助解决
4. push 成功后简要告知

> **注意：** git config 已配置好（user.name: Jialong6, user.email: jialon66@gmail.com）。push 时如果遇到认证问题，需要 Jay 提供 token。
