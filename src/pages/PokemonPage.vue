<template>
  <h1>Selecciona el pokemon Correcto</h1>
  <PokemonImagen :idPokemon="3" :mostrarPokemon="false" />
  <PokemonOpciones :pokemons="arreglo" />
</template>

<script>
import PokemonImagen from "../components/PokemonImagen.vue";
import PokemonOpciones from "../components/PokemonOpciones.vue";
import obtenerPokemonsFachada from "../clientes/clientePokemonAPI";
export default {
  components: {
    PokemonImagen,
    PokemonOpciones,
  },
  methods: {
     async cargaInicial() {
        const vectorInicial= await obtenerPokemonsFachada(4);
        this.arreglo=vectorInicial;
    },
  },
  data() {
    return {
      arreglo: [],
    };
  },
  //Los métodos de ciclo de vida son una excepción no necesitan un await
  mounted(){
      this.cargaInicial();


  }
};
</script>

<style>
</style>