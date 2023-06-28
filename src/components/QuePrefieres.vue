<template>
  <div class="background">
    <div class="img1">
      <img
        v-if="urlImagen1"
        :src="urlImagen1"
        alt="No se puede cargar la imagen"
      />
      <h2 v-if="respuesta1">Respuesta: {{ respuesta1 }}</h2>
    </div>
    <div class="maybe-response">
      <h2 v-show="respuesta1 != respuesta2">Maybe?</h2>
    </div>
    <div class="img2">
      <img
        v-if="urlImagen2"
        :src="urlImagen2"
        alt="No se puede cargar la imagen"
      />
      <h2 v-if="respuesta2">Respuesta: {{ respuesta2 }}</h2>
    </div>
  </div>

  <div class="container">
    <button v-if="urlImagen1" v-on:click="consumirAPI('2')" class="opcion-1">
      Elegir
    </button>
    <h2>Que Gif prefieres?</h2>
    <button
      v-if="!urlImagen1 && !urlImagen2"
      v-on:click="iniciarJuego()"
      class="iniciar"
    >
      Iniciar Juego
    </button>
    <button v-if="urlImagen2" v-on:click="consumirAPI('1')" class="opcion-2">
      Elegir
    </button>
  </div>
</template>

<script>
export default {
  name: "QuePrefieres",
  data() {
    return {
      respuesta1: "",
      urlImagen1: null,
      respuesta2: "",
      urlImagen2: null,
    };
  },
  methods: {
    async consumirAPI(numeroImagen) {
      const respuesta = await fetch("https://yesno.wtf/api").then((r) =>
        r.json()
      );
      const { answer, image } = respuesta;
      if (numeroImagen == "1") {
        this.respuesta1 = answer;
        this.urlImagen1 = image;
      } else {
        this.respuesta2 = answer;
        this.urlImagen2 = image;
      }
    },

    async iniciarJuego() {
      this.consumirAPI("1");
      this.consumirAPI("2");
    },
  },
};
</script>

<style>
.img1,
.img2 {
  display: flex;
  align-items: center;
  justify-content: left;
}

.img1 img,
.img2 img {
  width: 100vh;
  height: 50vh;
}
.img1 {
  background-color: #81f7be;
}

.img2 {
  background-color: #f78197;
}

.background {
  position: fixed;
  height: 100vh;
  width: 100vw;
  left: 0px;
  top: 0px;
  max-height: 100%;
  max-width: 100%;
}

.container {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 83vh;
}

.container h2,
.container button {
  margin-left: 800px;
}

.container h2 {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-size: 30px;
  font-weight: bold;
  background-color: aliceblue;
  border: 3px ridge #3953e5;
  font-style: italic;
  color: black;
  padding: 0px 100px 0px 100px;
}

.container .opcion-1,
.container .opcion-2 {
  margin: 100px 0px 100px 800px;
  background-color: #81e9f7;
  width: 200px;
  height: 300px;
  border: 3px solid #870889;
  font-size: 25px;
  font-weight: bold;
  border-radius: 20px;
}

.container .opcion-1:hover,
.container .opcion-2:hover {
  background-color: #870889;
  border: 3px solid #81e9f7;
  color: #fff;
}

.iniciar {
  margin: 0 5px;
  background-color: #3953e5;
  color: white;
  width: 200px;
  height: 50px;
  font-size: 25px;
  font-weight: bold;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.iniciar:hover {
  background-color: white;
  color: #3953e5;
}

.maybe-response {
  position: fixed;
  background: transparent;
  left: 49%;
  top: 40%;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size: 30px;
  color: #477aef;
  font-style: oblique;
  text-shadow:
    -1px -1px 0 white, 
    1px -1px 0 white, 
    -1px 1px 0 white, 
    1px 1px 0 white;
}
</style>