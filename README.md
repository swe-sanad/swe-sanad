```console
sanad@swe-pioneers:~$ whoami --verbose

  ┌────────────────────────────────────────────────────────────┐
  │  SANAD ALAROUSI                                            │
  │  software engineer · platforms, ERP & developer tooling    │
  └────────────────────────────────────────────────────────────┘

  role       platform lead @ SWE-Pioneers
             engineer      @ EXPORT119
             client delivery · ERPNext / Frappe
  focus      self-hosted multi-tenant platforms
             ERP implementation & custom Frappe apps
             Libyan payment-gateway integrations
             dev tooling (MCP servers for Claude Code)
  languages  python · dart · typescript · rust · shell
  infra      docker · traefik · postgres · minio
             prometheus · grafana · github actions
  location   Zawia, Libya
  status     ● open to interesting work
```

I build and run the boring parts that have to stay up: the edge proxy, the shared
database, the backups, the alert that fires at 3am. Most of my day is ERP work for
real businesses in Libya — and the platform underneath it that keeps a dozen
services online on hardware I own.

---

# `$ tree ~/portfolio`

> `🔒` marks commercial or client work — private source, happy to walk through it on a call.
> Everything else is public and linked.

## `01_platform/` — the thing everything else runs on

A single-tenant-per-client hosting platform on hardware I administer: edge routing and
TLS, one shared database and object store, monitoring, and a set of small Rust daemons
doing the privileged jobs.

| project | what it does | stack |
|---|---|---|
| **cloud-portal** `🔒` | Client self-service hosting portal — clients register, launch demos, start/stop their own containers, attach custom domains and see their billing; operators get a control panel over every tenant, subscription and invoice. The API container runs fully unprivileged (`cap_drop: ALL`, no docker socket, no sudo) and only *reads* state through a read-only socket proxy while *writing job rows*; one host worker drains that queue and re-authorizes every job against the owning client's label before it touches anything. Billing, dunning included. | `Django` `Django-Bolt` `React` `Rust` |
| **vps-infra** `🔒` | Infrastructure-as-code for the whole box — Traefik edge with automatic TLS, shared Postgres and MinIO, Prometheus/Grafana/Alertmanager, CrowdSec, container autoheal, and the provisioning scripts that onboard a new app. | `Shell` `Docker` |
| **swe-rs** `🔒` | Shared primitives every platform daemon links against — **std-only, zero external crates**, consumed as a submodule and path dependency. | `Rust` |
| **swe-deploy-bot** `🔒` | Deploy pipeline: a GitHub webhook forwarder plus a deploy receiver, so services ship themselves off a tag instead of me SSH-ing in. | `Rust` |
| **vps-builder** `🔒` | A self-hosted GitHub Actions runner written from scratch, so first-party CI builds on my own metal. | `Rust` |
| **scale-to-zero** `🔒` | Idle-container waker — demo stacks sleep when nobody's looking and wake on the first request. Cheap way to keep a dozen demos "always up". | `Rust` |
| **egress-proxy** `🔒` | Build-time egress filter, so untrusted student/guest builds can't phone home. | `Rust` |
| **swe-pioneers-mailcow** `🔒` | Self-hosted mail stack plugged in behind the same edge proxy. | `Shell` `Docker` |

## `02_erp/` — Frappe / ERPNext, where most of the revenue is

