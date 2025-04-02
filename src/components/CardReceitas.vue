<script lang="ts">
export default {
  props: {
    titulo: {
      type: String,
      required: true
    },
    imagem: {
      type: String,
      required: true
    },
    alt: {
      type: String,
      required: true
    }
  }
}
</script>

<template>
  <div class="card-receitas">
    <div class="img-container">
      <img class="img" :src="imagem" :alt="alt">
    </div>
    <p class="px-2">{{ titulo }}</p>
  </div>
</template>

<style scoped>
.card-receitas {
  /* Defina um tamanho adequado para o card */
  max-width: 282px;
  /* Ajuste conforme necessário */
  text-align: center;
  background: #000;
  border-radius: 20px;
  background-color: var(--branco);
  box-shadow: 0px 8px 5px var(--cinza-claro);

}

.img-container {
  width: 100%;
  height: 150px;
  /* Defina a altura desejada */
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
}

.img-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  /* Pode ser 'contain' se quiser exibir a imagem inteira */
  border-radius: 20px 20px 0 0;

}

.px-2 {
  padding: 2rem 0;
}
</style>