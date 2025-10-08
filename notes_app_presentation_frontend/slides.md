---
# Global deck settings
theme: default
title: "Nimbus Notes — Features & Architecture"
info: |
  Ocean Professional themed presentation for the Nimbus Notes application.
  Sections: Title, Agenda, Problem & Goals, Key Features, Architecture, Data Model,
  API/Flows, UI/UX Demo, Security, Performance, Roadmap, Q&A.
class: text-left
mdc: true
transition: slide-left
fonts:
  sans: Inter, ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Helvetica Neue, Arial
  mono: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace
css: |
  @import "./style.css";
---

# Nimbus Notes
<div class="title-slide with-hero-glow">
  <img src="/logo.svg" alt="Nimbus Notes" class="logo" />
  <div class="hero-copy">
    <h2 class="text-hero">Fast. Secure. Delightful Note‑Taking.</h2>
    <p class="subtitle text-md">Organize ideas, collaborate in real-time, and sync across devices</p>
    <div class="subtitle text-xs">Presented by: Product & Engineering • 2025</div>
    <div class="hero-ctas mt-2">
      <button class="btn-primary">Live Demo</button>
      <button class="btn-secondary">Docs</button>
    </div>
  </div>
</div>

<!-- Presenter Notes -->
Notes:
- Welcome and intro to Nimbus Notes.
- Emphasize Ocean Professional aesthetics and cross‑platform sync.

---

# Agenda

- Problem & Goals
- Key Features
- Architecture Overview
- Data Model
- API & Flows
- UI/UX Demo Screens
- Security & Permissions
- Performance
- Roadmap
- Q&A

Notes:
- Set expectations for the flow and outcomes.

---

# Problem & Goals

<div class="problem-grid">
  <div class="problem-card">
    <div class="eyebrow">Problem</div>
    <h3 class="feature-title">Note Chaos</h3>
    <ul class="points-clean">
      <li>Scattered notes across devices and apps</li>
      <li>Poor searchability and organization</li>
      <li>Hard to share and collaborate securely</li>
    </ul>
  </div>
  <div class="problem-card">
    <div class="eyebrow">Vision</div>
    <h3 class="feature-title">Unified Knowledge</h3>
    <ul class="points-clean">
      <li>One place for all notes and tasks</li>
      <li>Fast, offline-first, real-time collaboration</li>
      <li>Granular permissions and enterprise security</li>
    </ul>
  </div>
  <div class="problem-card">
    <div class="eyebrow">Goals</div>
    <h3 class="feature-title">Measurable Outcomes</h3>
    <ul class="points-clean">
      <li><strong>2x</strong> faster capture and retrieval</li>
      <li><strong>95%</strong> search success rate</li>
      <li>Zero‑trust sharing model</li>
    </ul>
  </div>
</div>

Notes:
- Tie goals to measurable KPIs (speed, search success, security posture).

---

# Key Features

<div class="card-grid three mt-2">
  <FeatureCard title="Rich Editor" icon="📝"
    :bullets='["Markdown + WYSIWYG", "Slash commands", "Embeds & attachments"]' />
  <FeatureCard title="Organization" icon="🗂️"
    :bullets='["Folders & tags", "Pinned notes", "Smart filters"]' />
  <FeatureCard title="Search" icon="🔎"
    :bullets='["Full-text & tag search", "Filters", "Saved queries"]' />

  <FeatureCard title="Collaboration" icon="🤝"
    :bullets='["Live cursors", "Comments & mentions", "Version history"]' />
  <FeatureCard title="Sync" icon="🔄"
    :bullets='["Offline-first", "Delta sync", "Conflict resolution"]' />
  <FeatureCard title="Security" icon="🔐"
    :bullets='["E2E encryption (optional)", "RBAC", "Audit logs"]' />
</div>

Notes:
- Show breadth with depth: editor, org, search, collab, sync, security.

---

# Architecture Overview

<ArchDiagram />

Notes:
- Explain client-heavy approach with API gateway and modular services.
- Mention WebSocket for presence and CRDT/OT for real-time editing.

---

# Data Model

<DataModel />

Notes:
- Keep model minimal but extensible (custom metadata, tags).
- IDs are ULIDs to preserve temporal ordering and uniqueness.

---

# API & Flows

