# GGE RE Plugins

面向 DeepSeek Harness 的静态逆向工程技能包。适合阅读陌生程序的结构、理解模块行为、比较构建版本，以及整理固件和离线协议样本。

| 技能 | 用途 |
| --- | --- |
| [文件初筛](skills/defensive-file-triage/SKILL.md) | 识别文件格式，计算 SHA-256，记录样本信息 |
| [原生二进制阅读](skills/re-static-binary-reading/SKILL.md) | 分析 PE、ELF 或 Mach-O 的函数、导入和调用关系 |
| [二进制版本差异](skills/re-binary-version-diff/SKILL.md) | 对比构建版本的模块、接口和关键行为 |
| [固件布局](skills/re-firmware-layout/SKILL.md) | 整理分区、组件和已有证据支持的启动关系 |
| [离线协议格式](skills/re-offline-protocol-format/SKILL.md) | 对比脱敏消息样本，推断字段、端序和长度规则 |
| [Android 包阅读](skills/re-android-package-reading/SKILL.md) | 分析清单、资源、组件和应用入口 |
| [托管代码阅读](skills/re-managed-code-reading/SKILL.md) | 阅读 JVM 或 .NET 元数据与反编译结果，梳理模块和数据流 |

包内是 DSH 配置与技能文档，沿用 DSH 已有的工具和权限。技能按需阅读用户指定的产物或已导出的分析结果。包内没有安装脚本、额外依赖或自带执行工具。

## 安装

在 DSH 打开「插件 → 添加插件 → 安装第三方插件」，填写 `github:govin-ai/gge-rea-plugins`。需要固定版本时，可在地址后加 `#<提交 SHA>`。

从本地安装时可选择仓库目录，或用命令行安装打包文件。以下示例使用 Web 默认的 `web` profile。

```sh
dsh plugin --profile web add /absolute/path/dsh-defensive-file-triage-0.2.0.tgz
```

安装后刷新插件页。可在会话中直接点名技能，例如「使用 `re-static-binary-reading` 阅读我提供的反编译结果，标注入口和调用关系」。技能所需的反汇编、清单等数据可由已有本地工具生成，也可以直接提供已有的导出结果。

[DeepSeek Harness 官方打包文档](https://github.com/deepseek-ai/deepseek-harness/blob/master/docs/user/develop/basic/publish.md)
