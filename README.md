<!-- ============================================================ -->
<!--  Profile README — goes in the Quentintnrl/Quentintnrl repo   -->
<!-- ============================================================ -->

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&height=200&color=0:70C1B3,100:3C4F76&text=Quentin%20Tennerel&fontColor=ffffff&fontSize=50&fontAlignY=38&desc=Backend%20%C2%B7%20DevOps%20%C2%B7%20Co-founder%20of%20Mairie360&descAlignY=58&descSize=18" alt="Quentin Tennerel" />

<a href="https://github.com/Quentintnrl">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=20&pause=1200&color=70C1B3&center=true&vCenter=true&width=640&lines=Building+APIs+in+Rust+%F0%9F%A6%80;Microservices+%C2%B7+Kubernetes+%C2%B7+GitOps;Modernizing+French+town+halls+%F0%9F%8F%9B%EF%B8%8F;Now+building%3A+an+AI+agent+orchestrator+%F0%9F%A4%96" alt="Typing SVG" />
</a>

<br/>

<a href="https://linkedin.com/in/quentin-tennerel-0367621b7"><img src="https://img.shields.io/badge/LinkedIn-Quentin%20Tennerel-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" /></a>
<a href="https://mairie360.fr"><img src="https://img.shields.io/badge/mairie360.fr-Website-70C1B3?style=for-the-badge&logo=googlechrome&logoColor=white" /></a>
<a href="https://github.com/mairie360"><img src="https://img.shields.io/badge/GitHub-Mairie360-383F51?style=for-the-badge&logo=github&logoColor=white" /></a>
<img src="https://komarev.com/ghpvc/?username=Quentintnrl&style=for-the-badge&color=3C4F76&label=VIEWS" />

</div>

---

## 👋 About me

