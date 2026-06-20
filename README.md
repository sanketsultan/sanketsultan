<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:1f6feb,100:58a6ff&height=120&section=header&text=Sanket%20Sultan&fontSize=42&fontColor=ffffff&fontAlignY=65&animation=fadeIn" width="100%" />

<a href="https://readme-typing-svg.demolab.com">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=20&pause=1200&color=58A6FF&center=true&vCenter=true&width=760&lines=Platform+Engineer+%26+SRE;Kubernetes+%7C+Cloud+Architecture+%7C+Security+%7C+Observability;Well-Architected+by+default%2C+not+by+audit;Reliability+is+a+feature%2C+not+an+afterthought;Cloud-native+from+the+ground+up" alt="Typing SVG" />
</a>

<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/sanketsultan/)
[![Medium](https://img.shields.io/badge/Medium-000000?style=for-the-badge&logo=medium&logoColor=white)](https://medium.com/@sanketsultan1997)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:sanketsultanwork@gmail.com)
[![Profile Views](https://komarev.com/ghpvc/?username=sanketsultan&style=for-the-badge&color=1f6feb&label=PROFILE+VIEWS)](https://github.com/sanketsultan)

</div>

---

## `$ whoami`

```yaml
name:      Sanket Sultan
role:      Platform Engineer · SRE · Staff-track
location:  Rotterdam, Netherlands
visa:      HSM -- open to relocation

lens:      I evaluate every system against six questions:
           Is it operationally excellent?   # automate toil, safe deploys, fast feedback
           Is it reliable?                  # SLOs, error budgets, chaos engineering
           Is it secure?                    # zero trust, least privilege, shift left
           Is it performing?                # latency budgets, capacity planning
           Is it cost-efficient?            # right-size before scaling, tag and attribute
           Is it sustainable?               # less compute for the same throughput

currently_building:
  intelligent-sre-agent:
    what: AI-native SRE platform -- anomaly detection, RCA, auto-healing
    stack: FastAPI · MCP · Claude API · Kubernetes · Prometheus · PostgreSQL
    why: "The best incident is the one that heals itself"

currently_thinking_about:
  - eBPF for kernel-level observability without instrumentation overhead
  - Supply chain security -- SBOM, Sigstore, admission control at registry layer
  - Where LLMs fit in incident response and where they introduce risk
  - Cost-aware architecture -- treating cloud spend as an engineering constraint
```

---

## How I Design Systems

Most platform problems look like Kubernetes problems. They are not. They are ownership gaps and missing feedback loops dressed up in YAML.

I think in pillars. Every architecture decision is evaluated across reliability, security, performance, cost, and operational excellence -- as constraints from the start, not a checklist at the end.

**Operational Excellence.** Safe and fast change is the goal. GitOps pipelines with OPA policy gates, automated testing before every production change, blue-green deployments so rollback is a non-event. I measure health through deployment frequency and change failure rate, not just uptime.

**Reliability.** I build for failure, not against it. SLIs and SLOs are defined before any alerting is written. Error budgets give teams a mechanism to prioritise reliability work. Quarterly game days validate that recovery plans actually work under pressure. When a failure pattern recurs across services, I fix the class of problem.

**Security.** Security is a property of the architecture, not a layer added afterward. Zero-trust networking with mTLS between services. Least-privilege IAM at the role level. Secrets through Vault with dynamic credentials. OPA/Gatekeeper at admission time so misconfigurations never reach production. Supply chain controls at the image layer with signing and scanning gates.

**Performance and Cost.** Right-sizing is not a one-time task. HPA and VPA based on real usage data, cgroup-level profiling for memory and CPU, latency budgets defined alongside SLOs. Cost is attributed per team and service -- an over-provisioned cluster is a noisy neighbour waiting to happen.

**Kubernetes specifically.** Multi-tenancy with Resource Quotas, Limit Ranges, and network policies per namespace. Cilium for eBPF networking, Istio for mTLS and traffic management. Admission control with pod security standards and seccomp profiles to reduce the kernel attack surface. Velero for backup with tested failover, not assumed.

---

## Linux and the Lower Layers

Kubernetes runs on Linux. When something breaks at the container boundary, that is where I go.

I troubleshoot using `strace` to trace system calls on misbehaving processes, `perf` for CPU profiling and hot path analysis, and `/proc` and `cgroups` to understand what the kernel actually sees versus what the container runtime reports. Memory issues get `vmstat`, `smaps`, and `pmap` before any application-level change is made. Networking issues start with `ss`, `tcpdump`, and `conntrack` -- not with a Kubernetes manifest.

The habit started early. Before cloud-native tooling abstracted most of it, I was managing bare Linux systems in production -- tuning `systemd` unit files, writing `bash` automation for operational tasks, diagnosing OOM kills from kernel logs. That foundation is what makes Kubernetes debugging fast. When a pod is OOM-killed or a liveness probe is misfiring, I know where to look before reaching for `kubectl`.

A few things I find genuinely interesting at this level:
- How cgroup v2 changed the memory accounting model and what that means for container resource limits
- Why `pid` namespace isolation matters for signal handling in multi-process containers
- How eBPF is moving observability from the application layer down to the kernel without the overhead of traditional instrumentation

---

## An Incident That Changed How I Think

We had a recurring set of production alerts that looked unrelated. Different services, different teams, different times. Each one got patched individually.

I pulled the last 12 post-mortems and mapped the failure modes. 70% traced back to the same root cause: services did not handle transient upstream failures gracefully. No retry, no backoff, no jitter. Under load, failures cascaded.

The instinct is to fix each service. The better move is to fix the pattern. I built a shared backoff-with-jitter library, documented the failure class, and got it adopted across 8 services in two weeks. The alert class disappeared.

That changed how I read post-mortems. I stopped asking what broke and started asking what class of problem this is and how many other services share the same exposure.

---

## Impact That Shipped

<div align="center">

| Pillar | Problem | Solution | Result |
|:---|:---|:---|:---:|
| Reliability | 30-min mean time to detect | Prometheus + Grafana SLO stack from scratch | MTTD down to 6 min |
| Reliability | Alert fatigue, no SLO framework | Multi-window burn rate alerting across 20+ services | On-call pages down 40% |
| Reliability | 70% of incidents, same root cause | Shared backoff-with-jitter library | 8 services fixed, pattern gone |
| Security | No policy enforcement at deploy time | OPA/Gatekeeper + GitLab CI gates | Zero misconfigs reaching production |
| Security | Secrets in env vars and config maps | Vault + External Secrets Operator | Dynamic, rotated credentials across all services |
| Operational Excellence | 2-day provisioning, config drift | Reusable Terraform modules, 100% adopted voluntarily | Down to 30 minutes |
| Operational Excellence | Noisy neighbour in shared clusters | Resource Quotas + Limit Ranges per namespace | Pod restarts down 45% |
| Cost | Cloud spend growing without visibility | Service-level cost attribution + right-sizing | Costs down 30% |
| Reliability | Untested DR plans | Quarterly game days, Velero backup strategy | RTO/RPO validated in production |

</div>

---

## Certifications

<div align="center">

[![CKA](https://img.shields.io/badge/CKA-Certified%20Kubernetes%20Administrator-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)](https://www.cncf.io/certification/cka/)
[![AWS](https://img.shields.io/badge/AWS-Solutions%20Architect%20Associate-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white)](https://aws.amazon.com/certification/certified-solutions-architect-associate/)
[![Terraform](https://img.shields.io/badge/HashiCorp-Terraform%20Associate-7B42BC?style=for-the-badge&logo=terraform&logoColor=white)](https://www.hashicorp.com/certification/terraform-associate)
[![MSc](https://img.shields.io/badge/MSc-Cloud%20Computing%20--%20NCI%20Dublin-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)](https://www.ncirl.ie/)

</div>

---

## Tech

**Kubernetes and Cloud Native**

![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Helm](https://img.shields.io/badge/Helm-0F1689?style=flat-square&logo=helm&logoColor=white)
![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=flat-square&logo=argo&logoColor=white)
![Kustomize](https://img.shields.io/badge/Kustomize-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Velero](https://img.shields.io/badge/Velero-00C4CC?style=flat-square)

**Observability**

![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)
![OpenTelemetry](https://img.shields.io/badge/OpenTelemetry-000000?style=flat-square&logo=opentelemetry&logoColor=white)
![Datadog](https://img.shields.io/badge/Datadog-632CA6?style=flat-square&logo=datadog&logoColor=white)
![Alertmanager](https://img.shields.io/badge/Alertmanager-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![CloudWatch](https://img.shields.io/badge/CloudWatch-FF4F8B?style=flat-square&logo=amazonaws&logoColor=white)

**Security**

![Vault](https://img.shields.io/badge/Vault-FFEC6E?style=flat-square&logo=vault&logoColor=black)
![OPA](https://img.shields.io/badge/OPA%2FGatekeeper-4B5563?style=flat-square)
![Istio](https://img.shields.io/badge/Istio-466BB0?style=flat-square&logo=istio&logoColor=white)
![Cilium](https://img.shields.io/badge/Cilium-F8C517?style=flat-square&logo=cilium&logoColor=black)

**Infrastructure and GitOps**

![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![GitLab CI](https://img.shields.io/badge/GitLab_CI-FC6D26?style=flat-square&logo=gitlab&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat-square&logo=jenkins&logoColor=white)

**Cloud**

![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![Azure](https://img.shields.io/badge/Azure-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)

**Linux**

![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white)

**Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white)

---

## `intelligent-sre-agent`

<div align="center">

[![intelligent-sre-agent](https://github-readme-stats.vercel.app/api/pin/?username=sanketsultan&repo=intelligent-sre-agent&theme=github_dark&hide_border=true&title_color=58a6ff&icon_color=58a6ff)](https://github.com/sanketsultan/intelligent-sre-agent)

</div>

**The problem.** SREs follow the same script for toil: find the spike, restart the pod, write the ticket. That loop is automatable. The hard part is making it safe in production.

**What I built.** A modular AI-native SRE platform where anomaly detection, root cause analysis, correlation, and healing are independent layers you can extend without touching the core.

```
Prometheus anomaly detected
        |
Claude API analyzes context and recent events
        |
Correlation engine checks blast radius
        |
Healing action executed with guardrails
        |
PostgreSQL audit log + human escalation if uncertain
```

**Decisions that mattered.**
- MCP gives the LLM bounded, structured access to cluster state. Least privilege applied to AI tooling.
- Healing only fires when confidence score and blast radius check both pass. Automation with a circuit breaker.
- Every action is logged before execution. Auditability is not optional in production.

---

## Writing

I write about SLO design, Kubernetes internals, cloud-native security, and Well-Architected patterns in practice.

[Read on Medium](https://medium.com/@sanketsultan1997)

---

## How I Work

Platform engineers influence without authority. I cannot force adoption of anything -- which means the work has to be good enough that people choose it.

I spend as much time understanding what product teams need as building tooling. I run workshops, treat adoption rate as the primary platform quality metric, and when I disagree on a technical direction I say so with data and then commit to the decision the team makes.

The Kubernetes troubleshooting workshops I ran reduced escalations to the platform team by 30%. The goal was not to create workshop dependency. It was to eliminate that class of escalation entirely.

---

## GitHub Activity

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=sanketsultan&show_icons=true&theme=github_dark&hide_border=true&title_color=58a6ff&icon_color=58a6ff&include_all_commits=true&count_private=true&rank_icon=github" height="170"/>
&nbsp;&nbsp;
<img src="https://github-readme-streak-stats.herokuapp.com/?user=sanketsultan&theme=github-dark-blue&hide_border=true&ring=58a6ff&fire=ff6b35&currStreakLabel=58a6ff" height="170"/>

</div>

<div align="center">

<img src="https://github-readme-activity-graph.vercel.app/graph?username=sanketsultan&theme=github-compact&hide_border=true&area=true&color=58a6ff&line=58a6ff&point=ffffff&area_color=1f6feb" width="100%" />

</div>

<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/sanketsultan/sanketsultan/output/github-contribution-grid-snake-dark.svg" />
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/sanketsultan/sanketsultan/output/github-contribution-grid-snake.svg" />
    <img alt="contribution snake" src="https://raw.githubusercontent.com/sanketsultan/sanketsultan/output/github-contribution-grid-snake.svg" />
  </picture>
</div>

---

<div align="center">

The best platform is the one your engineers forget exists.

<br/>

Open to Staff / Principal Platform Engineer · SRE · Cloud Architect roles in the Netherlands or remote.

<br/>

[sanketsultanwork@gmail.com](mailto:sanketsultanwork@gmail.com) &nbsp;·&nbsp; [LinkedIn](https://linkedin.com/in/sanketsultan/) &nbsp;·&nbsp; [GitHub](https://github.com/sanketsultan)

</div>

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:58a6ff,50:1f6feb,100:0d1117&height=80&section=footer" width="100%" />

</div>
