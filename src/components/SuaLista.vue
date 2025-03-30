<script lang="ts">
import Tag from '@/components/Tag.vue'
export default {
  components: {
    Tag
  },
  props: {
    ingredientes: {
      type: Array as () => string[],
      required: true
    }
  },
}
</script>

<template>
  <section>
    <span class="subtitulo-lg sua-lista-texto">
      Sua lista:
    </span>
    <ul v-if="ingredientes.length" class="ingredientes-sua-lista">
      <!-- <li v-for="ingrediente in ingredientes" v-bind:key="ingrediente" class="ingrediente"> -->
      <li v-for="ingrediente in ingredientes" :key="ingrediente">
        <!-- :key="ingrediente" é a mesma coisa que v-bind:key="ingrediente" -->
        <Tag :texto="ingrediente" ativa />
      </li>
    </ul>
    <p v-else class="paragrafo lista-vazia">
      <img src="../assets/imagens/icone-lista-vazia.svg" alt="sem receita">
      Sua lista está vazia, selecione ingredientes para iniciar.
    </p>
  </section>
</template>

<style>
.sua-lista-texto {
  color: var(--coral, #F0633C);
  display: block;
  text-align: center;
  margin-bottom: 1.5rem;
}

.lista-vazia {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.25rem;

  color: var(--coral, #F0633C);
  text-align: center;
}

.ingredientes-sua-lista {
  display: flex;
  justify-content: center;
  gap: 1rem 1.5rem;
  flex-wrap: wrap;
}
</style>