<template>
  <h2>{{presentar}}</h2>
  <!--<p>{{ numero }} <sup>2</sup>={{ calcularCuadrado() }}</p>  LLAMADA A UN METODO-->
  <p>{{ numero }} <sup>2</sup>={{ calcular }}</p>
  <!--LLAMADA A UNA PROPIEDAD COMPUTADA-->

  <div>
    <button v-on:click="incrementar">+1</button>
    <button v-on:click="disminuir">-1</button>
  </div>
</template>

<script>
export default {

 // props:["titulo","num"], Froma básica de declarar un props(Básica)
  props:{
    titulo: String,
    num: {
      type:Number,
     // required:true // esto cuando siempre va a ser requerido
     required: false,
     validator(value){
      //Toda la programación
      //return booleano
      return value>0;
     }
     

    }
    
  },
  data() {
    return {
      /*prop reactivas*/
      numero: this.num,

    };
  },
  methods: {
    calcularCuadrado() {
      console.log("Ingreso al metodo");
      return (
        this.numero * this.numero
      ); 
    },
    calcularCuadrado2(num1, num2) {
      console.log("Ingreso al metodo");
      return num1 * num2;
    },

    incrementar() {
      this.numero++;
      
    },

    disminuir() {
      this.numero--;
    },
  },

  computed: {
    calcular() {
      console.log("Ingreso a la propiedad computada");
      return this.numero * this.numero;
    },

    presentar(){
      if(this.titulo!==undefined){
        return this.titulo;
      }else{
       return  "Texto que quiero";
      }
    }
  },
};
</script>

<style>
* {
  background: #b6dbc2;
}
button {
  background: rgb(155, 208, 9);
  border-radius: 5px;
  border: 1px solid white;
  color: rgb(255, 255, 255);
  margin: 5px 5px;
  padding: 5px 20px;
  cursor: pointer;
}
button:hover {
  background: #5aa67b;
}
</style>