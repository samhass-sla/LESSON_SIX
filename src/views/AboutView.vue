<script setup lang="ts">
const highlights = [
  'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
  'Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.',
  'Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris.',
  'Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore.',
]
</script>

<template>
  <main class="about-page">
    <section class="about-card">
      <div class="profile-wrap">
        <div class="profile-photo" aria-label="Profile photo placeholder">SH</div>
      </div>

      <div class="content">
        <p class="eyebrow">About</p>
        <h1>Sam Hassler</h1>

        <p class="bio">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum nec velit nec nisi
          vulputate volutpat. Curabitur ac eros non sapien posuere feugiat. Integer et convallis
          metus, ac vestibulum nisl. Integer dapibus volutpat dolor, a laoreet ligula rutrum et.
        </p>

        <ul class="highlights">
          <li v-for="highlight in highlights" :key="highlight">{{ highlight }}</li>
        </ul>
      </div>
    </section>
  </main>
</template>

<style scoped>
.about-page {
  min-height: 100vh;
  display: grid;
  place-items: center;
  padding: 32px 20px;
  background:
    radial-gradient(circle at 20% 15%, rgba(168, 85, 247, 0.12), transparent 22%),
    radial-gradient(circle at 75% 30%, rgba(168, 85, 247, 0.10), transparent 25%),
    radial-gradient(circle at 50% 82%, rgba(147, 197, 253, 0.12), transparent 20%),
    linear-gradient(135deg, #f7f3ff 0%, #ffffff 52%, #f9f7ff 100%);
  position: relative;
  overflow: hidden;
}

.about-page::before,
.about-page::after {
  content: '';
  position: absolute;
  inset: auto;
  width: 540px;
  height: 540px;
  border-radius: 50%;
  border: 1px solid rgba(168, 85, 247, 0.12);
  pointer-events: none;
}

.about-page::before {
  top: -120px;
  left: -120px;
  background: radial-gradient(circle at center, rgba(196, 181, 253, 0.12), transparent 62%);
}

.about-page::after {
  right: -110px;
  bottom: -110px;
  background: radial-gradient(circle at center, rgba(216, 180, 254, 0.12), transparent 60%);
}

.about-card {
  position: relative;
  z-index: 1;
  width: min(100%, 860px);
  display: grid;
  grid-template-columns: 220px 1fr;
  gap: 28px;
  align-items: center;
  background: rgba(255, 255, 255, 0.8);
  border: 1px solid rgba(168, 85, 247, 0.12);
  border-radius: 28px;
  box-shadow: 0 20px 60px rgba(76, 29, 149, 0.08);
  padding: 32px;
}

.profile-wrap {
  display: flex;
  justify-content: center;
}

.profile-photo {
  width: 180px;
  height: 180px;
  border-radius: 50%;
  background: linear-gradient(135deg, #ddd6fe, #f5f3ff);
  display: grid;
  place-items: center;
  font-weight: 800;
  font-size: 2.2rem;
  letter-spacing: 0.08em;
  color: #4c1d95;
  border: 4px solid rgba(255, 255, 255, 0.9);
  box-shadow: 0 14px 30px rgba(109, 40, 217, 0.12);
}

.content {
  text-align: left;
}

.eyebrow {
  margin: 0 0 8px;
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  color: #7c3aed;
  font-weight: 700;
}

h1 {
  margin: 0 0 16px;
  font-size: clamp(2.2rem, 4vw, 3.2rem);
  line-height: 1.1;
  color: #111827;
}

.bio {
  margin: 0 0 20px;
  font-size: 1rem;
  line-height: 1.8;
  color: #374151;
}

.highlights {
  margin: 0;
  padding-left: 1.25rem;
  display: grid;
  gap: 10px;
  color: #374151;
  line-height: 1.6;
}

@media (max-width: 720px) {
  .about-card {
    grid-template-columns: 1fr;
    text-align: center;
    padding: 28px 20px;
  }

  .content {
    text-align: center;
  }

  .highlights {
    text-align: left;
  }
}
</style>
