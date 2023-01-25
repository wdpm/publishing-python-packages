# Exercises for Publishing Python Packages: Test, share, and automate your projects 🐍 📦 ⬆️

Fork of 《Publishing Python Packages》book.

## 笔记

目录说明：

- .github
- ch05 初具模型，基础的tox的使用
- ch06 重构解耦代码，模块化，SOLID原则。增加 typecheck(mypy)、lint(flake8)、format(black) 、测试hello配置。
- ~~ch07/ src和test代码和ch06一致，删除~~
- ch08/ 增加文档构建配置。sphinx，默认主题alabaster非常简陋。**添加自定义sphinx-rtd-theme主题后，注意在 cfg 文件中添加对应依赖**。
- ch09/
- .pre-commit-config.yaml

.github 中关注 workflow 的配置。

ch09添加了docs生成配置，ch10的模本生成不实用可以抛弃。

.pre-commit-config.yaml 配置了本地pre-commit的hooks。