<script lang="ts">
export default {
  props: {
    texto: { type: String, requirid: true },
    ativa: Boolean 
  }
}
</script>

<template>
  <span class="tag" :class="{ ativa }">
    {{ texto }}
  </span>
</template>

<style scoped>
.tag {
  display: inline-block;
  border-radius: 0.5rem;
  min-width: 4.25rem;
  padding: 0.5rem;
  text-align: center;
  transition: 0.2s;
  color: var(--cinza);
  font-weight: 500;
}

.tag.ativa {
  color: var(--creme, #FFFAF3);
  background: var(--coral, #F0633C);
  font-weight: 700;
}
</style>