# Universal Construction Work Record — Proposed Domain Contract

**Status: PROPOSED.** This is a shared schema direction for WAI-001, SCH-001, INS-001, CPI-001, WRI-001, PIP-001, asset lifecycle, and field intelligence.

## Core entities
- Project: stable ID, owner, scope, jurisdiction, contract references, boundaries, schedule baseline, access classification.
- Work package/task: scope, approved plan/spec revision, location geometry, dependencies, planned/actual dates, acceptance criteria.
- Organization: owner, prime contractor, subcontractor, utility, inspector/authority, supplier; preserve role and effective dates.
- Crew participation: worker identity reference, role, participation interval, authorization basis; personnel details access-controlled.
- Work event: what was performed, where, when, by whom/organization, equipment/method, source, notes, attachments.
- Asset reference: permanent asset ID, external identifiers, owner/operator, location ID, relationships and lifecycle state.
- Inspection event: authority, inspector reference, inspection type, requirements/revision, time, findings, evidence and disposition.
- Deficiency: requirement, approved source, observed condition, measurement/method, evidence, discovery date, responsible scope (if established), dispute/response, correction, reinspection and closure.
- Schedule event: baseline milestone, actual milestone, wait state, dependency, delay interval, documented cause, impact, mitigation and evidence.
- Recognition event: specific accomplishment, project/asset context, evidence, reviewer, criteria and response/correction mechanism.
- Submission: contractor declaration or as-built submission, revision, receipt time, scope, completeness, reviewer and acceptance status.

## Event chain
Approved requirement → authorized work → contemporaneous record → submission → review → deficiency/correction if needed → reinspection → disposition → history retained.

## Required distinctions
- Contractor completion declaration is not official acceptance.
- Submitted as-built is not independently verified geometry.
- A schedule delay is not automatically contractor fault.
- A deficiency is not automatically attributable to the incoming crew.
- Worker performance must account for inherited conditions, design changes, materials, access, weather, permits, utility coordination and inspection availability.
- Recognition and deficiency records both require evidence and correction/dispute pathways.

## Example: inherited pole attachment defect
Record the incoming crew's discovery, location and pole identity, approved plan/spec revision, actual measurement and method, photographs, notification, previous contractor's response, correction work, correction crew, reinspection, restart date and schedule effect. Do not infer blame from discovery alone.

## Dispositions
PASSED / FAILED / CONDITIONAL_ACCEPTANCE / CORRECTIONS_REQUIRED / REINSPECTION_REQUIRED / NOT_INSPECTED / RECORD_UNAVAILABLE / DISPUTED. Preserve issuing authority and original wording as source evidence.
