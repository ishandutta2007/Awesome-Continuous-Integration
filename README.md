# Awesome-Continuous-Integration

# 顶级持续集成（CI）平台生态系统

**精选 SaaS 产品与开源 GitHub 项目**
*聚焦流水线编排、构建自动化、测试执行与制品管理*
**最后更新：2026 年 9 月**

本仓库追踪 **持续集成（CI）** 领域的知名 **SaaS 平台** 与 **开源项目**。这些工具帮助开发团队在代码提交后自动构建、测试和验证软件，缩短反馈周期，确保代码质量。

**示例** 包括 CircleCI、GitHub Actions、GitLab CI/CD、Jenkins、Buildkite、Semaphore CI、Travis CI、Bitrise、Codefresh 和 TeamCity（该领域的领先者）。

**开源重点**：CI 是开源生态 **最成熟、最丰富** 的领域之一。从 Jenkins 到 Tekton，从 Drone 到 Woodpecker，开源 CI 引擎覆盖了从简单构建到大规模分布式流水线的全部场景。**本地优先** 和 **自托管** 是当前开源 CI 的核心趋势——**preloop** 让你在本地运行 GitHub Actions 工作流，**Fluent CI** 基于 Dagger 实现“在任何地方以一致方式运行流水线”，**SimpleCI** 用单个 Go 二进制替代 Jenkins 的复杂性。

欢迎贡献！提交 PR 以添加/更新条目。保持描述事实性，并链接到官方网站。

## 目录

