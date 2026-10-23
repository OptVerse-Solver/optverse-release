# 安装 / Installation — 3.8.1

## 环境 / Requirements

- **平台 / Platforms**：Linux x86_64、Linux ARM64 (aarch64)、Windows x86_64（预览 / Preview）。
- **Linux**：包内手册要求 / Bundled manual requirements: glibc >= 2.33、libstdc++ >= 6.0.26。
- **Windows**：保留 `bin/` 中的运行库 DLL。 / Keep the runtime DLLs supplied in `bin/`.
- **Python**：CPython 3.10–3.13；使用 [uv](https://docs.astral.sh/uv/) 管理环境。 / Use uv for the Python environment.
- **C++ 示例 / Examples**：C++17、CMake >= 3.13。

## 下载与校验 / Download & verify

从 [3.8.1 Release](https://github.com/OptVerse-Solver/optverse-release/releases/tag/v3.8.1) 下载对应平台的安装包，核对 SHA256 后解压。 / Download the package for your platform and verify its SHA256 before extraction.

```text
bc3642f63050eed8758fc0559d3f7f7d7520355e94733e681dbb4c6c98248fed  optverse.3.8.1-139121240.linux.aarch64.tar.gz
71e06d3b063fc9dccb17b0b8f10a59a86aca26c58a59e0c20b1d731852e2b218  optverse.3.8.1-139121240.linux.x86_64.tar.gz
ef268915d1629ea81548b472aa7905ab8b5d8306be349d9a01478f58dbc51b1b  optverse.3.8.1.windows.zip
```

Linux：

```bash
sha256sum optverse.3.8.1-139121240.linux.x86_64.tar.gz
```

Windows PowerShell：

```powershell
Get-FileHash .\optverse.3.8.1.windows.zip -Algorithm SHA256
```

## 许可证 / License

使用前阅读 [EULA](licenses/3.8.1/)，通过[官网](https://optverse.com.cn/#/)或 [optverse@huawei.com](mailto:optverse@huawei.com) 获取许可证文件，将下方示例路径替换为实际路径。

Read the EULA and obtain a license file through the website or email above. Replace the example license paths below with your actual path.

## Linux

x86_64、CPython 3.12 示例；ARM64 请将包名和 wheel 中的 `x86_64` 改为 `aarch64`。 / Example for x86_64 and CPython 3.12; use `aarch64` for ARM64.

```bash
tar -xzf optverse.3.8.1-139121240.linux.x86_64.tar.gz
export LD_LIBRARY_PATH="$PWD/optverse/lib${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}"
export OPTV_LICENSE_FILE="/absolute/path/Optverse.lic"
./optverse/bin/optverse --version
./optverse/bin/optverse ./optverse/examples/data/lp-example.lp
uv venv --python 3.12 .venv
uv pip install --python .venv/bin/python ./optverse/dist/optvpy-3.8.1-cp312-cp312-manylinux_2_27_x86_64.whl
.venv/bin/python ./optverse/examples/python/lp1.py
```

## Windows（预览 / Preview）

PowerShell、CPython 3.12：

```powershell
Expand-Archive -Path .\optverse.3.8.1.windows.zip -DestinationPath .\optverse
$env:PATH = "$((Resolve-Path .\optverse\bin).Path);$env:PATH"
$env:OPTV_LICENSE_FILE = "C:\licenses\Optverse.lic"
.\optverse\bin\optverse.exe --version
.\optverse\bin\optverse.exe .\optverse\examples\data\lp-example.lp
uv venv --python 3.12 .venv
uv pip install --python .venv\Scripts\python.exe .\optverse\dist\optvpy-3.8.1-cp312-cp312-win_amd64.whl
.\.venv\Scripts\python.exe .\optverse\examples\python\lp1.py
```

其他 Python 版本请同时替换 `--python 3.12` 和 wheel 的 `cp312-cp312`。环境变量仅对当前终端有效。 / For another Python version, update both the interpreter version and wheel tags. Environment variables apply to the current session.

包内 `docs/` 提供中英文手册，`examples/` 提供示例。 / Manuals and examples are in `docs/` and `examples/`.

本指南 / This guide: [Apache 2.0](docs/LICENSE). 求解器与 SDK / Solver & SDKs: [EULA](licenses/3.8.1/).
