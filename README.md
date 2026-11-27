# GGE — DSH 静态逆向工程插件

GGE 是一款面向 DeepSeek Harness（DSH）的静态逆向工程插件，内置 **7 项逆向分析技能**，覆盖文件初筛、原生二进制、构建版本对比、固件、离线协议、Android 应用包和 JVM/.NET 托管代码。可以用它梳理程序入口和调用关系、比较版本行为、整理固件组件，或根据已有消息样本推断协议字段。

> **使用范围**　适用于对自有或已获授权的软件、固件及脱敏样本进行静态分析。插件按需加载技能，使用 DSH 已有的工具和权限，也可以直接阅读你提供的反编译、清单或协议导出结果。

## 安装

### 方式一：从 DSH 插件页安装

打开「插件 → 添加插件 → 安装第三方插件」，填写：

```text
github:govin-ai/gge-rea-plugins
```

安装完成后刷新插件页。需要固定版本时，在地址末尾加上 `#<提交 SHA>`。

### 方式二：从本地安装

在 DSH 的第三方插件安装界面选择仓库目录。已有本地安装包时，也可以用命令行安装。以下命令使用 DSH Web 默认的 `web` 配置。

```sh
dsh plugin --profile web add /absolute/path/dsh-defensive-file-triage-0.2.0.tgz
```

## 技能目录

| 技能 | 用途 |
| --- | --- |
| [文件初筛](skills/defensive-file-triage/SKILL.md) | 识别文件格式，计算 SHA-256，记录样本信息 |
| [原生二进制阅读](skills/re-static-binary-reading/SKILL.md) | 梳理 PE、ELF 或 Mach-O 的函数、导入和调用关系 |
| [二进制版本差异](skills/re-binary-version-diff/SKILL.md) | 对照两个构建版本的模块、接口和可观察行为 |
| [固件布局](skills/re-firmware-layout/SKILL.md) | 整理分区、组件和有证据支持的启动关系 |
| [离线协议格式](skills/re-offline-protocol-format/SKILL.md) | 对比脱敏消息样本，推断字段边界、端序和长度规则 |
| [Android 包阅读](skills/re-android-package-reading/SKILL.md) | 阅读清单、资源和类索引，识别应用入口与组件 |
| [托管代码阅读](skills/re-managed-code-reading/SKILL.md) | 阅读 JVM 或 .NET 元数据与反编译结果，梳理模块和数据流 |

## 使用示例

安装后，在 DSH 会话里点名技能并指定要分析的材料。

- 「用 `re-static-binary-reading` 阅读这份反编译结果，找出配置文件的读取入口，列出调用链和证据位置。」
- 「用 `re-binary-version-diff` 对比这两个版本的导出符号和反编译结果，整理接口和行为变化。」

插件随包提供 DSH 配置与技能文档，安装无需运行安装脚本或下载额外依赖。二进制反汇编、清单导出等工作可使用已有本地工具完成。[DeepSeek Harness 官方打包文档](https://github.com/deepseek-ai/deepseek-harness/blob/master/docs/user/develop/basic/publish.md)
