# Don't use Cypress Cloud

## Summary

We don't believe the value of Cypress Cloud outweighs the costs required to enable Single Sign On with our Google Workspace, so we will only use local Cypress functionality.

## Problem

In September 2024 we discovered a Cypress Cloud account for Manage My Home that doesn't meet our policy for Single Sign On. In order to become compliant we would need either the Open Source Plan + SSO ($1,250 per year), or the Open Source Team Plan + SSO ($1,799 per year).

"Cypress" is an open source frontend testing libary that's used extensively across Hackney ICT engineering. "Cypress Cloud" is a proprietary SaaS which offers additional features including parallel build tracking, flake detection, and a UI to debug failures and replay tests.

Cypress Cloud was used by Manage My Home to enable parallel tests which in turn speeds up build time. This reduces our CircleCI usage and allows faster feedback.

## Proposal

- We MUST not use Cypress Cloud without it complying with our policies around SAML SSO and integration with our Google Workspace.

- We don't believe the value proposition of Cypress Cloud outweighs the base cost ($1250/year) given that it's currently only in use on two projects. There is other tooling we'd like to evaluate in preference to Cypress Cloud.

- Therefore we will not subscribe to a paid Cypress Cloud licence and will only utilise features available without a Cypress Cloud account.
