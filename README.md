# Exercises for Publishing Python Packages: Test, share, and automate your projects 🐍 📦 ⬆️

[![Documentation Status](https://readthedocs.org/projects/publishing-python-packages/badge/?version=latest)](https://publishing-python-packages.readthedocs.io/en/latest/?badge=latest)

Fork of 《Publishing Python Packages》book.

## 笔记

目录说明：

- .github
- ch05

  初具模型，基础的tox的使用
- ch06

  重构解耦代码，模块化，SOLID原则。增加 typecheck(mypy)、lint(flake8)、format(black) 、测试hello配置。
- ~~ch07/ src和test代码和ch06一致，删除~~
- ch08/

    - 增加sphinx文档构建配置。默认主题alabaster非常简陋。**添加自定义sphinx-rtd-theme主题后，注意在 cfg 文件中添加对应依赖**。
    - 托管到read the docs网站。注册read the docs账号，可以使用github互联。
        - 0.保证project根目录下存在正确配置的.readthedocs.yaml
        - 1.import 特定的github project；
        - 2.填写元信息，勾选advanced setting。
        - 3.填写 Project Extra Details。
    - Running sphinx-apidoc on Read the Docs。配置对应 conf.py，利用build doc的生命周期的builder-inited
    - update per pull-request:
        - visit https://readthedocs.org/dashboard/publishing-python-packages/edit/
        - click `Admin`,click `advanced setting`.
        - select `Build pull requests for this project`, then save.
        - push a change(must be pr, not push) to this repo to check if works as expected.
        - 配置文档查阅：https://docs.readthedocs.io/en/stable/pull-requests.html

- ch09/
- .pre-commit-config.yaml

.github 中关注 workflow 的配置。

ch09添加了docs生成配置，ch10的模本生成不实用可以抛弃。

.pre-commit-config.yaml 配置了本地pre-commit的hooks。