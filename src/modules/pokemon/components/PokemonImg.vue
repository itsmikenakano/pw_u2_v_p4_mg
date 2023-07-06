<template>
  <div class="contenedor-imagen">
    <img
      class="oculta-pokemon"
      :src="imagenFuente"
      alt="No se puede mostrar la imagen"
    />
    <img
      v-if="muestraPokemon"
      :src="imagenFuente"
      alt="No se puede mostrar la imagen"
    />
  </div>
</template>

<script>
export default {
  props: {
    pokemonId: {
      type: Number,
      required: true,
    },

    muestraPokemon: {
      type: Boolean,
      required: true,
    },
  },

  computed: {
    imagenFuente() {
      console.log("Hola esta es una propiedad computada");
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`;
    },
  },
};
</script>

<style scope>
.oculta-pokemon {
  filter: brightness(0);
}

img {
  position: absolute;
  height: 200px;
  right: 41%;
}

.contenedor-imagen {
  height: 200px;
}
</style>