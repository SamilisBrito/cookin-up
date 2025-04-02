<script lang="ts">
import BotaoBusca from '@/components/BotaoBusca.vue';
import CardReceitas from '@/components/CardReceitas.vue';
import { obterReceitas } from '@/http';
import type { IReceitas } from '@/interfaces/IReceitas';
import type { Pagina } from './ConteudoPrincipal.vue';

export default {
  components: {
    BotaoBusca,
    CardReceitas
  },
  data() {
    return {
      receitas: [] as IReceitas[],
      conteudo: 'SelecionarIngredientes' as Pagina,
    }
  },
  async created() {
    this.receitas = await obterReceitas();
  },
  methods:{
    redirecionar(pagina: Pagina) {
      this.conteudo = pagina;
    }
  }
}
</script>

<template>
  <main class="mostrar-receitas">
    <h1 class="cabecalho titulo-receitas">Receitas</h1>
    <p class="subtitulo-receitas">Resultados encontrados: <span>{{ receitas.length }}</span></p>
    <p>Veja as opções de receitas que encontramos com os ingredientes que você tem por aí!</p>
    <div class="receitas">
      <CardReceitas v-for="receita in receitas" :titulo="receita.nome" :imagem="`imagens/receitas/${receita.imagem}`" :alt="receita.nome" />
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