- [SaaS/托管平台](#saas托管平台)
- [开源 GitHub 项目](#开源github项目)
- [如何贡献](#如何贡献)
- [免责声明](#免责声明)

## SaaS/托管平台

- **[GitHub Actions](https://github.com/features/actions)**
  GitHub 原生 CI/CD，拥有 6,000+ 市场 Action。工作流在 GitHub 托管的 Linux、macOS、Windows 或容器运行器上执行。开源仓库免费，私有仓库有使用限额 。

- **[GitLab CI/CD](https://about.gitlab.com/stages-devops-lifecycle/continuous-integration/)**
  GitLab 内置的 CI/CD，支持 Auto DevOps 和流水线可视化。支持 Linux、macOS（beta）、Windows（beta）运行器。开源项目可申请 50,000 分钟免费额度 。

- **[CircleCI](https://circleci.com/)**
  云原生 CI/CD，以 Docker 层缓存和并行执行著称。提供开源项目免费额度。注意：**Cirrus CI 将于 2026 年 6 月 1 日关停**，不再是可选方案 。

- **[Jenkins Cloud](https://www.jenkins.io/)**
  可扩展的自动化服务器，拥有 1,800+ 插件。传统自托管 CI 的事实标准，云托管选项由第三方提供 。

- **[Buildkite](https://buildkite.com/)**
  混合 CI/CD——Agent 运行在你自己的基础设施上，UI 在云端。开源 Agent 用 Go 编写，支持在任何设备或网络上安全运行构建任务 。

- **[Semaphore CI](https://semaphoreci.com/)**
  高性能 CI/CD，以测试并行化能力著称 。

- **[Travis CI](https://travis-ci.com/)**
  早期云 CI 的先驱，与 GitHub 深度集成。仍在运营但市场份额已大幅下降。

- **[Bitrise](https://www.bitrise.io/)**
  移动端 CI/CD 专家，专注于 iOS 和 Android 构建、测试和部署。

- **[Codefresh](https://codefresh.io/)**
  面向 Kubernetes 和 Docker 的 CI/CD 平台，已被 Harness 收购。

- **[TeamCity](https://www.jetbrains.com/teamcity/)**
  JetBrains 的 CI/CD 服务器，以强大的构建配置管理和 .NET/Java 生态集成著称。

## 开源 GitHub 项目

### 本地优先 CI

- **[preloop](https://github.com/preloopdev/preloop)**
  **本地自托管的 GitHub Actions 等价方案。** 引擎接受与 GitHub 相同的工作流格式：`${{ }}` 表达式、矩阵构建、可复用工作流、并发组、OIDC 等。在硬件隔离的 **microVM** 上执行，可在 Windows/macOS/Linux 运行，**300ms 恢复**。你的 `.github/workflows` 文件 **无需修改** 即可运行，支持针对 **未提交更改** 运行 CI。使用官方 `actions/runner` 协议，无需消耗 GitHub 托管分钟数。Rust 运行器比官方二进制小 10 倍，内存占用低 10 倍。控制平面 RSS 约 **15MB**。支持 DAP 调试器，可在失败时暂停并检查上下文 。

- **[Fluent CI](https://github.com/fluentci-io/fluentci)**
  **基于 Dagger、Wasm 和 Deno 的自托管 CI/CD 工具。** 完全免费开源。核心特点：**单命令管理流水线**（`fluentci init && fluentci`），在 **任何机器上运行**（本地、远程、云、物理服务器、VM，x86 或 ARM），**导出到任何 CI 提供商**（GitHub Actions、GitLab CI、Azure Pipelines、AWS CodePipeline、CircleCI 等）。内置 **流水线注册表**，搜索使用他人为 Django、React、Node 等框架构建的预置流水线。支持 Web UI（FluentCI Studio）。可选 Nix 环境替代 Docker 。

- **[SimpleCI](https://github.com/haatos/simple-ci)**
  **轻量级自托管 CI，用单个 Go 二进制替代 Jenkins 的复杂性。** 100% Go 代码库，使用 **templ** 做服务端渲染，**HTMX** 做动态 UI——无重型 JavaScript 框架。架构：中心 **控制器**（Web 应用）管理凭据、Agent 和流水线；**Agent** 是通过 SSH 连接的远程机器，执行 YAML 定义的流水线。功能包括 **凭据加密存储**、**Agent 编排**、**YAML 流水线定义**（从 Git 仓库读取）、**Cron 调度**、**Web 仪表板**（实时构建日志）、**Webhook 集成**（GitHub/GitLab push/PR 触发）、**制品存储**。SQLite 数据库，**无需 Node.js，无需 Docker** 。

### 全功能 CI/CD 服务器

- **[Jenkins](https://github.com/jenkinsci/jenkins)**
  **CI 领域的开源鼻祖和事实标准。** 拥有 **1,800+ 插件**，几乎可以自动化任何任务。支持任何 VCS（git、mercurial、cvs、subversion）。虽然 UI 相对陈旧、维护成本较高，但仍是企业自托管 CI 的默认选择。**开源** 。

- **[GoCD](https://github.com/gocd/gocd)**
  **开源本地部署持续交付工具。** 以 **流水线可视化** 和 **价值流图** 著称，帮助团队理解从提交到部署的完整流程。支持 Git、Perforce、Mercurial、Subversion、TFS 和自定义 VCS。**开源** 。

- **[Drone CI](https://github.com/drone/drone)**
  **容器原生 CI/CD 服务。** 社区版 **Apache 2.0** 许可。支持 GitHub、GitLab、Gitea、BitBucket 和自定义 Git 服务。以 **简洁的 YAML 语法** 和 **Docker 优先设计** 闻名。被 Harness 收购后社区版仍免费自托管 。

- **[Woodpecker CI](https://github.com/woodpecker-ci/woodpecker)**
  **Drone CI 的轻量级社区分支。** 在 Drone 被收购后，社区接管维护，保持开源精神。支持多 forge（GitHub、GitLab、Gitea、Forgejo、Bitbucket）。**轻量级 CI 引擎**，适合希望从 Drone 迁移或寻求更简单替代方案的小型团队 。

- **[Tekton](https://github.com/tektoncd/pipeline)**
  **Kubernetes 原生 CI/CD 构建块。** 作为 **CD Foundation** 项目，Tekton 提供在 Kubernetes 集群内运行流水线的标准方式。Jenkins X 使用 Tekton 作为 Kubernetes 上的云原生流水线引擎 。

- **[Agola](https://github.com/agola-io/agola)**
  **重新定义 CI/CD。** 开源、自托管，支持 Docker 和 Kubernetes 后端。以 **1,506 stars** 和 **117 forks** 在持续交付领域获得关注。**开源** 。

- **[Kraken CI](https://kraken.ci/)**
  **现代开源本地 CI/CD 系统，高度可扩展且专注于测试。** 使用 **Starlark/Python** 定义工作流。执行器支持 **裸金属、Docker、LXD、VM**。可扩展到 **数千个执行器**。提供 **复杂的测试结果分析**、邮件和 Slack 通知。**开源** 。

- **[LAVA](https://www.lavasoftware.org/)**
  **Linaro 自动化验证架构——面向硬件和操作系统的持续集成系统。** 专门用于 **将操作系统部署到物理和虚拟硬件上运行测试**。测试类型包括简单启动测试、引导加载程序测试和系统级测试。结果随时间跟踪并可导出分析。Debian 提供 `lava-server` 包。**开源** 。

- **[PikoCI](https://github.com/pikoci/pikoci)**
  **Concourse 精神的自托管 CI。** 资源模型直接 **受 Concourse 启发**。主要区别：用 **Runners** 替代 `task image_resource`，单二进制部署（非多服务 + PostgreSQL 架构），支持 Vault 和文件密钥。流水线用 **HCL** 定义。支持 **Docker Compose** 一键评估。**PikoCI 用自己的 CI 跑自己的流水线**（dogfooding）。

- **[Pipewright](https://github.com/huangchengsir/pipewright)**
  **单 Go 二进制的轻量自托管 CI/CD + 部署 + 运维平台。** 零依赖。支持 **Pipeline as Code**——将流水线结构提交到 `.pipewright.yml`，与代码同源、可在 PR 中审查、按分支演进。如果 YAML 文件缺失或无效，自动回退到 Canvas UI 配置，**永不破坏运行**。内置 **GitOps 流水线**、**SSH 部署**、**健康检查**、**预览环境**、**异常检测**、**服务器指标采样**。Vue 3 前端嵌入二进制 。

### 流水线引擎与工具

- **[Dagger](https://dagger.io/)**
  **可编程 CI/CD 引擎，在容器中运行流水线。** 让流水线在笔记本和 CI 环境间 **可移植且一致**。“在我的机器上能跑”问题的根治方案。支持 GitHub、GitLab、Gitea。**开源** 。

- **[gitlab-ci-local](https://github.com/firecow/gitlab-ci-local)**
  **在本地运行 GitLab CI/CD 流水线，而非推送到远程测试。** 支持 Docker 和 shell 执行器、变量展开、includes、缓存、制品、services、并行作业。**MIT 许可** 。

- **[Dagu](https://github.com/dagu-org/dagu)**
  **开发者友好的极简 Cron 替代品**，能力远超传统 Cron。**1,618 stars**。用于复杂任务编排 。

### 其他强开源选项

- **本地/轻量**：**preloop**（GitHub Actions 本地运行）、**SimpleCI**（Go 单二进制）、**Fluent CI**（Dagger 驱动）、**gitlab-ci-local**（GitLab 本地运行）。
- **全功能服务器**：**Jenkins**（1,800+ 插件）、**GoCD**（流水线可视化）、**Drone**（容器原生）、**Woodpecker**（Drone 分支）、**Tekton**（K8s 原生）。
- **可扩展/测试聚焦**：**Kraken CI**（Starlark/Python，数千执行器）、**LAVA**（硬件/OS 测试）、**Agola**（Docker/K8s）。
- **一体化平台**：**Pipewright**（CI/CD + 部署 + 运维，Pipeline as Code）。

**构建自定义系统的框架**：以 **Tekton** 或 **Drone** 为流水线引擎，**preloop** 或 **gitlab-ci-local** 实现本地开发反馈循环，**Dagger** 保证环境一致性，**Pipewright** 提供一体化自托管平台。用 **Argo CD** 或 **Flux** 补充 GitOps 部署能力。

## 如何贡献

1. Fork 仓库。
2. 在 `README.md` 中添加/编辑条目（遵循现有格式）。
3. 包含：名称、链接、1–2 句描述，以及是 SaaS 还是开源。
4. 提交 PR 并附简短说明。

如果你觉得这个仓库有用，请点星！

## 免责声明

- 这是一个 **社区精选** 列表——并非详尽无遗，也不构成认可。
- CI 平台处理源代码和构建制品；确保访问控制和密钥管理符合安全策略。
- **开源现实**：CI 是 **开源生态最成熟的领域之一**。**preloop** 让你在本地以 300ms 恢复速度运行 GitHub Actions 工作流 。**Fluent CI** 基于 Dagger 实现跨环境一致性 。**SimpleCI** 用单个 Go 二进制替代 Jenkins 的复杂性 。**Kraken CI** 可扩展到数千执行器并专注测试分析 。**Pipewright** 提供 CI/CD + 部署 + 运维的一体化单二进制方案 。对于需要 **企业级支持、托管运行器、深度 IDE 集成** 的团队，商业平台（GitHub Actions、CircleCI、Buildkite）仍是首选——但开源替代方案在自托管场景下 **完全可行**。

---

**为 DevOps 工程师、平台团队、SRE 和开发者打造。**
让持续集成更开放、透明、高效。