| project | what it does | stack |
|---|---|---|
| **[SWE-Pioneers/frappe](https://github.com/SWE-Pioneers/frappe)** | Public monorepo tracking our forks of the Frappe app ecosystem as submodules — the base every ERP customisation ships from. | `Python` |
| **frappe-sales_system_setup** `🔒` | Libyan omnichannel sell-stack for ERPNext v16 — POS + webshop + accounting, vertical profiles (grocery, clothing) and a baked-in bilingual chart of accounts. | `Python` |
| **books** `🔒` | Simple accounting on Frappe — offline desktop build (free) and hosted web (paid). Ported from Frappe Books. | `Python` |
| **frappe-mailbox** `🔒` | Custom app pairing email integration with Libyan payment gateways. | `Python` |
| **frappe-construction_ops** `🔒` | Project accounting and construction operations for a contracting client. | `Python` |
| **frappe-shariah_compliance** `🔒` | Shariah-compliance rules layered onto standard ERPNext accounting. | `Python` |
| **erpnext-swe-pioneers-blueprint** `🔒` | The blueprint every client bench is provisioned from — shared, dedicated and demo tiers off one definition. | `Python` |

## `03_fintech/` — getting paid, locally

| project | what it does | stack |
|---|---|---|
| **platform-payments** `🔒` | Payments service for the platform with a provider-registry abstraction over the Libyan gateways — **LYPay**, **Moamalat** and **Plutu** — so a new provider is a class, not a rewrite. Pay-first provisioning hangs off this. | `Python` |

## `04_products/` — apps and client platforms

| project | what it does | stack |
|---|---|---|
| **masayef** `🔒` | Chalet reservation platform delivered for a government youth ministry — public booking flow plus an operator back office. | `TypeScript` |
| **talky-manager** `🔒` | Local, offline voice-note transcription with open-source Whisper — bring an audio file, get LLM-ready transcripts. No cloud, no upload. | `Rust` |
| **vaky-trips** `🔒` | Trip/travel platform. | `TypeScript` |
| **Chatty-AI** `🔒` | Cross-platform AI chat client. | `Dart` `Flutter` |
| **home_bakery-system** `🔒` | ERPNext + Flutter for small bakeries — separate flows for owners, bakers and drivers. | `Dart` `Python` |
| **elections-prototype** `🔒` | Election-process prototype. | `Dart` `Flutter` |
| **saas** `🔒` | Earlier multi-tenant SaaS built on ASP.NET with a Flutter client. | `ASP.NET` `Flutter` |

## `05_oss/` — public, and free to take

| project | what it does | stack |
|---|---|---|
| **[LibreOffice-Claude-Connector](https://github.com/swe-sanad/LibreOffice-Claude-Connector)** ⭐2 | A `.oxt` extension plus a **161-tool MCP server** that lets Claude Code drive LibreOffice — read, write, format, chart and export Writer/Calc documents live on the user's screen. | `Python` |
| **[jdownloader-mcp](https://github.com/swe-sanad/jdownloader-mcp)** ⭐2 | MCP server driving a local JDownloader 2 through its full download lifecycle — premium hosters, link containers, captcha folders — over `myjdapi`. | `Python` |
| **[awesome-metho-docs](https://github.com/arousi/awesome-metho-docs)** ⭐6 | Keep functional requirements, use cases, diagrams and PM artefacts *next to the codebase* instead of rotting in a wiki. | `Docs` |
| **[Libya-Cities](https://github.com/arousi/Libya-Cities)** ⭐4 | Open dataset of Libya's cities, because every form in the country needs one and nobody had published it. | `Data` |
| **[uot-it-swe](https://github.com/arousi/uot-it-swe)** ⭐9 | Software Engineering department archive at the Faculty of IT, University of Tripoli — years of coursework and student contributions in one place. | `Docs` |

## `$ systemctl status platform`

What's actually running in production right now, not just written:

```console
● traefik.service            edge proxy · automatic TLS · per-app routing
● platform-postgres.service  one shared database, no app runs its own
● platform-minio.service     shared S3-compatible object storage
● monitoring.service         prometheus · grafana · alertmanager → telegram
● crowdsec.service           bans enforced at the edge
● health-reactor.service     autoheals containers that stop answering
● erpnext.service            prod + dev + demo benches, shared & dedicated tiers
● payments.service           Libyan gateways — LYPay · Moamalat · Plutu
● mail.service               self-hosted mail stack behind the same proxy
```

## `$ cat stack`

<div align="center">

![Python](https://img.shields.io/badge/Python-3670A0?style=flat-square&logo=python&logoColor=ffdd54)
![Rust](https://img.shields.io/badge/Rust-000000?style=flat-square&logo=rust&logoColor=white)
![Dart](https://img.shields.io/badge/Dart-0175C2?style=flat-square&logo=dart&logoColor=white)
![Flutter](https://img.shields.io/badge/Flutter-02569B?style=flat-square&logo=flutter&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![Django](https://img.shields.io/badge/Django-092E20?style=flat-square&logo=django&logoColor=white)

![Frappe](https://img.shields.io/badge/Frappe%20%2F%20ERPNext-0089FF?style=flat-square&logo=frappe&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Traefik](https://img.shields.io/badge/Traefik-24A1C1?style=flat-square&logo=traefikproxy&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![MinIO](https://img.shields.io/badge/MinIO-C72E49?style=flat-square&logo=minio&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)

</div>

## `$ git log --oneline | head`

<div align="center">

[![streak](https://streak-stats.demolab.com/?user=swe-sanad&theme=dark&hide_border=true&date_format=M%20j%5B%2C%20Y%5D)](https://github.com/swe-sanad)

</div>

## `$ contact`

[![Email](https://img.shields.io/badge/sanad.arousi%40outlook.com-0078D4?style=flat-square&logo=microsoftoutlook&logoColor=white)](mailto:sanad.arousi@outlook.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/sanadalarousi)
[![Personal](https://img.shields.io/badge/personal%20%2F%20OSS-@arousi-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/arousi)

```console
sanad@swe-pioneers:~$ exit
```
