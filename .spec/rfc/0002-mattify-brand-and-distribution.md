# RFC 0002: Mattify identity and distribution (child of 0001)

**Status:** Approved

**Parent:** [0001](0001-mattify-rfc-first-skills.md)

## Summary

Rebrand active product surfaces and distribution metadata as Mattify, with `borg0ai/mattify` as canonical source repository. Preserve historical attribution and links whose purpose is to identify upstream work.

## Problem

Current install instructions and package metadata still point at `mattpocock/skills`, while the product is being rebuilt as Mattify in `borg0ai/mattify`. Users can install the wrong repository and encounter outdated product naming.

## Goals

Update active product names, package and marketplace identifiers, repository URLs, installation instructions, and owned links to Mattify. Rename active skill identifiers that embed the old product name and update every reference, metadata entry, docs page, and router entry affected by those renames.

## Non-goals

Changing skill behavior or reorganizing skill flows belongs to RFC 0003. Do not rewrite third-party authorship, historical changelog entries, or links used to cite original upstream issues and commits.

## Design

Use `borg0ai/mattify` for active repository and skills.sh source references. Update `package.json`, its lockfile, plugin and marketplace manifests, README and canonical install block, skill directories and cross-references, bucket indexes, docs, and `ask-matt` routing where active names change. Keep author/legal attribution and historical records truthful. Do not change Git remotes or publish externally as part of implementation.

## Acceptance

Repository-wide search finds no stale old-brand active identifiers or install sources; retained old references are historical, legal, or explicit upstream attribution. `npx skills add borg0ai/mattify --list` discovers the intended set. Plugin manifests validate, install instructions match `.agents/install-block.md`, and all promoted skill references remain consistent.
