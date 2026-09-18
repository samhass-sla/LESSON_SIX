<script setup lang="ts">
import { useTheme } from 'vuetify'
import { computed } from 'vue'
import LinkButton from '@/components/LinkButton.vue'

const theme = useTheme()

const links = [
  { label: 'Portfolio', url: 'https://samhassler.com', icon: 'mdi-earth' },
  { label: 'Dribbble', url: 'https://dribbble.com', icon: 'mdi-dribbble' },
  { label: 'LinkedIn', url: 'https://www.linkedin.com', icon: 'mdi-linkedin' },
  { label: 'Email', url: 'mailto:sam@example.com', icon: 'mdi-email-outline' },
]

const isDark = computed({
  get: () => theme.global.current.value.dark,
  set: (value: boolean) => {
    theme.global.name.value = value ? 'dark' : 'light'
  },
})
</script>

<template>
  <v-app>
    <v-main class="home-page d-flex align-center justify-center pa-6">
      <v-container class="py-10">
        <v-row justify="center">
          <v-col cols="12" sm="8" md="6" lg="4">
            <v-card class="home-card pa-6 text-center position-relative" rounded="xl" elevation="6">
              <button
                type="button"
                class="theme-toggle"
                :aria-label="isDark ? 'Switch to light mode' : 'Switch to dark mode'"
                @click="isDark = !isDark"
              >
                <span class="toggle-track" :class="{ dark: isDark }">
                  <span class="toggle-thumb">
                    <v-icon :icon="isDark ? 'mdi-weather-night' : 'mdi-weather-sunny'" size="12" />
                  </span>
                </span>
              </button>

              <v-avatar size="96" color="deep-purple-lighten-4" class="mb-2 text-deep-purple-darken-4 font-weight-bold">
                SH
              </v-avatar>

              <v-btn
                to="/about"
                class="mb-5 about-button"
                color="deep-purple-lighten-4"
                variant="flat"
                size="small"
                rounded="pill"
              >
                <span class="button-text">About</span>
              </v-btn>

              <h1 class="text-h4 font-weight-bold mb-2">Sam Hassler</h1>
              <p class="text-body-2 mb-4 text-medium-emphasis">
                I build digital experiences and love connecting with people.
              </p>

              <v-list class="link-list pa-0" density="comfortable" nav>
                <v-list-item v-for="link in links" :key="link.label" class="link-list-item px-0 py-3">
                  <LinkButton :label="link.label" :url="link.url" :icon="link.icon" />
                </v-list-item>
              </v-list>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<style scoped>
.home-page {
  min-height: 100vh;
  position: relative;
  overflow: hidden;
  background:
    radial-gradient(circle at 20% 15%, rgba(168, 85, 247, 0.12), transparent 22%),
    radial-gradient(circle at 75% 30%, rgba(168, 85, 247, 0.1), transparent 25%),
    radial-gradient(circle at 50% 82%, rgba(147, 197, 253, 0.12), transparent 20%),
    linear-gradient(135deg, #f7f3ff 0%, #ffffff 52%, #f9f7ff 100%);
}

.home-page::before,
.home-page::after {
  content: '';
  position: absolute;
  width: 540px;
  height: 540px;
  border-radius: 50%;
  border: 1px solid rgba(168, 85, 247, 0.12);
  pointer-events: none;
}

.home-page::before {
  top: -120px;
  left: -120px;
  background: radial-gradient(circle at center, rgba(196, 181, 253, 0.12), transparent 62%);
}

.home-page::after {
  right: -110px;
  bottom: -110px;
  background: radial-gradient(circle at center, rgba(216, 180, 254, 0.12), transparent 60%);
}

:deep(.v-card) {
  background: rgba(255, 255, 255, 0.82);
  border: 1px solid rgba(168, 85, 247, 0.12);
  box-shadow: 0 20px 60px rgba(76, 29, 149, 0.08);
}

:deep(.v-btn__content) {
  justify-content: center;
}

.theme-toggle {
  position: absolute;
  top: 14px;
  right: 14px;
  border: none;
  background: transparent;
  padding: 0;
  cursor: pointer;
}

.toggle-track {
  position: relative;
  display: inline-flex;
  align-items: center;
  width: 52px;
  height: 30px;
  border-radius: 999px;
  background: #e9d5ff;
  transition: background-color 0.25s ease;
  box-shadow: inset 0 0 0 1px rgba(109, 40, 217, 0.14);
}

.toggle-track.dark {
  background: #312e81;
}

.toggle-thumb {
  position: absolute;
  left: 4px;
  display: grid;
  place-items: center;
  width: 22px;
  height: 22px;
  border-radius: 50%;
  background: #ffffff;
  color: #6d28d9;
  box-shadow: 0 2px 8px rgba(15, 23, 42, 0.2);
  transition: transform 0.25s ease, background-color 0.25s ease, color 0.25s ease;
}

.toggle-track.dark .toggle-thumb {
  transform: translateX(22px);
  background: #1f2937;
  color: #f8fafc;
}

.about-button {
  display: flex;
  margin: 0 auto 18px;
  width: 120px;
  min-height: 36px;
  white-space: nowrap;
  color: #4c1d95 !important;
  background-color: #e9d5ff !important;
}

.link-list {
  margin-top: 6px;
}

.link-list-item {
  min-height: 0;
}

.home-link-button {
  color: #4c1d95 !important;
  background-color: #f3e8ff !important;
  transition: transform 0.18s ease, box-shadow 0.18s ease, filter 0.18s ease, background-color 0.18s ease;
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

:global(body) {
  margin: 0;
  background: linear-gradient(135deg, #f4f0ff 0%, #ffffff 46%, #f4f0ff 100%);
}

:global(.v-theme--dark body) {
  background: linear-gradient(135deg, #0f172a 0%, #111827 100%);
}

:global(.v-theme--dark .home-card) {
  background: rgba(15, 23, 42, 0.9) !important;
  border: 1px solid rgba(168, 85, 247, 0.2) !important;
  box-shadow: 0 20px 60px rgba(2, 6, 23, 0.48) !important;
}

:global(.v-theme--dark .text-medium-emphasis) {
  color: rgba(255, 255, 255, 0.7) !important;
}

:global(.v-theme--dark .home-link-button),
:global(.v-theme--dark .about-button) {
  background-color: #312e81 !important;
  color: #f8fafc !important;
}

:global(.v-theme--dark .button-text) {
  color: #f8fafc !important;
}

:global(.v-theme--dark .v-avatar) {
  background: #a78bfa !important;
  color: #111827 !important;
}
</style>
