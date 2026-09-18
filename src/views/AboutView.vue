<script setup lang="ts">
const highlights = [
  'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
  'Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.',
  'Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris.',
  'Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore.',
]
</script>

<template>
  <v-app>
    <v-main class="about-page d-flex align-center justify-center pa-6">
      <v-container class="py-10">
        <v-row justify="center">
          <v-col cols="12" md="10" lg="8">
            <v-card class="about-card pa-6 pa-md-8 position-relative" rounded="xl" elevation="6">
              <v-btn
                to="/"
                class="about-home-button"
                color="deep-purple-lighten-4"
                variant="flat"
                size="small"
                rounded="pill"
              >
                <span class="about-home-button-text">Home</span>
              </v-btn>

              <v-row align="center" no-gutters>
                <v-col cols="12" md="4" class="d-flex justify-center mb-6 mb-md-0 pt-5 pt-md-2">
                  <v-avatar size="180" color="deep-purple-lighten-4" class="profile-photo text-deep-purple-darken-4 font-weight-bold">
                    SH
                  </v-avatar>
                </v-col>

                <v-col cols="12" md="8" class="pl-md-6 pt-1">
                  <p class="text-overline text-deep-purple-darken-2 mb-2">About</p>
                  <h1 class="text-h3 font-weight-bold mb-4">Sam Hassler</h1>

                  <p class="text-body-1 mb-4 text-medium-emphasis">
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum nec velit nec
                    nisi vulputate volutpat. Curabitur ac eros non sapien posuere feugiat. Integer et
                    convallis metus, ac vestibulum nisl. Integer dapibus volutpat dolor, a laoreet
                    ligula rutrum et.
                  </p>

                  <v-list class="pa-0" density="comfortable">
                    <v-list-item v-for="highlight in highlights" :key="highlight" class="px-0 py-1">
                      <template #prepend>
                        <v-icon icon="mdi-check-circle" color="deep-purple-darken-2" />
                      </template>
                      <v-list-item-title class="text-body-2 text-medium-emphasis">
                        {{ highlight }}
                      </v-list-item-title>
                    </v-list-item>
                  </v-list>
                </v-col>
              </v-row>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<style scoped>
.about-page {
  min-height: 100vh;
  position: relative;
  overflow: hidden;
  background:
    radial-gradient(circle at 20% 15%, rgba(168, 85, 247, 0.12), transparent 22%),
    radial-gradient(circle at 75% 30%, rgba(168, 85, 247, 0.1), transparent 25%),
    radial-gradient(circle at 50% 82%, rgba(147, 197, 253, 0.12), transparent 20%),
    linear-gradient(135deg, #f7f3ff 0%, #ffffff 52%, #f9f7ff 100%);
}

.about-page::before,
.about-page::after {
  content: '';
  position: absolute;
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
  background: rgba(255, 255, 255, 0.82);
  border: 1px solid rgba(168, 85, 247, 0.12);
  box-shadow: 0 20px 60px rgba(76, 29, 149, 0.08);
  padding-top: 3.5rem;
}

.about-home-button {
  position: absolute;
  top: 18px;
  left: 18px;
  min-width: 96px;
  background-color: #e9d5ff !important;
  color: #4c1d95 !important;
}

.about-home-button-text {
  color: #4c1d95;
  font-weight: 700;
}

.profile-photo {
  border: 4px solid rgba(255, 255, 255, 0.9);
  box-shadow: 0 14px 30px rgba(109, 40, 217, 0.12);
  font-size: 2.2rem;
  letter-spacing: 0.08em;
}

:global(body) {
  margin: 0;
}
</style>
