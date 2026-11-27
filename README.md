# DSH 防御性文件初筛

为 DeepSeek Harness 提供一个只读静态检查技能。可记录本地证据文件的字节数、修改时间、SHA-256 和格式线索。技能在会话中按需加载，沿用 DSH 的工具权限。

包内只有 DSH 配置和技能文档。配置只解析包内技能路径并启用 DSH 自带的文件系统技能提供器。没有第三方依赖、安装脚本、自定义命令或网络客户端。技能指引的只读范围依赖 DSH 的权限控制。

## 安装

在 DSH 打开「插件 → 添加插件 → 安装第三方插件」，选择包含本文件的本地目录。也可以在插件安装框使用 Git 规格 `github:OWNER/REPO#COMMIT`。私有仓库需要本机有该仓库的 Git 读取权限。

Web 默认使用 `web` profile。若用命令行从本地安装，请将示例路径替换为本包的绝对路径。

```sh
dsh plugin --profile web add file:/absolute/path/dsh-defensive-file-triage
```

安装后刷新插件页。在有文件读取能力的会话试用「用 defensive-file-triage 对我指定的本地文件做静态初筛」。通过插件页卸载，或运行 `dsh plugin --profile web remove dsh-defensive-file-triage`。

[DeepSeek Harness 官方打包文档](https://github.com/deepseek-ai/deepseek-harness/blob/master/docs/user/develop/basic/publish.md)
