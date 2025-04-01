<script lang="ts">
import BotaoBusca from '@/components/BotaoBusca.vue';
import CardReceitas from '@/components/CardReceitas.vue';

export default {
  components: {
    BotaoBusca,
    CardReceitas
  }
}
</script>

<template>
  <main>
    <p>Resultados encontrados: <span>8</span></p>
    <p>Veja as opções de receitas que encontramos com os ingredientes que você tem por aí!</p>
    <CardReceitas />
    <BotaoBusca text="Editar lista" />
  </main>
</template>