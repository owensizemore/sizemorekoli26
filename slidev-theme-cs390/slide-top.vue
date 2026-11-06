<script setup lang="ts">
import { useNav } from '@slidev/client'

const { currentPage, total } = useNav()
</script>

<template>
  <div class="venue-cutoff" />
  <div v-if="currentPage > 1" class="slide-page-number">{{ currentPage }} / {{ total }}</div>
</template>

<style scoped>
.venue-cutoff {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  height: calc(100% * var(--venue-blank));
  background: rgba(239, 68, 68, 0.18);
  border-top: 3px solid #ef4444;
  pointer-events: none;
  z-index: 50;
  opacity: var(--show-cutoff);
}

.slide-page-number {
  position: absolute;
  right: 1.5rem;
  bottom: 0.5rem;
  font-size: 0.875rem;
  opacity: calc(0.5 * var(--show-page-number));
  pointer-events: none;
  z-index: 51;
}
</style>
