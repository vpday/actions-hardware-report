# actions-hardware-report

获取 GitHub Actions 中 Windows 运行环境的硬件规格信息。

工作流在 `windows-2022` 和 `windows-2025` 镜像中执行以下工具：

1.  **Systeminfo**: Windows 内置的系统配置信息工具。
2.  **Coreinfo**: Sysinternals 提供的工具。
3.  **CPU-Z**: CPUID 提供的硬件信息报告工具。

## 使用方法

通过 `workflow_dispatch` 手动触发工作流。

## 输入参数

| 参数名 | 描述 | 是否必填 | 默认值 |
| :--- | :--- | :--- | :--- |
| `cpuz_version` | 需要下载的 CPU-Z 版本号（例如 `2.12`, `2.17`）。 | 是 | `2.17` |

> **注意**：如果输入的版本号在 CPUID 服务器上不存在，工作流将执行失败。

## 输出结果 (Artifacts)

执行成功后，工作流将上传名为 `hardware-reports-<os-version>` 的压缩包。其中包含：

*   `coreinfo.txt`: Coreinfo 的输出内容。
*   `cpuz_report.txt`: CPU-Z 生成的报告。