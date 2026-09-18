<script setup lang="ts">
import { ref } from 'vue'
import { RouterLink } from 'vue-router'

const isDark = ref(false)

const links = [
  { label: 'Portfolio', href: 'https://samhassler.com', ariaLabel: 'Visit my portfolio' },
  { label: 'Dribbble', href: 'https://dribbble.com', ariaLabel: 'Visit my Dribbble' },
  { label: 'LinkedIn', href: 'https://www.linkedin.com', ariaLabel: 'Visit my LinkedIn' },
  { label: 'Email', href: 'mailto:sam@example.com', ariaLabel: 'Send me an email' },
]

function toggleTheme() {
  isDark.value = !isDark.value
}
</script>

<template>
  <main :class="['page-shell', { dark: isDark }]">
    <div class="card">
      <button class="theme-toggle" type="button" @click="toggleTheme" aria-label="Toggle color theme">
        {{ isDark ? 'Light mode' : 'Dark mode' }}
      </button>

      <div class="avatar" aria-label="Profile photo placeholder">SH</div>

      <RouterLink to="/about" class="about-button">About</RouterLink>

      <h1>Sam Hassler</h1>
      <p class="tagline">I build digital experiences and love connecting with people.</p>

      <nav class="link-stack" aria-label="Social links">
        <a
          v-for="link in links"
          :key="link.label"
          :href="link.href"
          :aria-label="link.ariaLabel"
          class="link-button"
          target="_blank"
          rel="noopener noreferrer"
        >
          {{ link.label }}
        </a>
      </nav>
    </div>
  </main>
</template>

<style scoped>
.page-shell {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 24px;
  background: #f4f5f7;
  color: #1f2937;
  transition: background-color 0.25s ease, color 0.25s ease;
}

.page-shell.dark {
  background: #111827;
  color: #f9fafb;
}

.card {
  position: relative;
  width: min(100%, 480px);
  background: rgba(255, 255, 255, 0.9);
  border: 1px solid rgba(148, 163, 184, 0.25);
  border-radius: 28px;
  box-shadow: 0 20px 50px rgba(15, 23, 42, 0.08);
  padding: 32px 20px 24px;
  text-align: center;
}

.dark .card {
  background: rgba(17, 24, 39, 0.9);
  border-color: rgba(148, 163, 184, 0.25);
  box-shadow: 0 20px 50px rgba(2, 6, 23, 0.5);
}

.theme-toggle {
  position: absolute;
  top: 18px;
  right: 18px;
  border: 1px solid rgba(148, 163, 184, 0.5);
  background: transparent;
  color: inherit;
  border-radius: 999px;
  padding: 8px 12px;
  font-size: 0.75rem;
  font-weight: 600;
  cursor: pointer;
  transition: transform 0.2s ease, background-color 0.2s ease;
}

.theme-toggle:hover {
  transform: translateY(-1px);
  background: rgba(148, 163, 184, 0.1);
}

.avatar {
  width: 100px;
  height: 100px;
  margin: 12px auto 18px;
  border-radius: 50%;
  background: linear-gradient(135deg, #9ca3af, #d1d5db);
  display: grid;
  place-items: center;
  font-weight: 800;
  letter-spacing: 0.08em;
  font-size: 1.5rem;
  color: #111827;
}

h1 {
  margin: 0;
  font-size: clamp(2rem, 6vw, 2.5rem);
  line-height: 1.1;
}

.tagline {
  margin: 10px auto 0;
  max-width: 300px;
  font-size: 0.96rem;
  color: inherit;
  opacity: 0.8;
}

.about-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  align-self: center;
  width: 120px;
  min-height: 36px;
  margin: 0 auto 18px;
  border-radius: 999px;
  background: #0f172a;
  color: #ffffff;
  text-decoration: none;
  font-size: 0.82rem;
  font-weight: 700;
  letter-spacing: 0.02em;
  transition: transform 0.2s ease, box-shadow 0.2s ease, opacity 0.2s ease;
  box-shadow: 0 10px 20px rgba(15, 23, 42, 0.18);
}

.link-stack {
  margin-top: 24px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.link-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  min-height: 52px;
  border-radius: 14px;
  text-decoration: none;
  font-weight: 700;
  color: #111827;
  background: #edf2ff;
  border: 1px solid rgba(59, 130, 246, 0.14);
  transition:
    transform 0.2s ease,
    box-shadow 0.2s ease,
    background-color 0.2s ease;
  box-shadow: 0 8px 20px rgba(59, 130, 246, 0.08);
  animation: button-bounce 0.2s ease;
}

.about-button:hover,
.link-button:hover {
  transform: translateY(-2px);
}

.page-shell.dark .link-button {
  background: rgba(148, 163, 184, 0.12);
  color: #f9fafb;
  border-color: rgba(148, 163, 184, 0.18);
}

.link-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 12px 24px rgba(59, 130, 246, 0.12);
}

.link-button:active {
  animation: button-bounce 0.3s ease;
}

@keyframes button-bounce {
  0% { transform: scale(1); }
  30% { transform: scale(0.97); }
  60% { transform: scale(1.02); }
  100% { transform: scale(1); }
}

@media (max-width: 480px) {
  .card {
    padding: 28px 16px 18px;
    border-radius: 22px;
  }

  .theme-toggle {
    top: 12px;
    right: 12px;
  }
}
</style>
