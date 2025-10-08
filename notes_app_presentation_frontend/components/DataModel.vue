<script setup lang="ts">
/**
 * PUBLIC_INTERFACE
 * DataModel renders an at-a-glance schema for core entities: Note, Folder, Tag, Share.
 */
</script>

<template>
  <div class="card">
    <div class="eyebrow">Schema</div>
    <h3 class="feature-title">Core Entities</h3>
    <div class="split-cols mt-1">
      <div>
        <div class="feature-card">
          <h4 class="feature-title">Note</h4>
          <ul class="points-clean">
            <li>id (ULID), title, content (markdown/json)</li>
            <li>folder_id (nullable), created_at, updated_at</li>
            <li>tags: string[]</li>
            <li>owner_id</li>
          </ul>
        </div>
        <div class="feature-card">
          <h4 class="feature-title">Folder</h4>
          <ul class="points-clean">
            <li>id, name, owner_id</li>
            <li>parent_id (nullable)</li>
          </ul>
        </div>
      </div>
      <div>
        <div class="feature-card">
          <h4 class="feature-title">Share</h4>
          <ul class="points-clean">
            <li>id, resource_type ("note"|"folder"), resource_id</li>
            <li>subject_type ("user"|"team"), subject_id</li>
            <li>role ("viewer"|"commenter"|"editor"|"owner")</li>
          </ul>
        </div>
        <div class="feature-card">
          <h4 class="feature-title">Index</h4>
          <ul class="points-clean">
            <li>note_id → searchable text & tags</li>
            <li>updated_at cursor for sync</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
