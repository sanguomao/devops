# 仓库CI配置自动化工具
通过脚本自动为代码仓库构建CI配置。

## 实现的功能
脚本旨在实现以下功能:
1. 基于模版为仓库创建Dockerfile，以协助仓库构建镜像（各仓库再次基础上添加自定义内容）。
2. 基于模版为仓库创建Makefile，为仓库提供lint，test，build等命令行功能。
3. 基于模版为仓库创建相关的Jenkins jobs以及各类job对应的Jenkinsfile。
4. 目前支持两种仓库模版：1.typescript 2.python。