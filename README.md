<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:1f6feb,100:58a6ff&height=120&section=header&text=Sanket%20Sultan&fontSize=42&fontColor=ffffff&fontAlignY=65&animation=fadeIn" width="100%" />

<a href="https://readme-typing-svg.demolab.com">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=20&pause=1200&color=58A6FF&center=true&vCenter=true&width=700&lines=Platform+Engineer+%26+SRE;Kubernetes+%7C+Security+%7C+Observability+%7C+Cloud;I+fix+systems%2C+not+just+symptoms;Building+platforms+devs+forget+exist" alt="Typing SVG" />
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
name:     Sanket Sultan
role:     Senior Platform Engineer · SRE
location: Rotterdam, Netherlands
visa:     HSM -- open to relocation

what I do:
  - Run multi-tenant Kubernetes platforms across AWS and Azure at scale
  - Design reliability from scratch -- SLIs, SLOs, error budgets, game days
  - Build observability that catches problems before customers do
  - Secure cloud-native infrastructure -- zero trust, PCI-DSS, policy as code
  - Optimize cloud costs -- attribution, rightsizing, spot strategy
  - Go down to Linux when Kubernetes is not the real problem

belief:   If the same incident happens twice, the system needs fixing -- not the ticket
```

---

## What I work with

**Kubernetes and Platform**

![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Helm](https://img.shields.io/badge/Helm-0F1689?style=flat-square&logo=helm&logoColor=white)
![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=flat-square&logo=argo&logoColor=white)
![Kustomize](https://img.shields.io/badge/Kustomize-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Velero](https://img.shields.io/badge/Velero-00C4CC?style=flat-square)
![HPA](https://img.shields.io/badge/HPA%2FVPA-326CE5?style=flat-square&logo=kubernetes&logoColor=white)

**Observability**

![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)
![OpenTelemetry](https://img.shields.io/badge/OpenTelemetry-000000?style=flat-square&logo=opentelemetry&logoColor=white)
![Datadog](https://img.shields.io/badge/Datadog-632CA6?style=flat-square&logo=datadog&logoColor=white)
![Alertmanager](https://img.shields.io/badge/Alertmanager-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![CloudWatch](https://img.shields.io/badge/CloudWatch-FF4F8B?style=flat-square&logo=amazonaws&logoColor=white)

**Security**

![Vault](https://img.shields.io/badge/Vault-FFEC6E?style=flat-square&logo=vault&logoColor=black)
![OPA](https://img.shields.io/badge/OPA%2FGatekeeper-4B5363?style=flat-square)
![Istio](https://img.shields.io/badge/Istio-466BB0?style=flat-square&logo=istio&logoColor=white)
![Cilium](https://img.shields.io/badge/Cilium-F8C517?style=flat-square&logo=cilium&logoColor=black)
![ExternalSecrets](https://img.shields.io/badge/External%20Secrets-4B5563?style=flat-square)

**Infrastructure and GitOps**

![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![GitLab CI](https://img.shields.io/badge/GitLab_CI-FC6D26?style=flat-square&logo=gitlab&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat-square&logo=jenkins&logoColor=white)

**Cloud**

![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![Azure](https://img.shields.io/badge/Azure-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)

**Languages and Linux**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)

---

## A few things I shipped

| What | How | Result |
|:---|:---|:---:|
| No visibility into service health | Prometheus + Grafana SLO stack, custom Python SLI exporters | MTTD 30 min down to 6 |
| Alerts firing but no one trusting them | Multi-window burn rate alerting, RED dashboards | Noise down 60%, 10+ breaches caught before customer impact |
| 70% of incidents, same root cause | One shared backoff-with-jitter library | Fixed 8 services, pattern eliminated |
| Infra taking 2 days to provision | Reusable Terraform modules, 100% voluntary adoption | Down to 30 minutes |
| No policy enforcement at deploy time | OPA/Gatekeeper at admission + GitLab CI gates | Zero misconfigs reaching production |
| Unstable shared clusters | Resource Quotas + Limit Ranges per namespace | Pod restarts down 45% |
| Untested recovery plans | Velero backup strategy + quarterly game days | RTO/RPO validated in production |
| Cloud costs growing untracked | Namespace-level cost attribution + rightsizing 20+ services | Down 30% |
| 10+ manual operational tasks per week | Scripted and automated across CI/CD, compute, networking | 8-10 hrs of team toil eliminated weekly |

---

## On Linux

Kubernetes runs on Linux. When something breaks at the container boundary, that is where I go.

`strace` for syscall tracing. `perf` for CPU hot paths. `cgroups` and `/proc` for what the kernel actually sees. `tcpdump` and `ss` before touching any manifest. `vmstat` and `smaps` for memory before any application-level change.

I managed bare Linux systems in production before containers were the default -- performance tuning, `systemd` service management, bash automation, OOM kill analysis from kernel logs. That foundation is what makes Kubernetes debugging fast. I know where to look before reaching for `kubectl`.

---

## Certifications

<div align="center">

[![CKA](https://img.shields.io/badge/CKA-Kubernetes%20Administrator-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)](https://www.cncf.io/certification/cka/)
[![AWS](https://img.shields.io/badge/AWS-Solutions%20Architect-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white)](https://aws.amazon.com/certification/certified-solutions-architect-associate/)
[![Terraform](https://img.shields.io/badge/HashiCorp-Terraform%20Associate-7B42BC?style=for-the-badge&logo=terraform&logoColor=white)](https://www.hashicorp.com/certification/terraform-associate)
[![MSc](https://img.shields.io/badge/MSc-Cloud%20Computing%20NCI%20Dublin-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)](https://www.ncirl.ie/)

</div>

---

## Featured project

<div align="center">

[![intelligent-sre-agent](https://github-readme-stats.vercel.app/api/pin/?username=sanketsultan&repo=intelligent-sre-agent&theme=github_dark&hide_border=true&title_color=58a6ff&icon_color=58a6ff)](https://github.com/sanketsultan/intelligent-sre-agent)

</div>

An AI-native SRE platform for Kubernetes. Detects anomalies, finds root causes, and heals automatically -- with guardrails so it does not make things worse.

```
Prometheus detects anomaly
        |
Claude analyzes context + recent events
        |
Blast radius check
        |
Auto-heal: restart / scale / rollback
        |
Audit log + escalate if uncertain
```

Stack: `FastAPI · MCP · Claude API · Kubernetes client · Prometheus · PostgreSQL`

The interesting problem was not the automation. It was defining safe boundaries for automation in production.

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

Open to Staff Platform Engineer · SRE · Cloud Architect roles -- Netherlands or remote.

<br/>

[sanketsultanwork@gmail.com](mailto:sanketsultanwork@gmail.com) &nbsp;·&nbsp; [LinkedIn](https://linkedin.com/in/sanketsultan/) &nbsp;·&nbsp; [GitHub](https://github.com/sanketsultan)

</div>

<div align="center">
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:58a6ff,50:1f6feb,100:0d1117&height=80&section=footer" width="100%" />
</div>
