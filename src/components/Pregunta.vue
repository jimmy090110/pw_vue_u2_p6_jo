<template>
  <img v-if="img"
    :src="img"
    alt="No se pudo"
  />

  <div class="oscuro">
    <div class="pregunta-container">
      <input v-model="pregunta" type="text" placeholder="Hazme una pregunta" />
      <p>Recuerda terminar la pregunta con el signo de interrogración(?)</p>

      <div class="respuesta">
        <h2>{{ pregunta }}</h2>
        <h1>{{ respuesta }}</h1>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pregunta: null,
      respuesta: null,
      img:null
    };
  },
  watch: {
    pregunta(value, oldValue) {
      console.log({ value, oldValue });
      if (!value.includes("?")) {
        return; //salgo del observador
      }
      //consumir el API para obtener la respuesta
      this.obtenerRespuesta();
    },
  },
  methods: {
    async obtenerRespuesta() {
      const data = await fetch("https://yesno.wtf/api").then((r) => r.json());
      console.log(data);
      const {answer, forced,image}=data;
      console.log(answer)
      this.respuesta= answer;
      this.img= image;
      return data;
    },
  },
  async prueba(){
    const data2= await this.obtenerRespuesta();
  }
};
</script>

<style>
img,
.oscuro {
  max-height: 100%;
  height: 100vh;
  max-width: 100%;
  width: 100vw;
  position: fixed;
  top: 0px;
  left: 0px;
}

.oscuro {
  background: rgba(0, 0, 0, 0.8);
  /* 0.0 full transparente, 1.0 full opaco*/
}
.pregunta-container {
  position: relative;
}

input {
  margin-top: 70px;
  width: 250px;
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  text-align: center;
}
input:focus {
  outline: none;
}

p,
h1,
h2 {
  color: white;
}

p {
  font-size: 25px;
  margin-top: 0px;
}
.respuesta {
  margin-top: 120px;
}
</style>