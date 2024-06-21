<template>
  <div class="pokemonContainer">
    <img
      v-show="!mostrarPokemon"
      class="ocultapokemon"
      :src="imagenFuente"
      alt=" No hay Imagen"
    />
    <img v-show="mostrarPokemon" :src="imagenFuente" alt=" No hay Imagen" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      mostrar: false,
    };
  },
  props: {
    idPokemon: {
      type: Number,
      required: true,
    },
    mostrarPokemon: {
      type: Boolean,
      required: true,
    },
  },
  //la propiedad computad no se va a ejecutar si no cambia el cuerpo
  //toda propiedad computada debe terner un retunr
  computed: {
    imagenFuente() {
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.idPokemon}.svg`;
    },
  },
};
</script>

<style scoped>
.ocultapokemon {
  filter: brightness(0);
}
img {
  height: 200px;
  width: 200px;
  position: absolute;
  right: 45%;
}

.pokemonContainer {
  height: 200px;
}
</style>