<script lang="ts">
import type { Pagina } from './ConteudoPrincipal.vue';
import type { PropType } from 'vue';

export default {
  props: {
    redirecionar: {
      type: Function as PropType<(pagina: Pagina) => void>,
      required: false
    },
    text: {
      type: String,
      required: true
    }
  },
  methods: {
    handleClick() {
      if (this.redirecionar)
        this.redirecionar('MostrarReceitas');
    }
  }
}
</script>

<template>
  <button class="botao-busca" @click="handleClick">
    {{ text }}
  </button>
</template>

<style scoped>
.botao-busca {
  background-color: var(--coral);
  color: var(--branco);
  font-size: 1.25rem;
  font-weight: 700;
  padding: 0.75rem 4.6875rem;
  border-radius: 3.125rem;
  cursor: pointer;
}
</style>