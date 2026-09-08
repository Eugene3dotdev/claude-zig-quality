# Tiger Style policy

This repository applies [Tiger Style](https://github.com/tigerbeetle/tigerbeetle/blob/main/docs/TIGER_STYLE.md) as its common engineering policy.

## Rules must be observable

A rule is incomplete until one of these mechanisms checks it:

- a compiler, linter, or formatter rule;
- a test or reproducibility check;
- a CI gate;
- generated configuration with a documented regeneration command.

The repository must not carry duplicate policy text that can drift from the canonical source. Tool-specific documents state the enforcement point and the command that proves it.

## This template

The repository contains a reusable quality template, not a Claude-only system. Agent harness adapters live at the boundary. The quality rules and their verification do not depend on one harness.

The Zig layer applies the policy through:

- `scripts/verify-fast.ts`, `scripts/verify-commit.ts`, `scripts/verify-pr.ts`, and `scripts/verify-release.ts`;
- `scripts/zig-fitness.zig` and `scripts/zig-doc-coverage.zig`;
- `ziglint` in the commit-tier gate;
- the Zig-specific guide in `doc/TIGER_STYLE_ZIG.md`.

Before adding a rule, identify the verifier and the command that runs it. Before adding a second copy of a rule, move the shared rule to its canonical source and link to it.

## Portfolio boundary

`ziglint` stays a separate focused linter. `zigdoc` stays a separate symbol and API documentation tool. Chezmoi may project configuration into a home environment, but the repository policy and its verification remain versioned with the repository that owns them.

## Migration requirement

The current repository name, package metadata, harness-specific documentation, former-owner links, and local-machine paths remain migration work. Do not treat them as policy exceptions. Track and remove them through the portfolio Wayfinder map.