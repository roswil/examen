<template>
    <h1>Listado de Pelicula
    </h1>
    <form class="form" >
    <input class="input" v-model="title" type="text" name="title" placeholder="Titulo a buscar" />
   
    <button class="btn btn-primary" @click="buscar">Buscar</button>
  </form>
  
    <div  v-for="p in peliculas" :key="p.id">
    {{p.Title}}
    </div>

   
        
</template>
<script>
import axios from 'axios'
import "bootstrap";
import "bootstrap/dist/css/bootstrap.min.css";
export default{
    
data(){
    return{
         peliculas:[],
         title: ""
    };
},
mounted(){
    axios.get ('http://www.omdbapi.com/?apikey=ba9b1dc&s=gal')
    .then((response) => {
        console.log(response.data.Search);
        this.peliculas=response.data.Search
      })
},
methods: {
    async buscar() {
        console.log(this.title);
    axios.get ('http://www.omdbapi.com/?apikey=ba9b1dc&s='+this.title)
    .then((response) => {
        console.log(response.data.Search);
        this.peliculas=response.data.Search
      })
        
    
    }
  }
}
</script>
