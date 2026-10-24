# RFC 0003: Route Mattify skills through RFC creation with specify (child of 0001)

**Status:** Approved

**Parent:** [0001](0001-mattify-rfc-first-skills.md)

## Summary

Reorient Mattify's skill catalog around the `/specify` RFC lifecycle. Skills help users form, validate, and implement decisions recorded as RFCs, and avoid parallel spec or ticket flows that bypass that lifecycle.

## Problem

The current catalog centers on interviews, tracker-published specs, ticket decomposition, and implementation chains. That does not match the requested Mattify purpose: use `/specify` to create RFCs.

## Goals

Define one coherent user journey in which skill entry points identify when an RFC is needed, call `/specify` to create or manage it, and route implementation work from approved RFCs. Update, combine, retire, or retain skills based on their role in that journey. Ensure router and skill descriptions reflect actual behavior.

## Non-goals

Product naming, source URLs, package identity, and legal or historical attribution belong to RFC 0002. This RFC does not implement changes before approval and does not require every skill to create an RFC when the user asks for an unrelated, non-project task.

## Design

Inventory all buckets and invocation modes. Define which skills create RFCs, provide research or decision input to an RFC, implement an approved RFC, or remain standalone utilities. Establish `/specify` as the only RFC lifecycle authority; remove conflicting direct-publication paths where they duplicate or bypass it. Update `ask-matt`, skill instructions and metadata, bucket READMEs, root README, and promoted-skill docs according to the final map. Preserve approval gates and the existing promoted-versus-non-promoted packaging rules unless a later RFC changes them.

## Acceptance

Every skill has a documented role in the RFC-first journey or an explicit reason to remain standalone. No route duplicates `/specify` RFC creation or bypasses its lifecycle. `ask-matt` routes correctly, indexes and plugin manifests match bucket policy, promoted docs match behavior, and `npx skills add . --list` discovers the intended catalog.
