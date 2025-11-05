<script setup lang="ts"></script>

<template>
  <div class="ssi-component">
    <div class="txts">
      <h2>Minecraft SSI Tjänst</h2>
      <h3>Verifiera din identitet här</h3>
    </div>
  </div>
</template>

<style scoped>
.ssi-component {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-bottom: 1.5rem;
}

.ssi-component h2 {
  width: 100%;
  font-size: 2rem;
  color: #ffffff;
  text-align: right;
}

.ssi-component h3 {
  width: 100%;
  font-size: 1.2rem;
  color: #dddddd;
  text-align: center;
  margin-top: 0;
}

@media (min-width: 1024px) {
  .ssi-component {
    align-items: flex-end;
    padding-right: 15mm;
    margin-bottom: 0;
  }
}
</style>
