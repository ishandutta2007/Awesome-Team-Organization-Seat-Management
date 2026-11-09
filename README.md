# Awesome Team Organization & Seat Management

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](http://creativecommons.org/publicdomain/zero/1.0/)

A curated list of top **Team Organization**, **User Provisioning**, **Identity & Access Management (IAM)**, and **Seat & License Management** platforms. This guide features SaaS/hosted enterprise platforms and open-source self-hosted solutions for managing team hierarchies, user groups, SCIM directory synchronization, role-based access control (RBAC), and license quota allocation.

> 🌟 **Star this repo if you find it useful!** 🌟

---

## 📋 Table of Contents

- [Sector Overview & Market Dynamics](#-sector-overview--market-dynamics)
- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [SaaS Overview & Comparison Table](#saas-overview--comparison-table)
  - [Detailed SaaS Profiles](#detailed-saas-profiles)
- [Open-Source Software](#-open-source-software)
  - [Open-Source Solutions (Ranked by Stars)](#open-source-solutions-ranked-by-stars)
- [Feature Comparison Matrix](#-feature-comparison-matrix)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🌐 Sector Overview & Market Dynamics

The global Identity and Access Management (IAM) and SaaS Operations market is valued at approximately **$21B–$26B in 2025/2026** and projected to exceed **$60B+ by 2032** (CAGR ~12–14%). The sector exhibits a **bifurcated, moderately concentrated market dynamic** where foundational directory and identity infrastructure operates as a high-barrier "winner-take-most" ecosystem dominated by hyperscalers (Microsoft Entra ID, Google Workspace, Okta), while granular seat allocation, fine-grained permissions, and cross-SaaS license lifecycle management remain moderately fragmented among best-of-breed specialized tools and open-source frameworks.

---

## 🟦 SaaS / Hosted Platforms

### SaaS Overview & Comparison Table

The following SaaS solutions provide built-in team hierarchy modeling, SCIM user provisioning, or granular seat and license management. Sorted by **Company Scale / Valuation (Descending)**:

| Platform | Company Scale / Valuation | Pricing (Starting Tier) | Free Tier Limit / Free Trial | Core Seat & Organization Capability |
| :--- | :--- | :--- | :--- | :--- |
| **[Microsoft Entra ID](https://www.microsoft.com/en-us/security/business/identity-access/microsoft-entra-id)** | **$3.1+ Trillion** (Market Cap) | **$7.00** / user / month (P1 tier) | **Free Plan**: Up to 300,000 directory objects (with verified domain; 50k unverified); 30-day trial for P1/P2 | Automated group-based licensing across Microsoft 365 / Azure workloads |
| **[Google Workspace](https://workspace.google.com/)** | **$2.1+ Trillion** (Alphabet Market Cap) | **$7.00** / user / month (Business Starter, annual commitment) | **Free Trial**: 14 days full access (no perpetual free tier) | Directory API for nested groups, delegated admin roles, and member management |
| **[Slack (Salesforce)](https://slack.com/)** | **$260+ Billion** (Salesforce Market Cap; Slack acquired for ~$27.7B) | **$7.25** / user / month (Pro, billed annually) | **Free Plan**: 90 days message history, 10 app integrations, 1:1 audio/video huddles | SCIM 2.0 provisioning, enterprise IDP groups, Fair Billing policy on active seats |
| **[GitHub Teams](https://github.com/)** | **$100+ Billion** (Microsoft subsidiary; acquired for $7.5B in 2018) | **$4.00** / user / month (Team plan) | **Free Plan**: Unlimited public/private repos, 2,000 CI/CD Actions mins/mo, 500 MB packages | Nested team hierarchy with inherited repository access and IdP team sync |
| **[Notion](https://www.notion.so/)** | **$11.0 Billion** (Valuation, 2025/2026 tender) | **$10.00** / user / month (Plus, billed annually) | **Free Plan**: Unlimited blocks for individuals, 1,000 block cap for 2+ users, 5 MB file upload limit | SCIM 2.0 API, Enterprise Teamspaces, role-based workspace permissions |
| **[GitLab](https://about.gitlab.com/)** | **$6.3+ Billion** (Market Cap NASDAQ: GTLB) | **$29.00** / user / month (Premium, billed annually) | **Free Plan**: Up to 5 users per top-level private group namespace, 400 CI/CD minutes/month | Hierarchical subgroups, billable members tracking API across namespaces |
| **[BrowserStack](https://www.browserstack.com/)** | **$4.0 Billion** (Valuation, Series B) | **$29.00** / user / month (Live Desktop, billed annually) | **Free Trial**: 30 minutes manual Live testing, 100 mins automated testing, 100 screenshots | User license allocation per team, primary team deduction, cross-team test isolation |
| **[Asana](https://asana.com/)** | **$2.5+ Billion** (Market Cap NYSE: ASAN) | **$10.99** / user / month (Starter, billed annually) | **Free Plan**: Maximum 2 user seats, unlimited tasks/projects, 100 MB file limit | SCIM user and team provisioning, role assignment via enterprise service token |

---

### Detailed SaaS Profiles

#### Microsoft Entra Group-Based Licensing
- **Type:** Automated license assignment via security groups
- **Key Capabilities:** Microsoft Entra ID supports group-based licensing where security groups automatically assign subscription licenses to members. Adding or removing users dynamically provisions or unassigns licenses.
- **Best For:** Microsoft 365 / Azure enterprise environments seeking automated seat provisioning linked directly to corporate directory security groups.

#### Google Workspace Admin Groups
- **Type:** Directory groups with nested hierarchy and delegated administration
- **Key Capabilities:** Google Workspace Directory API manages nested group structures with `OWNER`, `MANAGER`, and `MEMBER` roles. Groups can be nested with inherited permissions and managed via API.
- **Best For:** Organizations standardizing on Google Workspace requiring delegated administration and API-driven group provisioning.

#### Slack SCIM & User Groups
- **Type:** Enterprise messaging user provisioning and identity groups
- **Key Capabilities:** Full SCIM 2.0 support across enterprise organizations for provisioning and deprovisioning users and groups. Slack features an automated Fair Billing policy that only charges for actively participating seats.
- **Best For:** Enterprises utilizing Okta, Entra ID, or OneLogin to automate group membership and user lifecycle across communication channels.

#### GitHub Teams
- **Type:** Repository access teams with nested membership
- **Key Capabilities:** Supports hierarchical child teams with inherited permissions (`member` or `maintainer`). Team synchronization with enterprise identity providers is natively supported on GitHub Enterprise Cloud.
- **Best For:** Software engineering teams needing granular repository permissions and inherited access controls tied to IdP groups.

#### Notion SCIM & Teamspaces
- **Type:** Enterprise workspace provisioning and granular teamspaces
- **Key Capabilities:** SCIM API provisions users and groups with SAML 2.0 IdP integration. Granular role mapping includes `owner`, `membership_admin`, `member`, and `restricted_member` across segregated teamspaces.
- **Best For:** Knowledge-base and project documentation management across multi-department enterprises.

#### GitLab Group Members
- **Type:** Hierarchical groups with billable member tracking
- **Key Capabilities:** Hierarchical group architecture equipped with a dedicated Billable Members API to inspect which specific users consume paid license seats across nested projects and subgroups.
- **Best For:** DevOps and engineering organizations requiring clear visibility into license utilization across multi-tier repositories.

#### BrowserStack Team Management
- **Type:** Granular seat allocation and test data segregation
- **Key Capabilities:** Administrators can allocate fixed numbers of licenses directly to custom teams rather than draining an organization-wide pool. Supports Primary Team seat deductions and Additional Team collaboration.
- **Best For:** Large QA and engineering organizations managing shared cloud device testing pools across distributed squads.

#### Asana SCIM Provisioning
- **Type:** Enterprise user and team provisioning
- **Key Capabilities:** SCIM integration via Microsoft Entra ID or Okta to synchronize user attributes, provision project teams, and deactivate departing members automatically via Service Account tokens.
- **Best For:** Enterprise project tracking with automated employee directory synchronization.

---

## 🟩 Open-Source Software

Self-hosted, community-driven platforms for team hierarchies, identity governance, access control, and user provisioning.

### Open-Source Solutions (Ranked by Stars)

*Solutions are sorted by GitHub Star Count in descending order:*

| Project | GitHub Stars | Stack | License | Primary Focus |
| :--- | :---: | :--- | :--- | :--- |
| **[Keycloak](https://github.com/keycloak/keycloak)** | [![Stars](https://img.shields.io/github/stars/keycloak/keycloak?style=social&color=white)](https://github.com/keycloak/keycloak/stargazers) | Java | Apache 2.0 | Full-featured enterprise IAM, OpenID Connect / SAML IdP, user federation, fine-grained role & group hierarchies |
| **[Authelia](https://github.com/authelia/authelia)** | [![Stars](https://img.shields.io/github/stars/authelia/authelia?style=social&color=white)](https://github.com/authelia/authelia/stargazers) | Go | Apache 2.0 | Single Sign-On and 2FA authentication portal and companion for reverse proxies with group-based access control |
| **[Authentik](https://github.com/goauthentik/authentik)** | [![Stars](https://img.shields.io/github/stars/goauthentik/authentik?style=social&color=white)](https://github.com/goauthentik/authentik/stargazers) | Python, Go | GPL-3.0 | Modern identity provider with built-in SCIM provider/consumer, flow-based user lifecycle, and group policies |
| **[ZITADEL](https://github.com/zitadel/zitadel)** | [![Stars](https://img.shields.io/github/stars/zitadel/zitadel?style=social&color=white)](https://github.com/zitadel/zitadel/stargazers) | Go | Apache 2.0 | Cloud-native multi-tenant identity infrastructure with organizational hierarchies, projects, and delegated team roles |
| **[Casdoor](https://github.com/casdoor/casdoor)** | [![Stars](https://img.shields.io/github/stars/casdoor/casdoor?style=social&color=white)](https://github.com/casdoor/casdoor/stargazers) | Go | Apache 2.0 | Multi-tenant UI-first IAM platform with SCIM 2.0, WebAuthn, OAuth/OIDC, and organization member management |
| **[Permify](https://github.com/Permify/permify)** | [![Stars](https://img.shields.io/github/stars/Permify/permify?style=social&color=white)](https://github.com/Permify/permify/stargazers) | Go | Apache 2.0 | Google Zanzibar-inspired authorization service for modeling multi-tenant organizational hierarchies and permissions |
| **[MidPoint](https://github.com/Evolveum/midpoint)** | [![Stars](https://img.shields.io/github/stars/Evolveum/midpoint?style=social&color=white)](https://github.com/Evolveum/midpoint/stargazers) | Java | EUPL 1.2 | Comprehensive open-source Identity Governance and Administration (IGA) with identity lifecycle and role cataloging |
| **[Hitobito](https://github.com/hitobito/hitobito)** | [![Stars](https://img.shields.io/github/stars/hitobito/hitobito?style=social&color=white)](https://github.com/hitobito/hitobito/stargazers) | Ruby on Rails | AGPL-3.0 | Tree-structured group hierarchy management with role inheritance for associations, federated NGOs, and clubs |
| **[Apache Syncope](https://github.com/apache/syncope)** | [![Stars](https://img.shields.io/github/stars/apache/syncope?style=social&color=white)](https://github.com/apache/syncope/stargazers) | Java | Apache 2.0 | Standards-based identity governance, SCIM server, automated user provisioning, and enterprise role entitlements |
| **[Perun IdM](https://github.com/CESNET/perun)** | [![Stars](https://img.shields.io/github/stars/CESNET/perun?style=social&color=white)](https://github.com/CESNET/perun/stargazers) | Java | Apache 2.0 | Virtual organization (VO) management, academic project access control, and distributed group administration |
| **[GoSCIM](https://github.com/arturoeanton/goscim)** | [![Stars](https://img.shields.io/github/stars/arturoeanton/goscim?style=social&color=white)](https://github.com/arturoeanton/goscim/stargazers) | Go | MIT | Lightweight, high-performance RFC 7643/7644 SCIM 2.0 provisioning server for IdP directory sync |
| **[Sesame IDAM](https://github.com/microscaler/sesame-idam)** | [![Stars](https://img.shields.io/github/stars/microscaler/sesame-idam?style=social&color=white)](https://github.com/microscaler/sesame-idam/stargazers) | Rust | Apache 2.0 | Modern, self-hosted OIDC provider with org-scoped authorization and fine-grained ABAC verification |

---

## 📊 Feature Comparison Matrix

| Software / Project | Type | Group Hierarchy | Seat / Quota Allocation | SCIM Provisioning | Self-Hosted | Primary Stack |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Microsoft Entra ID** | SaaS | Security Groups | ✅ Automated group licenses | ✅ Full SCIM 2.0 | ❌ | Cloud |
| **Google Workspace** | SaaS | Nested Groups + Roles | ❌ License per account | ⚠️ Via Directory API | ❌ | Cloud |
| **Slack SCIM** | SaaS | IDP Groups | ⚠️ Fair active-seat billing | ✅ Full SCIM 2.0 | ❌ | Cloud |
| **GitHub Teams** | SaaS | Nested Teams | ⚠️ Org seat pool | ⚠️ IdP Team Sync | ❌ | Cloud |
| **Notion** | SaaS | Groups + Teamspaces | ⚠️ Workspace seat pool | ✅ Enterprise SCIM | ❌ | Cloud |
| **GitLab** | SaaS / Self-Host | Hierarchical Subgroups | ✅ Billable Members API | ✅ Full SCIM 2.0 | Optional | Ruby, Go, Vue |
| **BrowserStack** | SaaS | Granular Teams | ✅ Granular quota per team | ⚠️ REST API | ❌ | Cloud |
| **Asana** | SaaS | Teams + Workspaces | ⚠️ Workspace seat pool | ✅ Full SCIM 2.0 | ❌ | Cloud |
| **Keycloak** | Open-Source | ✅ Deep Group Tree | ⚠️ Role/Attribute based | ⚠️ Via Extensions | ✅ | Java |
| **Authelia** | Open-Source | Flat / Rule Groups | ❌ Access policy only | ❌ | ✅ | Go |
| **Authentik** | Open-Source | ✅ Groups & Users | ⚠️ Quota / Flow policies | ✅ Provider & Consumer | ✅ | Python, Go |
| **ZITADEL** | Open-Source | ✅ Org / Project Roles | ⚠️ Multi-tenancy scopes | ⚠️ In progress / API | ✅ | Go |
| **Casdoor** | Open-Source | ✅ Multi-Org + Groups | ⚠️ Quota / App limits | ✅ Built-in SCIM | ✅ | Go |
| **Permify** | Open-Source | ✅ Zanzibar Relations | ⚠️ Relation-based checks | ⚠️ API driven | ✅ | Go |
| **MidPoint** | Open-Source | ✅ Full Org Structure | ✅ Entitlement governance | ✅ Full SCIM 2.0 | ✅ | Java |
| **Hitobito** | Open-Source | ✅ Deep Tree + Layers | ❌ Roles & permissions | ❌ | ✅ | Ruby on Rails |
| **Apache Syncope** | Open-Source | ✅ Org Units & Roles | ✅ Entitlements engine | ✅ Full SCIM 2.0 | ✅ | Java |
| **Perun IdM** | Open-Source | ✅ Virtual Orgs + Groups | ⚠️ Service access rights | ⚠️ Via connectors | ✅ | Java |
| **GoSCIM** | Open-Source | Flat SCIM Groups | ❌ Directory sync only | ✅ RFC 7643/7644 | ✅ | Go |
| **Sesame IDAM** | Open-Source | Org + Roles | ⚠️ Org-scoped ABAC | ❌ | ✅ | Rust |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source or enterprise platform specializing in team organization, identity governance, or seat/license allocation:

1. Fork this repository.
2. Create a new branch: `git checkout -b feature/add-tool`.
3. Add the tool to the appropriate table and profile section following the existing format.
4. Open a Pull Request with a clear summary of the platform's unique value proposition.

---

## 📄 License

This repository and its curated documentation are published under the **[CC0 1.0 Universal (Public Domain)](http://creativecommons.org/publicdomain/zero/1.0/)** license. Individual software platforms and projects mentioned retain their respective trademarks and licenses.
