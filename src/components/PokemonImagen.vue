<template>
  <div class="pokemonContainer">
    <img
      v-show="!mostrar"
      class="ocultapokemon"
      src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/1.svg"
      alt=" No hay Imagen"
    />
    <img
      v-show="mostrar"
      src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/1.svg"
      alt=" No hay Imagen"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      mostarr: true,
    };
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

.pokemonContainer{
    height: 200px;
}
</style>