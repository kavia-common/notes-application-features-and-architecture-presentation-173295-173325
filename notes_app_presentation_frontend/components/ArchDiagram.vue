<script setup lang="ts">
/**
 * PUBLIC_INTERFACE
 * ArchDiagram renders a simple architecture diagram for the Notes app using inline SVG.
 * Shows Client, API Gateway, Services (Notes, Search, Realtime), and Data Stores.
 */
</script>

<template>
  <div class="card">
    <div class="eyebrow">High-Level Architecture</div>
    <div class="glass-frame">
      <svg viewBox="0 0 800 340" width="100%" height="260" role="img" aria-label="Architecture Diagram">
        <!-- Styles -->
        <defs>
          <linearGradient id="g1" x1="0" y1="0" x2="1" y2="1">
            <stop offset="0%" stop-color="#2563EB" stop-opacity="0.25" />
            <stop offset="100%" stop-color="#ffffff" stop-opacity="0.06" />
          </linearGradient>
          <style>
            .node { fill: rgba(255,255,255,0.06); stroke: #4b5563; }
            .label { fill: #E5E7EB; font: 600 12px Inter, sans-serif; }
            .line { stroke: #6B7280; stroke-width: 2; marker-end: url(#arrow); }
          </style>
          <marker id="arrow" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
            <path d="M 0 0 L 10 5 L 0 10 z" fill="#6B7280"></path>
          </marker>
        </defs>

        <!-- Background -->
        <rect x="0" y="0" width="800" height="340" fill="url(#g1)" rx="12" />

        <!-- Nodes -->
        <rect class="node" x="40"  y="40"  rx="10" ry="10" width="150" height="56" />
        <text class="label" x="115" y="72" text-anchor="middle">Client (Web/Mobile)</text>

        <rect class="node" x="260" y="40"  rx="10" ry="10" width="150" height="56" />
        <text class="label" x="335" y="72" text-anchor="middle">API Gateway</text>

        <rect class="node" x="480" y="24"  rx="10" ry="10" width="140" height="44" />
        <text class="label" x="550" y="50" text-anchor="middle">Notes Svc</text>

        <rect class="node" x="480" y="84"  rx="10" ry="10" width="140" height="44" />
        <text class="label" x="550" y="110" text-anchor="middle">Search Svc</text>

        <rect class="node" x="640" y="54"  rx="10" ry="10" width="120" height="44" />
        <text class="label" x="700" y="80" text-anchor="middle">Realtime</text>

        <rect class="node" x="280" y="200" rx="10" ry="10" width="150" height="56" />
        <text class="label" x="355" y="232" text-anchor="middle">Auth (OIDC)</text>

        <rect class="node" x="480" y="190" rx="10" ry="10" width="140" height="44" />
        <text class="label" x="550" y="216" text-anchor="middle">DB (Postgres)</text>

        <rect class="node" x="640" y="190" rx="10" ry="10" width="120" height="44" />
        <text class="label" x="700" y="216" text-anchor="middle">Search (ES)</text>

        <!-- Edges -->
        <line class="line" x1="190" y1="68" x2="260" y2="68" />
        <line class="line" x1="410" y1="68" x2="480" y2="46" />
        <line class="line" x1="410" y1="68" x2="480" y2="106" />
        <line class="line" x1="620" y1="76" x2="640" y2="76" />
        <line class="line" x1="550" y1="68" x2="550" y2="190" />
        <line class="line" x1="550" y1="128" x2="550" y2="190" />
        <line class="line" x1="335" y1="96" x2="355" y2="200" />
      </svg>
    </div>
  </div>
</template>
