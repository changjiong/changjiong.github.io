# [ubuntu 如何安装代码统计工具tokei 和scc？](https://github.com/changjiong/changjiong.github.io/issues/13)

在 Ubuntu 上安装这两款工具非常简单，你可以根据自己的习惯选择通过包管理器直接安装，或者通过 Rust/Go 的环境进行安装。

### 1. 安装 tokei

[tokei](https://github.com/XAMPPRocky/tokei) 官方已经进入了 Ubuntu 的标准仓库（Ubuntu 20.04+），可以直接使用 `apt`。

* **官方仓库安装 (最快)**：
```bash
sudo apt update
sudo apt install tokei

```


* **通过 Cargo 安装 (版本最新)**：
如果你本地有 Rust 开发环境，推荐使用 Cargo，这样能获取到最新特性：
```bash
cargo install tokei

```



---

### 2. 安装 scc

[scc](https://github.com/boyter/scc) 在 Ubuntu 官方仓库中可能不直接提供，通常推荐使用 Snap 或直接下载二进制文件。

* **通过 Snap 安装 (最推荐)**：
Snap 是 Ubuntu 自带的包管理方式，安装非常方便：
```bash
sudo snap install scc

```


* **通过 Go 安装**：
如果你安装了 Go 环境，可以使用以下命令：
```bash
go install github.com/boyter/scc/v3@latest

```


* **手动安装二进制文件**：
如果你不想安装任何环境，可以去 [GitHub Releases](https://github.com/boyter/scc/releases) 下载对应的 `.deb` 包或压缩包，解压后将二进制文件移动到 `/usr/local/bin/` 即可。

---

### 常用指令对比

安装完成后，你可以对比一下两者的输出风格：

| 需求 | tokei 命令 | scc 命令 |
| --- | --- | --- |
| **基础统计** | `tokei .` | `scc .` |
| **按代码量排序** | `tokei . --sort code` | `scc . --sort code` |
| **输出 JSON 格式** | `tokei . -o json` | `scc . --format json` |
| **查看单个文件** | `tokei . --files` | `scc . --by-file` |

**提示**：如果你是在大型项目中使用，`scc` 默认会提供更详细的**复杂度 (Complexity)** 和**开发成本估算**信息；而 `tokei` 的输出则更加简洁明了。