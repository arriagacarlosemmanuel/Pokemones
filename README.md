<html><head>
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">

</head>  

<body>
<div id="app1" class="container">  
    <h1>{{titulo}}</h1>
    
    <div class="row">
        <div class="col">
    <ul>    
        <li v-for="poke in pokemones">
  <a v-for:click="poke.url">{{poke.name}}</a>
  </li>
    </ul>     
    <button v-on:click="pokes(siguiente)" class="btn btn-primary">siguiente</button>
    Total de pokemones: {{totalpokes}}
    <button v-on:click="pokes(anterior)" class="btn btn-warning">Anteriores</button>
     
</div>
        <div class="col">
            <h3>Imagen del Pokemon</h3>
            <img src="">
        </div>
<script>
</script>    

</div></div></body></html>
var app=new Vue({
  el:"#app1",
  data:{  
      titulo: "API de Pokemones",
      urlAPI: "https://pokeapi.co/api/v2/pokemon",
      pokemones : [],      
      totalpokes: 0,
      siguiente:"",
      anterior:"",
      poke:[],
      nombrePoke:"",
  },  
        mounted(){
    this.pokes(this.urlAPI);
  },
  methods:
    {
    pokes: async function(url) {
        const response = await fetch(url);
        this.pokemones = await response.json();
        this.totalPokes = this.pokemones.count; 
        this.siguiente = this.pokemones.next;
        this.anterior = this.pokemones.previous;
        this.pokemones = this.pokemones.results;
    },
verPokes: async function(url,nombre){
    const response= await fech(url);
    this.poke= await response.json();
    this.poke=this.po.sprites.other
    this.nombrePoke=nombre;
    this.urlImagen=this.poke.dream_world.front_default;
    }
  },        
}) //fin de objeto Vue
