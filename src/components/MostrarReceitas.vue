<script lang="ts">
import BotaoBusca from '@/components/BotaoBusca.vue';
import CardReceitas from '@/components/CardReceitas.vue';
import type { IReceitas } from '@/interfaces/IReceitas';
import type { Pagina } from './ConteudoPrincipal.vue';
import { obterReceitas } from '@/http';

export default {
  props: {
    ingredientes: {
      type: Array as () => string[],
      required: true
    }
  },
  components: {
    BotaoBusca,
    CardReceitas,
  },
  data() {
    return {
      receitas: [] as IReceitas[],
    }
  },
  async created() {
    const receitas = await obterReceitas();

    const receitasCorrespondentes = receitas.filter(receita => this.ingredientes.every(ing => receita.ingredientes.includes(ing)));

    this.receitas = receitasCorrespondentes;
  },
}
</script>

<template>
  <main class="mostrar-receitas">
    <h1 class="cabecalho titulo-receitas">Receitas</h1>
    <p class="subtitulo-receitas">Resultados encontrados: <span>{{ receitas.length }}</span></p>
    <p v-if="receitas.length > 0">Veja as opções de receitas que encontramos com os ingredientes que você tem por aí!
    </p>
    <p v-else="receitas.length < 0">Ops, não encontramos resultados para sua combinação. Vamos tentar de novo?</p>
    <div class="receitas">
      <CardReceitas :key="receita.nome" v-if="receitas.length > 0" v-for="receita in receitas" :titulo="receita.nome"
        :imagem="`imagens/receitas/${receita.imagem}`" :alt="receita.nome" />
      <img v-else="receitas.length > 0" src="/src/assets/imagens/sem-receitas.png" alt="">
    </div>
    <BotaoBusca text="Editar lista" />
  </main>
</template>

<style scoped>
.receitas {
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  flex-wrap: wrap;
  padding-top: 2.25rem;
  padding-bottom: 3.5rem;
}

.titulo-receitas {
  color: var(--verde-medio, #3D6D4A);
  display: block;
  margin-bottom: 1.5rem;
}

.subtitulo-receitas {
  color: var(--verde-medio, #3D6D4A);
  display: block;
  margin-bottom: 0.5rem;
}

.mostrar-receitas {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>