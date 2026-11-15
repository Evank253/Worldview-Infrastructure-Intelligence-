# Security, Privacy and Access Boundaries

**Status: PROPOSED CONTROL REQUIREMENTS.**

## Infrastructure sensitivity
Critical infrastructure information may expose security-relevant layouts, access points, network topology, vulnerabilities, private facilities or operational details. Apply source-specific rights, classification, least privilege, purpose limitation, tenant/project scope, audit logging, retention rules and secure storage. Public availability of one record does not imply permission to redistribute or combine it without restriction.

## Worker and resident privacy
Worker identity, employment history, private credentials, performance disputes and residential utility details are restricted to authorized scopes. Provide consent-aware sharing, correction/dispute workflows, access logs and data minimization. Public-facing maps must not expose private worker or resident information.

## Access controls
Separate authentication from authorization. An identity provider establishes an identity assertion only; it does not grant project, utility-owner, engineering, inspection or human-governance authority. Enforce role + resource + purpose + scope policies server-side. Deny by default and log decisions.

## Safety boundary
WII is an intelligence and recordkeeping aid. It is not an official 811 ticket, utility locate, excavation clearance, engineering approval, permit, inspection approval or authorization to enter/alter infrastructure. Users must follow applicable law, utility-owner processes, professional requirements and field safety procedures.

## Data integrity and correction
No privileged user silently rewrites historical evidence. Append corrections with author, reason, time, prior digest/reference and review disposition. Preserve audit history and disputed claims.
