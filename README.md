<div align="center">
  <img src="https://raw.githubusercontent.com/nowzycc/nowzycc/main/assets/hero.svg" alt="Nagato Hikari — Job-native observability for HTC/HPC" width="100%">
</div>

<p align="center">
  <a href="https://github.com/joblens-org/JobLens">
    <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=22&pause=1200&color=22D3EE&center=true&vCenter=true&width=820&height=48&lines=Job-native+observability+for+HTC%2FHPC;Building+JobLens+with+eBPF+and+C%2B%2B;Profiling+batch+workloads+by+work+progress;PhD+%40+CC.IHEP.CAS" alt="typing">
  </a>
</p>

<p align="center">
  <a href="https://github.com/joblens-org/JobLens/releases"><img src="https://img.shields.io/github/v/release/joblens-org/JobLens?style=for-the-badge&label=JobLens&labelColor=0B1020&color=22D3EE&logo=github&logoColor=white" alt="JobLens release"></a>
  <a href="https://github.com/joblens-org/JobLens"><img src="https://img.shields.io/github/stars/joblens-org/JobLens?style=for-the-badge&label=stars&labelColor=0B1020&color=A78BFA&logo=github&logoColor=white" alt="JobLens stars"></a>
  <img src="https://img.shields.io/badge/license-Apache--2.0-F472B6?style=for-the-badge&labelColor=0B1020" alt="license">
  <img src="https://komarev.com/ghpvc/?username=nowzycc&style=for-the-badge&color=22D3EE&label=PROFILE+VIEWS" alt="profile views">
</p>

---

## ⚡ 关于我

> **把监控粒度从节点下沉到作业。**
> 让每个作业的资源使用、I/O 行为与工作进度都可测量、可比较、可复用。

- 🔬 中国科学院高能物理研究所计算中心（CC.IHEP.CAS）· 博士研究
- 🛰️ 主线：**JobLens** —— 面向 HTC/HPC 的 Job-Native 可观测性 Agent
- 🧪 在研：工作进度条件化的批作业性能画像，以及真实画像驱动的 what-if 仿真
- 📍 北京 · 从自动化跨到计算机，懂一点电子与控制

---

## 🛰️ 主线工作 · JobLens

