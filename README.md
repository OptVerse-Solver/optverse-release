# Huawei OptVerse Solver Community Edition

华为天筹求解器社区版 / Huawei OptVerse Solver Community Edition

**3.8.1** · **LP / MILP / QP / SOCP / NLP / CP**<br>
**SDK**：C++ · Python（CPython 3.10–3.13）<br>
**Utilities**：IIS · Feas-Relax · Callbacks · Sensitivity analysis · Multi-objective · General constraints

适用范围见 API 文档。 / Availability varies by problem type.

## 下载 / Download

| 平台 / Platform | 安装包 / Package |
| --- | --- |
| Linux x86_64 | [tar.gz](https://github.com/OptVerse-Solver/optverse-release/releases/download/v3.8.1/optverse.3.8.1-139121240.linux.x86_64.tar.gz) |
| Linux ARM64 (aarch64) | [tar.gz](https://github.com/OptVerse-Solver/optverse-release/releases/download/v3.8.1/optverse.3.8.1-139121240.linux.aarch64.tar.gz) |
| Windows x86_64（预览 / Preview） | [zip](https://github.com/OptVerse-Solver/optverse-release/releases/download/v3.8.1/optverse.3.8.1.windows.zip) |

[最新版本 / Latest release](https://github.com/OptVerse-Solver/optverse-release/releases/latest) · [用户手册 / Documentation](https://optverse-user-manual.readthedocs.io/en/latest/)

## 安装 / Installation

将许可证示例路径替换为实际路径。 / Replace the example license paths with your actual paths.

Linux x86_64；ARM64 请将包名中的 `x86_64` 替换为 `aarch64`。 / On Linux x86_64; use `aarch64` for ARM64.

```bash
tar -xzf optverse.3.8.1-139121240.linux.x86_64.tar.gz
export LD_LIBRARY_PATH="$PWD/optverse/lib${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}"
export OPTV_LICENSE_FILE="/absolute/path/Optverse.lic"

# Verify installation
./optverse/bin/optverse --version
./optverse/bin/optverse ./optverse/examples/data/lp-example.lp
```

Windows 操作系统安装流程。 / On Windows.

```powershell
Expand-Archive -Path .\optverse.3.8.1.windows.zip -DestinationPath .\optverse
$env:PATH = "$((Resolve-Path .\optverse\bin).Path);$env:PATH"
$env:OPTV_LICENSE_FILE = "C:\licenses\Optverse.lic"

# Verify installation
.\optverse\bin\optverse.exe --version
.\optverse\bin\optverse.exe .\optverse\examples\data\lp-example.lp
```

### Python SDK

使用随包 wheel 和 [uv](https://docs.astral.sh/uv/) 安装。以下示例为 CPython 3.12；其他版本请同时修改 Python 版本和 wheel 标签，ARM64 请将 `x86_64` 改为 `aarch64`。

Install the bundled wheel with uv. These examples use CPython 3.12; update the Python version and wheel tags for other versions, and use `aarch64` for ARM64.

Linux：

```bash
uv venv --python 3.12 .venv
uv pip install --python .venv/bin/python ./optverse/dist/optvpy-3.8.1-cp312-cp312-manylinux_2_27_x86_64.whl
.venv/bin/python ./optverse/examples/python/lp1.py
```

Windows PowerShell：

```powershell
uv venv --python 3.12 .venv
uv pip install --python .venv\Scripts\python.exe .\optverse\dist\optvpy-3.8.1-cp312-cp312-win_amd64.whl
.\.venv\Scripts\python.exe .\optverse\examples\python\lp1.py
```

也可通过pip命令直接安装。/ Or install python SDK with.

```bash
pip install optvpy
```

运行前请配置上方的库路径和实际许可证路径。 / Configure the library and actual license paths above before running.

安装包 SHA256 见 [Release](https://github.com/OptVerse-Solver/optverse-release/releases/tag/v3.8.1#sha256)。 / Package SHA256 checksums are listed in the Release.

## 使用许可 / Licensing

学术用户免费，CLI 和 SDK 均需有效许可证。[申请学术试用](https://optverse.com.cn/#/)或联系 [optverse@huawei.com](mailto:optverse@huawei.com) 获取授权。试用仅限技术评估，不得用于商业、生产或盈利目的。

Free for academic users; the CLI and SDKs require a valid license. [Request an academic trial](https://optverse.com.cn/#/) or contact the team for licensing. Trial licenses permit technical evaluation only, excluding commercial, production, and profit-making use.

- **求解器与 SDK / Solver & SDKs**：[EULA 中文](licenses/3.8.1/optv-eula_cn.pdf) · [English](licenses/3.8.1/optv-eula_en.pdf)
- **公开文档 / Public documentation**：[Apache 2.0](docs/LICENSE)，不含求解器、SDK、EULA 和另有许可的第三方内容。 / Excludes the solver, SDKs, EULA, and separately licensed third-party content.
