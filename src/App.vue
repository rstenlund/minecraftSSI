<script setup lang="ts">
import SSI from './components/SSI.vue'
import CredInput from './components/CredInput.vue'
</script>

<template>
  <header>
    <div class="wrapper">
      <SSI />
    </div>
  </header>

  <main>
    <CredInput />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
    width: 100%;
  }
}
</style>
