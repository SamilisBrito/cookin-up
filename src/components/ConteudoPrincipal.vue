<script lang="ts">
import SelecionarIngredientes from '@/components/SelecionarIngredientes.vue';
import SuaLista from '@/components/SuaLista.vue';
import BotaoBusca from '@/components/BotaoBusca.vue';
import Footer from '@/components/Footer.vue';
import MostrarReceitas from './MostrarReceitas.vue';

export type Pagina = 'SelecionarIngredientes' | 'MostrarReceitas'

export default {
  components: {
    SelecionarIngredientes,
    SuaLista,
    BotaoBusca,
    Footer,
    MostrarReceitas
  },
  data() {
    return {
      ingredientes: [] as string[],
      conteudo: 'SelecionarIngredientes' as Pagina,
    }
  },
  methods: {
    adicionarIngrediente(ingrediente: string) {
      this.ingredientes.push(ingrediente);
    },
    removerIngrediente(ingrediente: string) {
      this.ingredientes = this.ingredientes.filter(i => i !== ingrediente);
    },
    redirecionar(pagina: Pagina) {
      this.conteudo = pagina;
    }
  }
}
</script>

<template>
  <main class="conteudo-principal">
    <SuaLista :ingredientes="ingredientes" />
    <SelecionarIngredientes v-if="conteudo === 'SelecionarIngredientes'" @adicionar-ingrediente="adicionarIngrediente"
      @remover-ingrediente="removerIngrediente" />
    <MostrarReceitas v-else-if="conteudo === 'MostrarReceitas'" :ingredientes="ingredientes" :redirecionar="redirecionar"/>
    <BotaoBusca v-if="conteudo === 'SelecionarIngredientes' && ingredientes.length > 0" :redirecionar="redirecionar" conteudo="MostrarReceitas" :text="' Buscar receitas!'" />
  </main>
  <Footer />
</template>

<style scoped>
.conteudo-principal {
  padding: 6.5rem 7.5rem;
  border-radius: 3.75rem 3.75rem 0rem 0rem;
  background: var(--creme, #FFFAF3);
  color: var(--cinza, #444);

  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5rem;
}

@media only screen and (max-width: 1300px) {
  .conteudo-principal {
    padding: 5rem 3.75rem;
    gap: 3.5rem;
  }
}

@media only screen and (max-width: 767px) {
  .conteudo-principal {
    padding: 4rem 1.5rem;
    gap: 4rem;
  }
}
</style>