<div class="card grid-2 mt-2">
  <div>
    <div class="eyebrow">Create & Edit</div>
    <ul class="points-clean">
      <li>POST /api/notes — create note</li>
      <li>PATCH /api/notes/{id} — update content/metadata</li>
      <li>PUT /api/notes/{id}/share — share with users/teams</li>
    </ul>

    <div class="eyebrow mt-1">Sync</div>
    <ul class="points-clean">
      <li>GET /api/sync/notes?cursor=... — incremental fetch</li>
      <li>WS /realtime — presence, comments, edits</li>
    </ul>

    <div class="eyebrow mt-1">Search</div>
    <ul class="points-clean">
      <li>GET /api/search?q=...&tags=... — full-text + filters</li>
    </ul>
  </div>
  <div>
    <div class="glass-frame tall">
      <div class="placeholder">Sequence Diagram: Edit → Sync → Broadcast</div>
    </div>
  </div>
</div>

Notes:
- Stress pagination via cursor, delta sync, idempotent updates.

---

# UI/UX Demo Screens

<div class="card-grid three mt-2">
  <div class="feature-card">
    <div class="eyebrow">Home</div>
    <h3 class="feature-title">Notebook Overview</h3>
    <ul class="points-clean">
      <li>Recent notes, starred, quick capture</li>
      <li>Global search input</li>
    </ul>
  </div>
  <div class="feature-card">
    <div class="eyebrow">Editor</div>
    <h3 class="feature-title">Rich Content Editing</h3>
    <ul class="points-clean">
      <li>Markdown + toolbar</li>
      <li>Comments and mentions</li>
    </ul>
  </div>
  <div class="feature-card">
    <div class="eyebrow">Sharing</div>
    <h3 class="feature-title">Granular Permissions</h3>
    <ul class="points-clean">
      <li>Viewer/Commenter/Editor/Owner</li>
      <li>Link-based and domain-based</li>
    </ul>
  </div>
</div>

Notes:
- These are conceptual mockups—focus on information hierarchy.

---

# Security & Permissions

<div class="card-grid three mt-2">
  <div class="feature-card">
    <div class="eyebrow">AuthN/Z</div>
    <ul class="points-clean">
      <li>OIDC / OAuth 2.1, optional SSO/SAML</li>
      <li>RBAC with roles: viewer, commenter, editor, owner</li>
    </ul>
  </div>
  <div class="feature-card">
    <div class="eyebrow">Data Protection</div>
    <ul class="points-clean">
      <li>At-rest AES-256, in-transit TLS 1.3</li>
      <li>Optional E2EE for private spaces</li>
    </ul>
  </div>
  <div class="feature-card">
    <div class="eyebrow">Compliance</div>
    <ul class="points-clean">
      <li>GDPR, SOC 2 Type II</li>
      <li>Audit trails & retention policies</li>
    </ul>
  </div>
</div>

Notes:
- Clarify E2EE trade-offs with server-side search and collaboration.

---

# Performance

<div class="stats-grid mt-2">
  <div class="stat-card">
    <div class="stat-number">50ms</div>
    <div class="stat-label">Editor TTI</div>
  </div>
  <div class="stat-card">
    <div class="stat-number">p95&lt;200ms</div>
    <div class="stat-label">API Latency</div>
  </div>
  <div class="stat-card">
    <div class="stat-number">99.95%</div>
    <div class="stat-label">Uptime</div>
  </div>
</div>

- Offline caching with IndexedDB
- Streaming renders for large docs
- Incremental search indexing
- Lightweight delta protocol for sync

Notes:
- Mention edge caching and CDN for static/editor bundles.

---

# Roadmap

<div class="timeline mt-2">
  <div class="time-node">
    <div class="time-dot"></div>
    <div class="time-card">
      <div class="eyebrow">Q1</div>
      <ul class="points-clean">
        <li>MVP: editor, folders, basic search</li>
        <li>Local encryption, device sync</li>
      </ul>
    </div>
  </div>
  <div class="time-node">
    <div class="time-dot"></div>
    <div class="time-card">
      <div class="eyebrow">Q2</div>
      <ul class="points-clean">
        <li>Collaboration: comments, presence</li>
        <li>Mobile apps (iOS/Android)</li>
      </ul>
    </div>
  </div>
  <div class="time-node">
    <div class="time-dot future"></div>
    <div class="time-card">
      <div class="eyebrow">Q3+</div>
      <ul class="points-clean">
        <li>AI: summaries, smart tags, Q&A over notes</li>
        <li>Enterprise: SSO, DLP, Admin APIs</li>
      </ul>
    </div>
  </div>
</div>

Notes:
- Align roadmap with customer feedback loops and analytics.

---

layout: center
class: text-center
---

# Q&A

Ask us anything.

<div class="mt-4 subtle">Press S for presenter mode • Use arrow keys to navigate</div>
