<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/nowzycc/nowzycc/main/assets/hero-dark.svg">
    <img src="https://raw.githubusercontent.com/nowzycc/nowzycc/main/assets/hero-light.svg" alt="Nagato Hikari — job-native observability for HTC/HPC" width="100%">
  </picture>
</p>

## About

I work on job-level observability and performance analysis for HTC/HPC clusters. The goal is to move monitoring from the node down to the job: making each job's resource use, I/O behavior and work progress measurable, comparable and reusable.

PhD researcher at the Computing Center, Institute of High Energy Physics, Chinese Academy of Sciences (CC.IHEP.CAS), Beijing.

```console
$ joblens --whoami
role      PhD researcher @ CC.IHEP.CAS
focus     job-level observability · workload profiling · what-if simulation
stack     eBPF / C++ / HTCondor / Elasticsearch
status    building job-grained event collection
```

## Work

### JobLens

[JobLens](https://github.com/joblens-org/JobLens) is a job-native observability system for HTC/HPC clusters. Agents on compute nodes collect with eBPF and attribute resource data to individual jobs; a unified control plane handles on-demand collection and query.

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/nowzycc/nowzycc/main/assets/joblens-flow-dark.svg">
    <img src="https://raw.githubusercontent.com/nowzycc/nowzycc/main/assets/joblens-flow-light.svg" alt="JobLens data flow: compute nodes to agent, writers, TAP" width="100%">
  </picture>
</p>

| Area | Detail |
|:---|:---|
| **Scope** | CPU, memory, syscall I/O, file metadata, network; power (RAPL/IPMI), GPU (NVML) |
| **Attribution** | HTCondor, Slurm, cgroup; PID → job mapping and lifecycle events |
| **Output** | File, Elasticsearch, Kafka, Prometheus; routed per collector |
| **Control plane** | Trigger (Flask): REST API and Lua rule engine for admission and collector selection |
| **Delivery** | C++ / CMake / systemd / unified RPM; AlmaLinux 9; Apache-2.0 |
| **Production** | Validated at IHEP: 256 cores, 251 HTCondor jobs, CPU < 0.15%, RSS ~145 MB |

[Source](https://github.com/joblens-org/JobLens) · [API](https://github.com/joblens-org/JobLens/blob/main/doc/api_documentation.md) · [Deployment](https://github.com/joblens-org/JobLens/blob/main/doc/joblens_simplest_deployable_suite.md) · [Releases](https://github.com/joblens-org/JobLens/releases)

## Research

Two threads, both in progress. No experimental results yet.

### Work-progress-conditioned profiling

For recurring HTC workloads, I study how "how much work has been completed" can enter a job profile, and whether it improves remaining-time prediction and start-time staggering under the same delay budget. The work separates demand, environment and response, and respects what information is available at each point in time.

### Profile-driven what-if simulation

Using collected profiles to drive SimGrid / WRENCH-style simulation, so that profiles become calibrated simulation inputs rather than a separate, measurement-free model.

## Stack

| Area | Detail |
|:---|:---|
| **Languages** | C++ · Python · Bash |
| **Systems** | eBPF · Linux · CMake · systemd |
| **Scheduling** | HTCondor · Slurm · cgroup |
| **Data** | Elasticsearch · Kafka · Prometheus |
| **Services** | FastAPI · Vue · Docker · Kubernetes |

## GitHub

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api?username=nowzycc&show_icons=true&hide_rank=true&hide_border=true&bg_color=0D1117&title_color=F0F6FC&icon_color=8B949E&text_color=8B949E&cache_seconds=86400">
    <img height="170" src="https://github-readme-stats.vercel.app/api?username=nowzycc&show_icons=true&hide_rank=true&hide_border=true&bg_color=FFFFFF&title_color=111827&icon_color=6B7280&text_color=6B7280&cache_seconds=86400" alt="GitHub stats">
  </picture>
</p>

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://streak-stats.demolab.com?user=nowzycc&theme=dark&background=0D1117&border=0D1117&stroke=21262D&ring=F0F6FC&fire=F0F6FC&currStreakNum=F0F6FC&sideNums=F0F6FC&currStreakLabel=8B949E&sideLabels=8B949E&dates=8B949E">
    <img height="170" src="https://streak-stats.demolab.com?user=nowzycc&theme=default&background=FFFFFF&border=FFFFFF&stroke=E5E7EB&ring=111827&fire=111827&currStreakNum=111827&sideNums=111827&currStreakLabel=6B7280&sideLabels=6B7280&dates=6B7280" alt="GitHub streak">
  </picture>
</p>

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/nowzycc/nowzycc/output/github-snake-dark.svg">
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/nowzycc/nowzycc/output/github-snake.svg">
    <img src="https://raw.githubusercontent.com/nowzycc/nowzycc/output/github-snake.svg" alt="Contribution graph" width="100%">
  </picture>
</p>

## Contact

[Email](mailto:wangzhenyuan@ihep.ac.cn) · [GitHub](https://github.com/nowzycc) · [JobLens](https://github.com/joblens-org/JobLens)

<details>
<summary>WakaTime stats</summary>

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

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/nowzycc/nowzycc/main/assets/footer-dark.svg">
    <img src="https://raw.githubusercontent.com/nowzycc/nowzycc/main/assets/footer-light.svg" alt="Measure, profile, simulate" width="100%">
  </picture>
</p>
