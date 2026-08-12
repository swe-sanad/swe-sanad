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
  location   Zawia, Libya
  status     ● open to interesting work
```

I build and run the boring parts that have to stay up: the shared services, the backups,
the alert that fires at 3am. Most of my day is ERP work for real businesses in Libya —
and the platform underneath it that keeps a dozen services online.

---

# `$ tree ~/portfolio`

> `🔒` marks commercial or client work — private source, happy to walk through it on a call.
> Everything else is public and linked.

## `01_platform/` — the platform behind the client work

**Cloud portal & control platform** `🔒`

A self-hosted, multi-tenant hosting and control platform I designed, built and operate.
Clients get a self-service portal — register, launch a demo, run and manage their own
services, attach a custom domain, and see their own billing. Operators get a control
panel spanning every tenant, subscription and invoice. Privilege-separated by design, so
a client can drive their own workloads without ever holding privileged access.

Full commercial billing (plans, subscriptions, invoices, payments, dunning), deploy
automation so services ship themselves off a tag, first-party CI on my own metal, and
idle-workload suspension that makes a fleet of always-available demos cheap to run.

`Python` · `Django` · `Rust` · `React` · `TypeScript` · `Docker`

## `02_erp/` — Frappe / ERPNext, where most of the revenue is

| project | what it does | stack |
|---|---|---|
| **[SWE-Pioneers/frappe](https://github.com/SWE-Pioneers/frappe)** | Public monorepo tracking our forks of the Frappe app ecosystem as submodules — the base every ERP customisation ships from. | `Python` |
| **Sales system setup** `🔒` | Libyan omnichannel sell-stack for ERPNext v16 — POS + webshop + accounting, vertical profiles (grocery, clothing) and a baked-in bilingual chart of accounts. | `Python` |
| **Books** `🔒` | Simple accounting on Frappe — offline desktop build (free) and hosted web (paid). Ported from Frappe Books. | `Python` |
| **Mailbox** `🔒` | Custom app pairing email integration with Libyan payment gateways. | `Python` |
| **Construction ops** `🔒` | Project accounting and construction operations for a contracting client. | `Python` |
| **Shariah compliance** `🔒` | Shariah-compliance rules layered onto standard ERPNext accounting. | `Python` |
| **Client blueprint** `🔒` | The blueprint every client bench is provisioned from — shared, dedicated and demo tiers off one definition. | `Python` |

## `03_fintech/` — getting paid, locally

| project | what it does | stack |
|---|---|---|
| **Payments service** `🔒` | Payments for the platform with a provider-registry abstraction over the Libyan gateways — **LYPay**, **Moamalat** and **Plutu** — so a new provider is a class, not a rewrite. Pay-first provisioning hangs off this. | `Python` |

## `04_products/` — apps and client platforms

| project | what it does | stack |
|---|---|---|
| **Masayef** `🔒` | Chalet reservation platform delivered for a government youth ministry — public booking flow plus an operator back office. | `TypeScript` |
| **Talky Manager** `🔒` | Local, offline voice-note transcription with open-source Whisper — bring an audio file, get LLM-ready transcripts. No cloud, no upload. | `Rust` |
| **Vaky Trips** `🔒` | Trip/travel platform. | `TypeScript` |
| **Chatty AI** `🔒` | Cross-platform AI chat client. | `Dart` `Flutter` |
| **Home bakery system** `🔒` | ERPNext + Flutter for small bakeries — separate flows for owners, bakers and drivers. | `Dart` `Python` |
| **Elections prototype** `🔒` | Election-process prototype. | `Dart` `Flutter` |
| **SaaS platform** `🔒` | Earlier multi-tenant SaaS built on ASP.NET with a Flutter client. | `ASP.NET` `Flutter` |

## `05_oss/` — public, and free to take

| project | what it does | stack |
|---|---|---|
| **[LibreOffice-Claude-Connector](https://github.com/swe-sanad/LibreOffice-Claude-Connector)** ⭐2 | A `.oxt` extension plus a **161-tool MCP server** that lets Claude Code drive LibreOffice — read, write, format, chart and export Writer/Calc documents live on the user's screen. | `Python` |
| **[jdownloader-mcp](https://github.com/swe-sanad/jdownloader-mcp)** ⭐2 | MCP server driving a local JDownloader 2 through its full download lifecycle — premium hosters, link containers, captcha folders — over `myjdapi`. | `Python` |
| **[awesome-metho-docs](https://github.com/arousi/awesome-metho-docs)** ⭐6 | Keep functional requirements, use cases, diagrams and PM artefacts *next to the codebase* instead of rotting in a wiki. | `Docs` |
| **[Libya-Cities](https://github.com/arousi/Libya-Cities)** ⭐4 | Open dataset of Libya's cities, because every form in the country needs one and nobody had published it. | `Data` |
| **[uot-it-swe](https://github.com/arousi/uot-it-swe)** ⭐9 | Software Engineering department archive at the Faculty of IT, University of Tripoli — years of coursework and student contributions in one place. | `Docs` |

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
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
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
