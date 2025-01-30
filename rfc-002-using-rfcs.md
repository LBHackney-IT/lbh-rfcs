---
status: proposed
---

# Must Use RFCs for Architectural or Process or Technical Operational Changes

## Summary
All changes to our current architecture, processes, or ways of working must be covered by a Request for Change (RFC) for better governance and audit purposes.

## Problem
At the implementation of our initial Hack-It restructure, one of the decisions made was to eliminate the use of the Change Advisory Board (CAB) as it was felt that this was no longer fit for purpose.  The majority of our projects were in a more agile format with delivery occuring once or more per week.

At the start of the Modern Tools for Housing programme, Architecture Decision Records (ADRs) were used to record decisions on changes to the architecture being built [ADR Repository](https://github.com/LBHackney-IT/lbh-adrs).  These have not been used since the base API Platform architecture was established so for much of the changes since then, there was not a consistent way of recording decisions on changes so no clear audit trail.


## Proposal
In order to establish a clear audit trail and decision log for changes to what we build or how we build a record of decisions must be re-introduced.  This is to be in the form of a Request for Change (RFC) which would give a broader scope on the types of change that could be recorded.
Any change to architecture patterns, engineering processes or technical ways of working should be backed by an RFC.  The template RFC can be found at [RFC Template](https://github.com/LBHackney-IT/lbh-rfcs/blob/main/rfc-000-template.md).

## Scope
- Changes to architecture such as database technologies, encryption methods, etc.
- Changes to programming patterns such as Event Driven Architecture
- Changes to a feature or implementation for a serfice that has moved from development to BAU.

## Out of Scope
- Products under active development and not in BAU (unless the change relates to the overall architecture or change in development standard).
- Emergency fixes (a retrospective RFC can be provided in these cases)
