# Awesome-Team-Organization-Seat-Management

# Awesome Team Organization & Seat Management

> A curated list of top Team Organization and Seat Management platforms — both SaaS/Hosted commercial solutions and open-source alternatives for managing team hierarchies, user groups, license allocation, and role-based access across organizational tools.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [BrowserStack Team Management](#browserstack-team-management)
  - [Slack SCIM & User Groups](#slack-scim--user-groups)
  - [Google Workspace Admin Groups](#google-workspace-admin-groups)
  - [Microsoft Entra Group-Based Licensing](#microsoft-entra-group-based-licensing)
  - [GitHub Teams](#github-teams)
  - [GitLab Group Members](#gitlab-group-members)
  - [Notion SCIM & Teamspaces](#notion-scim--teamspaces)
  - [Asana SCIM Provisioning](#asana-scim-provisioning)
- [Open-Source Software](#-open-source-software)
  - [Hitobito](#hitobito)
  - [Apache Syncope](#apache-syncope)
  - [GoSCIM](#goscim)
  - [Perun IdM](#perun-idm)
  - [Sesame IDAM](#sesame-idam)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Team Organization and Seat Management platforms. These are not open-source but are included as reference points for feature comparison.

### BrowserStack Team Management
**Type:** Test platform teams with granular seat allocation
BrowserStack allows organization Owners and Admins to create Teams that reflect internal structure (e.g., Frontend, MobileSquad) and assign members to them [citation:1]. The critical differentiator for seat management is **User License Allocation**: the owner can assign a fixed number of product licenses (e.g., 25 Live licenses to Team A) while leaving other teams to share from the organization pool [citation:1]. Advanced features include **Manage Data Access** (restricting test data visibility to a user's own team) and **Multiple Teams** (a user can belong to one Primary Team for license deduction and multiple Additional Teams for collaboration) [citation:1]. Teams and user access can also be managed via REST API, including updating RBAC roles and product access [citation:14].
**Best for:** Organizations using BrowserStack Enterprise wanting granular control over which teams consume specific product licenses and what test data each team can see.

### Slack SCIM & User Groups
**Type:** Enterprise messaging user provisioning and groups
Slack supports SCIM 2.0 for provisioning and deprovisioning users and groups, primarily for Enterprise organizations where SCIM operations span the entire org rather than individual workspaces [citation:3]. Creating a SCIM group creates an IDP group. **Key limitations:** Users cannot be permanently deleted (only deactivated); duplicate emails fail provisioning even if the existing user is deactivated; single-channel guests cannot be fully provisioned via SCIM [citation:3]. Group mention handles (@group) cannot be set via SCIM. The Slack Python SDK provides SCIM API wrappers for Users and Groups [citation:15].
**Best for:** Enterprise organizations using an IdP (Okta, OneLogin) to automate Slack user lifecycle and group membership, accepting SCIM limitations for guests and deletion.

### Google Workspace Admin Groups
**Type:** Directory groups with nested membership and roles
Google Workspace Directory API manages group members with three roles: **OWNER** (full control including deletion), **MANAGER** (everything except making owners or deleting), and **MEMBER** (subscribe, view archives, view membership) [citation:4]. Groups can be nested (a group can be a member of another group), but cyclic memberships are rejected. Nested group members may take up to 10 minutes to propagate to the parent group. The API supports adding, updating, retrieving, and listing members with pagination [citation:4].
**Best for:** Google Workspace organizations needing hierarchical group structures with delegated administration roles and API-driven membership management.

### Microsoft Entra Group-Based Licensing
**Type:** Automated license assignment via security groups
Microsoft Entra ID supports **group-based licensing**: security groups are configured to automatically assign licenses from a set of subscriptions to all members [citation:5]. When a user is added to or removed from the group, licenses are automatically assigned or unassigned. **Critical constraint:** You must ensure enough licenses exist for all group members; if licenses run out, new users will not be assigned licenses until more become available [citation:5]. Group-based licensing should not be configured for groups containing Azure B2B accounts.
**Best for:** Microsoft 365 enterprises wanting to automate license assignment and removal based on security group membership, reducing manual admin overhead.

### GitHub Teams
**Type:** Repository access teams with nested membership
GitHub Teams group organization members for repository permissions. Team members include members of child teams, with each membership having a role (`member` or `maintainer`) and an `inherited` flag indicating whether membership comes from a child team [citation:6]. The REST API supports listing team members filtered by role, and adding or updating team membership (requires org owner or team maintainer). Team synchronization with an IdP is available on GitHub Enterprise Cloud [citation:6].
**Best for:** GitHub organizations needing nested teams with inherited permissions and API-driven membership management for repository access.

### GitLab Group Members
**Type:** Hierarchical groups with billable member tracking
GitLab Groups support hierarchical membership, and the **Billable Members API** lists all members consuming a license, including members from subgroups and projects [citation:7]. This endpoint only works on top-level groups. The API supports searching by name/username/email and sorting by access level, join date, or last activity. A separate endpoint lists all memberships for a specific billable member, showing which projects and subgroups they belong to [citation:7].
**Best for:** GitLab organizations needing visibility into exactly which users are consuming licenses across nested groups and projects.

### Notion SCIM & Teamspaces
**Type:** Enterprise workspace provisioning and groups
Notion's SCIM API (Enterprise plan only) provisions users and groups, with a requirement for SAML 2.0 IdP support [citation:9]. SCIM can create/remove members, update profiles, create/remove groups, and manage group membership. **Important:** SCIM cannot manage workspace guests. A separate SCIM token is required for each workspace being managed. The `role` attribute supports `owner`, `membership_admin`, `member`, and `restricted_member` [citation:9].
**Best for:** Notion Enterprise organizations using an IdP to automate user and group provisioning, accepting that guest management remains manual.

### Asana SCIM Provisioning
**Type:** Enterprise user and team provisioning
Asana supports SCIM provisioning via Microsoft Entra ID (and other IdPs), automatically creating/removing users and keeping attributes synchronized [citation:10]. SCIM can also provision groups and group memberships. Prerequisites include an Asana Enterprise plan and admin access to generate a Service Account token with scopes: Users: Read, Users: Create and modify, and Teams: Read [citation:10]. Attribute mapping includes userName, active, name.formatted, title, department, manager, and employeeNumber.
**Best for:** Asana Enterprise organizations wanting automated user and team provisioning from their IdP, with attribute synchronization.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Team Organization and Seat Management tools. The open-source ecosystem splits between **group hierarchy managers** and **identity governance/SCIM servers**.

### Hitobito
**Stack:** Ruby on Rails | **License:** AGPL-3.0
Hitobito is an open-source web application for managing **complex group hierarchies** with members, events, courses, and mailings [citation:19]. It provides a powerful meta-model: groups are arranged in a tree, each group type has specific role types with permissions, and layers define permission ranges. The core does not provide specific group/role types—these are defined in organization-specific plugins (Wagons). This makes it exceptionally suited for organizations with distributed structures (political parties with local chapters, associations with regional branches). Every user's abilities are derived from their role permissions across their different groups [citation:19].
**Best for:** Associations, non-profits, and federated organizations needing to model complex nested group hierarchies with role-based permissions rather than simple seat counting.

### Apache Syncope
**Stack:** Java | **License:** Apache 2.0
Apache Syncope is an open-source Identity and Access Management (IAM) and Identity Governance Administration (IGA) platform [citation:16]. It provides centralized user, group, role, and entitlement management with automated provisioning/deprovisioning workflows. Supports RBAC, delegated administration, LDAP/AD/database connectors, SAML 2.0, OIDC, and **SCIM standards** [citation:16]. Includes audit logging and compliance reporting. Available via Azure Marketplace with Docker deployment.
**Best for:** Organizations wanting a standards-based, Apache-governed IGA platform for centralized group and role management across heterogeneous directories and applications.

### GoSCIM
**Stack:** Go | **License:** Open Source
GoSCIM is a lightweight, high-performance SCIM 2.0 server built in Go, designed for user provisioning from IdPs like Okta and Azure [citation:23]. It implements full RFC 7643/7644 compliance, supports dynamic schema loading, advanced ANTLR-based filter parsing, and scales from 10 to 100,000+ users. Integrates with Active Directory, LDAP, Salesforce, Slack, and more. Docker deployment with Couchbase backend. Described as "the fastest and most flexible open-source implementation of the SCIM 2.0 protocol" [citation:23].
**Best for:** Developers needing a focused, fast SCIM server to receive user/group provisioning from enterprise IdPs without deploying a full IAM suite.

### Perun IdM
**Stack:** Java | **License:** Open Source
Perun is an identity and access management system primarily targeting **academia**, for managing users within organizations and projects and managing access rights to services [citation:24]. Features include automated identity management workflows, provisioning/deprovisioning, delegated user/service management, group and virtual organization organization, full user lifecycle handling, self-registration via invitations, and import/export/sync with existing user databases. All actions are audited.
**Best for:** Research institutions and universities needing to manage users across projects, virtual organizations, and service access with delegated administration.

### Sesame IDAM
**Stack:** Rust | **License:** Open Source
Sesame is a self-hosted identity and access management system with a **portable OIDC provider contract** and org-scoped authorization [citation:17]. Features include EdDSA-signed JWT access tokens, coarse-grained checks via JWT claims (zero latency for "is Admin?"), fine-grained ABAC authorization via `POST /authorize`, role inheritance, application/RP model, webhook system, and API keys. The project emphasizes a self-hosted, no per-user pricing model. OpenAPI specs are published for six services (identity-login, identity-session, identity-user-mgmt, authz-core, api-keys, org-mgmt) [citation:17].
**Best for:** Teams wanting a modern, Rust-based IDAM with org-scoped authorization and a portable contract, accepting that the project is early-stage with some features (webhooks, application model) still in progress.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Group Hierarchy | Seat/License Mgmt | SCIM | Self-Hosted | Best For |
|----------|---------|-------|-----------------|-------------------|------|-------------|----------|
| **BrowserStack Teams** | Proprietary | Cloud | Flat teams | ✅ Granular allocation | API | ❌ | Test platform seat control |
| **Slack SCIM** | Proprietary | Cloud | IDP groups | (Via IdP) | ✅ | ❌ | Enterprise messaging provisioning |
| **Google Workspace** | Proprietary | Cloud | Nested groups + roles | ❌ | (API) | ❌ | Directory group hierarchy |
| **Entra Group Licensing** | Proprietary | Cloud | Security groups | ✅ Automatic | (Entra) | ❌ | Microsoft 365 license automation |
| **GitHub Teams** | Proprietary | Cloud | Nested teams | (Via org) | (Entra sync) | ❌ | Repository access teams |
| **GitLab Groups** | Proprietary | Cloud | Hierarchical groups | ✅ Billable members API | (SCIM) | ❌ | License consumption visibility |
| **Notion SCIM** | Proprietary | Cloud | Groups + Teamspaces | (Enterprise seats) | ✅ | ❌ | Notion Enterprise provisioning |
| **Asana SCIM** | Proprietary | Cloud | Groups + Teams | (Enterprise seats) | ✅ | ❌ | Asana Enterprise provisioning |
| **Hitobito** | AGPL-3.0 | Ruby/Rails | ✅ Deep tree + layers | (Roles, not seats) | ❌ | ✅ | Complex organizational hierarchies |
| **Apache Syncope** | Apache 2.0 | Java | Groups + roles | (Entitlements) | ✅ | ✅ | Standards-based IGA |
| **GoSCIM** | Open Source | Go | SCIM groups | (Via SCIM) | ✅ | ✅ | Fast SCIM provisioning |
| **Perun IdM** | Open Source | Java | Groups + VOs | (Access rights) | (Check) | ✅ | Academia/research orgs |
| **Sesame IDAM** | Open Source | Rust | Orgs + roles | (Entitlements) | (Check) | ✅ | Modern OIDC + ABAC |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Team Organization or Seat Management tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source. Note that the open-source ecosystem **splits** between group hierarchy managers (Hitobito) and identity governance/provisioning servers (Syncope, GoSCIM, Perun). No open-source tool replicates BrowserStack's specific model of allocating fixed product licenses per team, but Hitobito offers the deepest organizational hierarchy modeling and Syncope offers the most comprehensive IGA capabilities.

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
