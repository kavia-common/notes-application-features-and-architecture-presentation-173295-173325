<script setup lang="ts">
/**
 * PUBLIC_INTERFACE
 * FeatureCard renders a stylized card with an icon, title, and bullet list.
 * Props:
 * - title: string - main heading
 * - icon: string - emoji or short icon text
 * - bullets: string[] - bullet items
 */
const props = defineProps<{
  title: string
  icon?: string
  bullets?: string[] | string
}>()
</script>

<template>
  <div class="feature-card">
    <div class="eyebrow" v-if="icon">{{ icon }}</div>
    <h3 class="feature-title">{{ title }}</h3>
    <ul class="points-clean" v-if="bullets">
      <li v-for="(b, idx) in (Array.isArray(bullets) ? bullets : [bullets])" :key="idx">{{ b }}</li>
    </ul>
  </div>
</template>
