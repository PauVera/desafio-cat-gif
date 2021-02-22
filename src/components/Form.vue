<template>
  <div class="container">
    <h1 class="text-center">Random Gif Cat</h1>
    <br />
    <div class="contenedorForm mx-0 p-5">
      <div class="row form-group">
        <label for="titulo" class="col-3">Título</label>
        <input
          class="form-control col-9"
          type="text"
          name="titulo"
          placeholder="Texto que aparecerá en el GIF"
          v-model="Gato.titulo"
        />
      </div>
      <div class="row form-group">
        <label for="filtro" class="col-3">Filtro</label>
        <select name="filtro" id="filtro" class="form-control col-9" v-model="Gato.filtro">
          <option value="sepia">Sepia</option>
          <option value="blur">Blur</option>
          <option value="mono">Monocromático</option>
          <option value="negative">Negativo</option>
          <option value="paint">Paint</option>
          <option value="pixel">Pixelado</option>
        </select>
      </div>
      <div class="row form-group">
        <label for="color" class="col-3">Color</label>
        <div>
          <select name="color" id="color" class="form-control col-6 d-inline-block py-1" v-model="Gato.color">
            <option value="red">Rojo</option>
            <option value="blue">Azul</option>
            <option value="green">Verde</option>
            <option value="yellow">Amarillo</option>
            <option value="white">Blanco</option>
            <option value="black">Negro</option>
          </select>
          <div
            class="rounded-circle muestraColor col-3 d-inline-block ml-3"
          ></div>
        </div>
      </div>
      <div class="row form-group">
        <label for="tamano" class="col-3">Tamaño</label>
        <input class="form-control col-9" type="number" name="tamano" placeholder="-" v-model="Gato.tamano"/>
      </div>
    </div>
    <div class="contenedorBtn text-center form-group">
      <button class="form-control btn btn-light" @click="obtenerInfo">Obtener mi gatito</button>
    </div>
    <div class="contenedorGif">
        <img v-if="mostrar" :src="imgSrc">
    </div>
  </div>
</template>

<script>
export default {
    data(){
        return{
            Gato: {
                titulo:"",
                filtro:"",
                color:"",
                tamano:"",
            },
            mostrar:"",
        };
    },
    methods:{
        obtenerInfo(){
            const patron = this.Gato;
            const url = `https://cataas.com/cat/gif/says/${patron.titulo}?filter=${patron.filtro}&color=${patron.color}&size=${patron.tamano}&type=or`;
            this.mostrar = true;
            this.imgSrc = url;
        }
    }
};
</script>

<style>
.contenedorForm {
  background-color: rgb(240, 128, 127) !important;
}

.contenedorBtn,
.row,
.contenedorGif {
  padding: 1rem;
}

.muestraColor {
  width: 30px;
  height: 30px;
  background-color: red;
}

button{
    width: 15rem!important;
}
</style>