Final-year student at **Epitech** (Master's-level "Grande École" program, graduating June 2027) and **co-founder of [Mairie360](https://mairie360.fr)**, a SaaS platform that helps small French municipalities modernize how they work.

I'm into **backend** and **DevOps**: designing solid APIs, splitting platforms into services, and **automating everything that can be automated**, from commit to production.

```rust
struct Quentin {
    role:      &'static str,
    based_in:  &'static str,
    focus:     [&'static str; 3],
    building:  &'static str,
    learning:  [&'static str; 2],
}

const ME: Quentin = Quentin {
    role:     "Backend / DevOps · co-founder @ Mairie360",
    based_in: "Nantes area, France 🇫🇷",
    focus:    ["Rust APIs", "Microservices on Kubernetes", "CI/CD, GitOps & IaC"],
    building: "An orchestrator for AI coding agents",
    learning: ["MCP & AI agents", "中文 (Mandarin)"],
};
```

<!-- ✏️ Adjust this line to your current search -->
> 🔎 **Open to opportunities** in backend / DevOps (internship or fixed-term contract), in Paris, Nantes or remote. [Reach out on LinkedIn](https://linkedin.com/in/quentin-tennerel-0367621b7)!

---

## 🤖 Currently building: an AI agent orchestrator

A **control plane for AI coding agents**, in the spirit of Kubernetes: it doesn't do the work itself, it manages the flow between agents that take a project **from spec to production**.

- 🧩 **One agent per role** (specs, dev, PR, CI, merge, prod monitoring), so no single agent tunnel-visions on its own feature
- 🔌 **Bring your own agents and tools**: prebuilt agents or your own, with your ticketing, CI and observability stack (Jira, Linear…). Nothing is imposed
- 🚦 **Coordination built in**: when several agents hit the same unexpected issue, it's raised once in a shared registry and becomes a single ticket, and blocked work resumes automatically with updated context once it's fixed
- 👀 **Humans only when needed**: runs day and night, calls a human only when the AI decides one is required, and works the same way whether you're coding by hand with Claude Code or letting the agents run
- 📈 **Telemetry, not opinions**: tracks where and why agents get stuck (real work vs. waiting on the model vs. waiting on a human), with end-to-end traceability. You keep your own choices of tools and models

> 🛠️ Currently in the design phase.

---

## 🏛️ Flagship project: Mairie360

<table>
<tr>
<td width="60%" valign="top">

**Mairie360** gives municipal staff, elected officials and department heads a single workspace: **dashboard, projects, calendar, messaging, approval workflows and e-learning**. Everything runs in the browser.

- 🧪 **MVP in pilot** with two partner municipalities on Réunion Island
- 🔐 **Sovereign by design**: a dedicated instance per municipality instead of a shared multi-tenant database
- 👥 Team of 4 developers, spread across mainland France and Réunion
- 🌐 Open source: [github.com/mairie360](https://github.com/mairie360)

**My role:** fullstack, with a strong focus on **Rust backend and DevOps**. I designed the delivery pipeline, the CI/CD and the infrastructure.

</td>
<td width="40%" valign="top">

**At a glance**

| | |
|---|---|
| 📦 Repositories | 38 |
| 🦀 APIs | Rust |
| 🧩 BFFs | Node.js / TS |
| 🖥️ Frontends | Next.js (SSR) |
| ☸️ Runtime | Kubernetes + Argo CD |
| 🏗️ IaC | Terraform + Ansible |
| 🌍 Environments | dev · staging · prod |

</td>
</tr>
</table>

<details>
<summary><b>🔧 Architecture and delivery pipeline</b></summary>

<br/>

```mermaid
flowchart LR
    subgraph IaC["Provisioning"]
        T[Terraform<br/>machines] --> AN[Ansible<br/>configuration]
    end
    subgraph Client["One instance per municipality"]
        F[Next.js frontends] --> B[Node.js BFFs]
        B --> A[Rust APIs]
        A --> D[(PostgreSQL<br/>Liquibase migrations)]
    end
    AN --> Client
    N[n8n<br/>release orchestration] --> G[GitHub Actions<br/>tests · security · perf]
    G -->|Docker images| P[GitHub Packages]
    P --> AR[Argo CD<br/>GitOps]
    AR --> Client
```

**What I built:**

- **Infrastructure as Code**: machines provisioned with **Terraform** and configured with **Ansible**
- **GitOps with Argo CD**: one Argo CD per environment group, each municipality on its own machines
- **Controlled promotion**: `dev-sha` → `staging-sha` → `vX.Y.Z`, with manual gates at the critical steps
- **Global versioning**: each release pins a tested combination of every service, so a municipality never has to manage compatibility between services
- **CI-driven quality**: unit, integration and e2e tests, [Newman](https://github.com/postmanlabs/newman), [k6](https://k6.io) (load), [OWASP ZAP](https://www.zaproxy.org) (DAST), [Semgrep](https://semgrep.dev), `cargo audit`, `npm audit`, accessibility checks
- **Dependencies kept up to date** by [Renovate](https://github.com/renovatebot/renovate)
- **Release pipeline orchestrated by n8n**, step by step (DB → APIs → BFFs → frontends), and restartable from any step
- **MCP servers** (in progress) to expose the platform to AI agents running in n8n workflows

</details>

---

## 🛠️ Tech stack

<div align="center">

**Languages**<br/>
<img src="https://skillicons.dev/icons?i=rust,java,ts,js,go,python,php&perline=7" />

**Backend & Frontend**<br/>
<img src="https://skillicons.dev/icons?i=nodejs,nextjs,react,postgres,redis,graphql&perline=6" />

**DevOps & Cloud**<br/>
<img src="https://skillicons.dev/icons?i=docker,kubernetes,terraform,ansible,githubactions,linux,nginx,aws,gcp,azure&perline=10" />

**Tools**<br/>
<img src="https://skillicons.dev/icons?i=git,github,postman,figma,vscode&perline=5" />
<img src="https://img.shields.io/badge/n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white" height="40" />
<img src="https://img.shields.io/badge/Argo%20CD-EF7B4D?style=flat-square&logo=argo&logoColor=white" height="40" />

</div>

---

## 🚀 Other projects

| Project | Description | Stack |
|---|---|---|
| 🏆 **EPIck'em** | Tournament and prediction platform, Epitech team project with 3 people (2026–2027) | Web · fullstack |

---

## 📊 Activity

<div align="center">

<img height="170" src="https://github-readme-stats.vercel.app/api?username=Quentintnrl&show_icons=true&count_private=true&include_all_commits=true&hide_border=true&bg_color=00000000&title_color=70C1B3&icon_color=3C4F76&text_color=8b949e&rank_icon=github" />
<img height="170" src="https://streak-stats.demolab.com?user=Quentintnrl&hide_border=true&background=00000000&ring=70C1B3&fire=3C4F76&currStreakLabel=70C1B3&sideLabels=8b949e&dates=8b949e&currStreakNum=8b949e&sideNums=8b949e" />

<img width="95%" src="https://github-readme-activity-graph.vercel.app/graph?username=Quentintnrl&bg_color=00000000&color=8b949e&line=70C1B3&point=3C4F76&area=true&hide_border=true" />

</div>

---

<div align="center">

**🏆 GitHub achievements:** Pair Extraordinaire · Pull Shark ×3 · Quickdraw · YOLO

<br/>

*"A good tool fades into the background, so staff can focus on citizens."*

<img src="https://capsule-render.vercel.app/api?type=waving&height=100&section=footer&color=0:70C1B3,100:3C4F76" />

</div>