[JobLens](https://github.com/joblens-org/JobLens) 是一套面向 HTC/HPC 集群的作业级可观测性系统：在计算节点用 eBPF 采集，把资源指标精确归因到具体作业，再通过统一控制面按需采集与查询。

<p align="center">
  <img src="https://img.shields.io/badge/CPU_OVERHEAD-%3C0.15%25-22D3EE?style=for-the-badge&labelColor=0B1020" alt="CPU overhead">
  <img src="https://img.shields.io/badge/RSS-~145_MB-A78BFA?style=for-the-badge&labelColor=0B1020" alt="RSS">
  <img src="https://img.shields.io/badge/JOBS_/_NODE-251-F472B6?style=for-the-badge&labelColor=0B1020" alt="jobs per node">
  <img src="https://img.shields.io/badge/COLLECTORS-9-38BDF8?style=for-the-badge&labelColor=0B1020" alt="collectors">
  <img src="https://img.shields.io/badge/WRITERS-4-818CF8?style=for-the-badge&labelColor=0B1020" alt="writers">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/nowzycc/nowzycc/main/assets/joblens-arch.png" alt="JobLens architecture" width="100%">
</p>

| 维度 | 内容 |
|:---|:---|
| **采集** | eBPF / 内核事件为主：CPU、内存、syscall I/O、文件元数据、网络；功耗（RAPL/IPMI）、GPU（NVML） |
| **归因** | HTCondor / Slurm / cgroup；PID → Job 映射与作业生命周期事件 |
| **写出** | File / Elasticsearch / Kafka / Prometheus，按采集器路由 |
| **控制面** | Trigger（Flask）提供 REST API 与 Lua 规则引擎，按作业特征动态选择采集器 |
| **工程** | C++ / CMake / systemd / 统一 RPM，AlmaLinux 9，Apache-2.0 |
| **验证** | IHEP 生产节点实测；256 核、251 个 HTCondor 作业时 CPU < 0.15%、RSS ~145 MB |

<p align="center">
  <a href="https://github.com/joblens-org/JobLens"><img src="https://img.shields.io/badge/源码-181717?style=flat-square&logo=github&logoColor=white" alt="source"></a>
  <a href="https://github.com/joblens-org/JobLens/blob/main/doc/api_documentation.md"><img src="https://img.shields.io/badge/API_文档-0EA5E9?style=flat-square" alt="api docs"></a>
  <a href="https://github.com/joblens-org/JobLens/blob/main/doc/joblens_simplest_deployable_suite.md"><img src="https://img.shields.io/badge/部署套件-22C55E?style=flat-square" alt="deployment"></a>
  <a href="https://github.com/joblens-org/JobLens/releases"><img src="https://img.shields.io/badge/Releases-A78BFA?style=flat-square" alt="releases"></a>
</p>

---

## 🧪 在研究

> 当前处于方法梳理、测量契约与文献基线阶段，尚无实验结论。

| 🧠 工作进度条件化的批作业性能画像 | 🧬 真实画像驱动的 what-if 仿真 |
|:---|:---|
| 面向反复运行的 HTC 作业，研究「已完成多少工作」如何进入作业画像，以及它能否在同等启动延迟预算下改善剩余时长预测与错峰决策。关注工作、环境与响应的分离，以及信息可得时刻对预测的约束。 | 用采集到的作业画像驱动 SimGrid / WRENCH 一类的仿真，评估调度与资源配置策略，让画像成为可校准的仿真输入，而不是另建一套脱离测量的模型。 |
| `status: in progress` · `reading: 121 PDFs / 29 papers` | `status: in progress` · `prototype: symbiotic PoC` |

---

## 🧰 技术栈

<p align="center">
  <img src="https://skillicons.dev/icons?i=cpp,python,bash,linux,cmake,elasticsearch,kafka,prometheus,docker,kubernetes,fastapi,vue&theme=dark&perline=12" alt="tech stack">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/eBPF-1F425F?style=flat-square" alt="eBPF">
  <img src="https://img.shields.io/badge/HTCondor-7D3C98?style=flat-square" alt="HTCondor">
  <img src="https://img.shields.io/badge/Slurm-2E86C1?style=flat-square" alt="Slurm">
  <img src="https://img.shields.io/badge/cgroup-4A4A4A?style=flat-square" alt="cgroup">
  <img src="https://img.shields.io/badge/RPM-F43F5E?style=flat-square&logo=redhat&logoColor=white" alt="RPM">
  <img src="https://img.shields.io/badge/Elasticsearch-005571?style=flat-square&logo=elasticsearch&logoColor=white" alt="Elasticsearch">
  <img src="https://img.shields.io/badge/Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white" alt="Kafka">
  <img src="https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white" alt="Prometheus">
</p>

---

## 📈 GitHub 数据

<p align="center">
  <img height="168" src="https://github-readme-stats.vercel.app/api?username=nowzycc&show_icons=true&include_all_commits=true&count_private=true&bg_color=0B1020&title_color=22D3EE&icon_color=A78BFA&text_color=C7D2FE&border_color=1F2A44" alt="GitHub stats">
  <img height="168" src="https://github-readme-stats.vercel.app/api/top-langs/?username=nowzycc&layout=compact&langs_count=8&bg_color=0B1020&title_color=22D3EE&text_color=C7D2FE&border_color=1F2A44" alt="top languages">
</p>

<p align="center">
  <img src="https://streak-stats.demolab.com?user=nowzycc&background=0B1020&border=1F2A44&stroke=22D3EE&ring=A78BFA&fire=F472B6&currStreakLabel=22D3EE&sideLabels=C7D2FE&dates=8B95B5" alt="GitHub streak">
</p>

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/nowzycc/nowzycc/output/github-snake-dark.svg">
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/nowzycc/nowzycc/output/github-snake.svg">
    <img src="https://raw.githubusercontent.com/nowzycc/nowzycc/output/github-snake.svg" alt="contribution snake" width="100%">
  </picture>
</p>

---

## 🌱 最近动态

| 时间 | 进展 |
|:---|:---|
| `2026-10` | 梳理 JobLens 事件信号路径，规划作业粒度的事件采集与写出链路 |
| `2026-10` | 完成工作进度条件化画像的文献基线与学习综述（121 篇 PDF，29 篇精读） |
| `2026-09` | JobLens v0.3.6 发布：拆分采集器调度、统一 RPM 打包、完善 Trigger 生命周期 |
| `2026-08` | JobLens 完成 IHEP 生产节点部署与资源开销验证 |

---

## 🤝 联系我

<p align="center">
  <a href="mailto:wangzhenyuan@ihep.ac.cn"><img src="https://img.shields.io/badge/Email-wangzhenyuan%40ihep.ac.cn-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="email"></a>
  <a href="https://github.com/nowzycc"><img src="https://img.shields.io/badge/GitHub-nowzycc-181717?style=for-the-badge&logo=github&logoColor=white" alt="github"></a>
  <a href="https://github.com/joblens-org/JobLens"><img src="https://img.shields.io/badge/Project-JobLens-22D3EE?style=for-the-badge&logo=github&logoColor=white" alt="JobLens"></a>
</p>

<details>
<summary><b>📊 编码时间 · WakaTime（每日自动更新）</b></summary>

<!--START_SECTION:waka-->
![Code Time](http://img.shields.io/badge/Code%20Time-537%20hrs%2037%20mins-blue?style=flat)

**🐱 My GitHub Data** 

> 📦 11.6 kB Used in GitHub's Storage 
> 
> 🏆 443 Contributions in the Year 2026
> 
> 🚫 Not Opted to Hire
> 
> 📜 6 Public Repositories 
> 
> 🔑 4 Private Repositories
> 
**I'm a Night 🦉** 

```text
🌞 Morning                48 commits          ██░░░░░░░░░░░░░░░░░░░░░░░   09.90 % 
🌆 Daytime                161 commits         ████████░░░░░░░░░░░░░░░░░   33.20 % 
🌃 Evening                239 commits         ████████████░░░░░░░░░░░░░   49.28 % 
🌙 Night                  37 commits          ██░░░░░░░░░░░░░░░░░░░░░░░   07.63 % 
```
📅 **I'm Most Productive on Tuesday** 

```text
Monday                   87 commits          ████░░░░░░░░░░░░░░░░░░░░░   17.94 % 
Tuesday                  105 commits         █████░░░░░░░░░░░░░░░░░░░░   21.65 % 
Wednesday                48 commits          ██░░░░░░░░░░░░░░░░░░░░░░░   09.90 % 
Thursday                 75 commits         ████░░░░░░░░░░░░░░░░░░░░░   15.46 % 
Friday                   31 commits         ██░░░░░░░░░░░░░░░░░░░░░░░   06.39 % 
Saturday                 83 commits         ████░░░░░░░░░░░░░░░░░░░░░   17.11 % 
Sunday                   56 commits         ███░░░░░░░░░░░░░░░░░░░░░░   11.55 % 
```


📊 **This Week I Spent My Time On** 

```text
🕑︎ Time Zone: Asia/Hong_Kong

💬 Programming Languages: 
Markdown                 3 hrs 25 mins       █████████░░░░░░░░░░░░░░░░   35.68 % 
Other                    3 hrs 1 min         ████████░░░░░░░░░░░░░░░░░   31.41 % 
HTML                     1 hr 23 mins        ████░░░░░░░░░░░░░░░░░░░░░   14.40 % 
Python                   58 mins             ███░░░░░░░░░░░░░░░░░░░░░░   10.12 % 
C++                      22 mins             █░░░░░░░░░░░░░░░░░░░░░░░░   03.83 % 

🔥 Editors: 
VS Code                  4 hrs 57 mins       █████████████░░░░░░░░░░░░   51.58 % 
Opencode Cli             2 hrs 47 mins       ███████░░░░░░░░░░░░░░░░░░   28.99 % 
Codex Vscode             1 hr 45 mins        █████░░░░░░░░░░░░░░░░░░░░   18.24 % 
OpenCode                 6 mins              ░░░░░░░░░░░░░░░░░░░░░░░░░   01.19 % 

💻 Operating System: 
WSL                      9 hrs 37 mins       █████████████████████████   100.00 % 
```

**I Mostly Code in Python** 

```text
Python                   10 repos            ███████████░░░░░░░░░░░░░░   45.45 % 
C                        2 repos             ██░░░░░░░░░░░░░░░░░░░░░░░   09.09 % 
Makefile                 1 repo              █░░░░░░░░░░░░░░░░░░░░░░░░   04.55 % 
Jupyter Notebook         1 repo              █░░░░░░░░░░░░░░░░░░░░░░░░   04.55 % 
C++                      1 repo              █░░░░░░░░░░░░░░░░░░░░░░░░   04.55 % 
```



**Timeline**

![Lines of Code chart](https://raw.githubusercontent.com/nowzycc/nowzycc/main/assets/bar_graph.png)


 Last Updated on 19/10/2026 23:08:50 UTC
<!--END_SECTION:waka-->

</details>

<div align="center">
  <img src="https://raw.githubusercontent.com/nowzycc/nowzycc/main/assets/footer.svg" alt="Measure · Profile · Simulate" width="100%">
</div>
