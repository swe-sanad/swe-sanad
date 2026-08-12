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

## `$ ls ~/work --public`

| project | what it is |
|---|---|
| **[LibreOffice-Claude-Connector](https://github.com/swe-sanad/LibreOffice-Claude-Connector)** | A `.oxt` extension plus a 161-tool MCP server that lets Claude Code drive LibreOffice — read, write, format, chart and export Writer/Calc documents live on the user's screen. `Python` |
| **[jdownloader-mcp](https://github.com/swe-sanad/jdownloader-mcp)** | MCP server that drives a local JDownloader 2 through its full download lifecycle — premium hosters, link containers, captcha folders — over `myjdapi`. `Python` |
| **[awesome-metho-docs](https://github.com/arousi/awesome-metho-docs)** | A methodology repo that keeps functional requirements, use cases, diagrams and PM artefacts *next to the codebase* instead of rotting in a wiki. |
| **[SWE-Pioneers/frappe](https://github.com/SWE-Pioneers/frappe)** | Monorepo tracking our forks of the Frappe app ecosystem as submodules — the base we ship ERP customisations from. |
| **[Libya-Cities](https://github.com/arousi/Libya-Cities)** | Open dataset of Libya's cities, because every form in the country needs one and nobody had published it. |

## `$ systemctl status platform`

Not all of it is open source. The platform I run and maintain:

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

**Delivery work:** ERPNext + custom Frappe apps for a government youth-sector
reservations platform, project accounting for a construction company, and NGO
customisations — each on its own tenant, provisioned from one blueprint.

## `$ cat stack`

<div align="center">

![Python](https://img.shields.io/badge/Python-3670A0?style=flat-square&logo=python&logoColor=ffdd54)
![Dart](https://img.shields.io/badge/Dart-0175C2?style=flat-square&logo=dart&logoColor=white)
![Flutter](https://img.shields.io/badge/Flutter-02569B?style=flat-square&logo=flutter&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Rust](https://img.shields.io/badge/Rust-000000?style=flat-square&logo=rust&logoColor=white)
![Django](https://img.shields.io/badge/Django-092E20?style=flat-square&logo=django&logoColor=white)

![Frappe](https://img.shields.io/badge/Frappe%20%2F%20ERPNext-0089FF?style=flat-square&logo=frappe&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Traefik](https://img.shields.io/badge/Traefik-24A1C1?style=flat-square&logo=traefikproxy&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
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
