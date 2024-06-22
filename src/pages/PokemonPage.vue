<template>
  <h1 v-if="!pokemonCorrecto">Por favor espere.......</h1>
  <div v-else>
    <h1>Selecciona el Pokemon correcto</h1>
    <PokemonImagen :idPokemon="pokemonCorrecto.id" :mostrarPokemon="mostrar" />
    <PokemonOpciones :pokemons="arreglo" @seleccionPokemon="revisarRespuesta($event)" />
    <div v-show="mostrarmensajeI"></div>
    <div v-show="mostrarmensajeC"></div>
    <p></p>
  </div>
  <!-- <div>{{ cargaInicial() }}</div> -->
</template>

<script>
import PokemonImagen from "../components/PokemonImagen.vue";
import PokemonOpciones from "../components/PokemonOpciones.vue";
import obtenerPokemonsFachada from "../clientes/clientePokemonAPI"; /* Solo para funciones */

export default {
  components: {
    PokemonImagen,
    PokemonOpciones,
  },
  methods: {
    async cargaInicial() {
      const vectorInicial = await obtenerPokemonsFachada(5);
      this.arreglo = vectorInicial;
      const indice = Math.floor(Math.random() * 7);
      this.pokemonCorrecto = this.arreglo[indice];
    },
    revisarRespuesta(){
      console.log('Se emitio un evento desde el hijo')
      this.mostrar=true;
      if(data.ident == this.pokemonCorrecto.id){
        this.mostrar = true;
        console.log("Respuesta correcta");
        mostrarmensajeC:true;
    }else{
      this.mostrar = false;
      console.log("Respuesta incorrecta");
      mostrarmensajeI:true;

    }
  },
},
  data() {
    return {
      arreglo: [],
      pokemonCorrecto: "" /* Esto se puede hacer pero no se recomienda */,
      /* llamar: this.cargaInicial(), */
      mostrar: false,
      mostrarmensajeC:'Felicidades has ganado el juego',
      mostrarmensajeI:'Pokemon incorrecto,Siga intentando',
    };
  },
  mounted() {
    this.cargaInicial();
  }, /* se dispara cuando se incia pa pagina web */
}

</script>

<style scope></style>