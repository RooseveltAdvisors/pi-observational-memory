# Vision

This repository is the RooseveltAdvisors house fork of elpapi42/pi-observational-memory, the Pi extension that keeps long agent sessions coherent across compactions, handoffs, and days of work.
The upstream project's purpose is stated in its own README; this vision exists to state why the house carries a fork at all.
The captain's fleet runs its real coding work in Pi sessions that last for days or weeks, and observational memory is what keeps those sessions from losing the thread, so the fleet depends on this extension the way it depends on its own infrastructure.
It serves the captain and the coding agents who run long sessions on top of this extension.
It deliberately does not serve upstream's broader user base; upstream serves them directly, and the fork's job is to keep the fleet's dependency reviewed, tested, and understood.

## Why a fork exists

The fleet never posts work to upstream by default, so it needs its own place to validate, review, and merge changes to the extension under its own direct-PR discipline and merge authority.
Owning the fork also lets the house carry a fix on its own schedule when a defect bites a live session and the fix has not yet landed upstream.
And it lets the house document the extension's behavior at the depth an operator needs, not just a user: how provider tokens are counted, what the pool budgets mean, when each worker trigger fires.
The fork exists to be nearly empty; its value is trust in what the fleet runs, not divergence from upstream.

## What it carries beyond upstream

Today the delta is deliberately small: documentation, backed by tests, of provider token accounting and the observation pool budgets that drive the observer, reflector, dropper, and compaction triggers.
The historical pattern is the point: fixes proven here, such as accepting headers-based OAuth model auth and distinguishing observer stream failures, landed upstream until the delta shrank again.
The fork tracks upstream's master branch closely and moves forward through explicit merge pull requests, so drift never accumulates silently.
Anything that proves generally useful belongs upstream first; the fork carries it only while it waits.

## What it must never diverge on

The V3 memory model is contract, not detail: the branch-local ledger as source of truth, observations and reflections as the memory layers, coverage evidence guiding the dropper, source-backed recall by id, and no V2 compatibility layer.
The `observational-memory` settings namespace and its documented defaults must mean exactly the same thing here as upstream, so a config the captain writes keeps its meaning on both sides.
Compatibility with Pi's extension system, the `pi.extensions` entry point and its peer dependencies, is the product itself and cannot be traded away.
The MIT license, upstream attribution to elpapi42, and the credit to Mastra's observational memory research stay intact in every carried change.
Publishing to npm stays upstream's act; this fork ships through reviewed pull requests, never through a release.

## Non-goals

- Not a divergent feature fork; feature work belongs upstream.
- Not a memory database, semantic search, or transcript browser; recall recovers evidence for a known id.
- Not a V2 compatibility layer or migration service.
- Not a publisher of npm releases.

## Done well

In a year, done well looks like a delta that stays within a handful of commits: documentation and fixes either already upstreamed or waiting to be.
Upstream merges stay routine fast-forwards, and no fleet session ever runs on memory semantics that differ from what upstream documents.
The fleet's longest sessions stay coherent across compactions, and every defect the house finds in this extension becomes a fix the whole upstream community inherits.
