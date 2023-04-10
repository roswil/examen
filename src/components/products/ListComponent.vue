<template>
    <h1>Listado de Pelicula
    </h1>

    <div  v-for="p in peliculas" :key="p.id">
    {{p.Title}}
    </div>

    <button 
        class="btn btn-primary" 
        data-bs-target="#collapseTarget" 
        data-bs-toggle="collapse">
        Adicionar
    </button>
    
</template>
<script>
import axios from 'axios'
import "bootstrap";
import "bootstrap/dist/css/bootstrap.min.css";
export default{
    
data(){
    return{
         peliculas:[]
    };
},
mounted(){
    axios.get ('http://www.omdbapi.com/?apikey=ba9b1dc&s=gal')
    .then((response) => {
        console.log(response.data.Search);
        this.peliculas=response.data.Search
      })
}
}
</script>
