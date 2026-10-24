# RFC 0001: Rebuild Mattify Skills around RFC authoring (Umbrella)

**Status:** Approved

**Type:** Umbrella

## Summary

This umbrella defines Mattify as a skills product whose identity and skill flows are centered on creating RFCs through the `/specify` skill. Child RFCs separately cover product identity and distribution, and the RFC-first skill architecture.

## Problem

The repository still carries the original Matt Pocock product identity and workflows that route substantial work through issue-tracker specs and tickets. Mattify needs one coherent identity and a clear RFC-first purpose across its install surface and skill catalog.

## Goals

Complete both listed child RFCs. The finished product presents as Mattify and directs relevant work through `/specify` to create and manage RFCs.

## Non-goals

This umbrella does not define implementation details for either child. It does not authorize publishing, deployment, or changes to external repositories.

## Children

| RFC | Concern |
|-----|---------|
| [0003](0003-rfc-first-skill-flows.md) | Route Mattify skills through RFC creation with specify |
| [0002](0002-mattify-brand-and-distribution.md) | Mattify identity and distribution |

## Acceptance

Close when both children are Implemented and their acceptance criteria pass. Create a new RFC for later scope; do not reopen this umbrella.
