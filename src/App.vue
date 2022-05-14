<template>
<div class="contenedor">
  <div class="tittle">
    <h1>Random Gif Cat</h1>
  </div>
  <div class="form">
    <form action="" @submit.prevent="getTodos()">
      <div class="titulo">
        <label for="">Titulo</label>
        <input type="text" v-model="titulo" placeholder="Ingresa un mensaje">
      </div>
      <div class="filtro">
         <label for="">Filtro</label>
        <select name="filtro" v-model="filtro">
        <option value="blur">Borroso</option>
        <option value="mono">Monocromatico</option>
        <option value="sepia">Sepia</option>
        <option value="negative">Negativo</option>
        <option value="paint">Pintar</option>
        <option value="pixel">Pixelar</option>
      </select>
      <p>{{filtro}}</p>
      </div>
      <div class="color">
        <label for="">Color</label>
        <select name="color" v-model="color">
          <option value="green">Green</option>
          <option value="red">Red</option>
          <option value="blue">Blue</option>
          <option value="yellow">yellow</option>
        </select>
         <p class="circulo" :style="{backgroundColor : color}"> </p>
      </div>
      <div class="tamaño">
       <label for="">Tamaño</label>
        <select name="tamaño" v-model="tamaño">
          <option value="grande">400</option>
          <option value="mediano">300</option>
          <option value="pequeño">200</option>
          <p> {{tamaño}}</p>
        </select>
        <p>{{tamaño}}</p>
      </div>  
    </form>
  </div>
  <div class="button">
    <button @click="getTodos" type="submit">Buscar Gatito</button>
  </div>
  <div class="result">
   <img class="img-gatito" :src="url" alt="">
  </div>
</div>
</template>

<script>
import axios from 'axios';


export default {
  name: 'App',
  data : () =>({
    url: "",
    titulo: "",
    filtro: "",
    color: "",
    tamaño: "",
    
  }),
  mounted(){
    this.getTodos();
    
  },
  methods: {
    getTodos(){
      this.url = `https://cataas.com/cat/gif/says/${this.titulo}?filter=${this.filtro}&color=${this.color}&size=${this.tamaño}`
  }
  
  },
} 
</script>

<style>
body{
background-color: aquamarine;
width: 100%;
font-family: 'Macondo', cursive;
}
.contenedor{
  text-align: center;
}
.form{
  background-color: rgb(230, 230, 123);
  display: flex;
  align-content: center;
  justify-content: center;
}
.titulo{
  margin-bottom: 10px;
  margin-top: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.filtro{
  margin-bottom: 10px;
  margin-top: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.color{
  margin-bottom: 10px;
  margin-top: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.tamaño{
  margin-bottom: 10px;
  margin-top: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.circulo{
  border-radius: 50%;
  height: 25px;
  width: 25px;
}
.button{
  margin-bottom: 10px;
  margin-top: 10px;
  height: 40px;
}
label{
  font-size: 18px;
}
input[type=text]{
  width: 100%;
  display: inline-block;
  margin: 8px;
  padding: 8px;
}
select{
  width: 100%;
  display: inline-block;
  margin: 8px;
  padding: 8px;
}
button{
      color: #fff;
    background-color: #343a40;
    border-color: #343a40;
    display: inline-block;
    font-weight: 400;
    text-align: center;
    vertical-align: middle;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    border: 1px solid transparent;
    padding: 0.375rem 0.75rem;
    font-size: 1rem;
    line-height: 1.5;
    border-radius: 0.25rem;
    transition: color .15s ease-in-out,background-color .15s ease-in-out,border-color .15s ease-in-out,box-shadow .15s ease-in-out;
}


</style>
