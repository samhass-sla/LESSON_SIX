<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps<{
  label: string
  url: string
  icon: string
}>()

const isExternal = computed(() => props.url.startsWith('http') || props.url.startsWith('mailto:'))
</script>

<template>
  <v-btn
    :href="url"
    :aria-label="label"
    block
    rounded="lg"
    color="purple-lighten-5"
    variant="flat"
    :target="isExternal ? '_blank' : undefined"
    :rel="isExternal ? 'noopener noreferrer' : undefined"
    class="home-link-button"
  >
    <v-icon :icon="icon" class="link-icon" />
    <span class="button-text">{{ label }}</span>
  </v-btn>
</template>

<style scoped>
.link-icon {
  margin-right: 0;
}

.home-link-button {
  color: #4c1d95 !important;
  background-color: #f3e8ff !important;
  transition: transform 0.18s ease, box-shadow 0.18s ease, filter 0.18s ease, background-color 0.18s ease;
}

:deep(.v-btn__content) {
  gap: 10px;
}

.home-link-button:hover {
  transform: translateY(-2px) scale(1.01);
  box-shadow: 0 12px 26px rgba(109, 40, 217, 0.18);
  filter: brightness(1.02);
}

.home-link-button:active {
  transform: translateY(0) scale(0.98);
}

.button-text {
  color: #4c1d95;
  font-weight: 700;
}

:global(.v-theme--dark .home-link-button) {
  background-color: #312e81 !important;
  color: #f8fafc !important;
}

:global(.v-theme--dark .button-text) {
  color: #f8fafc !important;
}
</style>
