<template>
    <div>
      <loader :isLoading="load"></loader>
        <div class="container">
          <h1>Cadastro Cliente</h1>
            <form method="" action="#">
                <label for="name">Nome</label><br>
                <input type="text" placeholder="Seu nome" v-model="movie.name"><br>

                <label for="description">Descrição</label><br>
                <input type="text" placeholder="Descrição" v-model="movie.description"><br>
                <a href="lista" @click="Save()" ><button>Cadastrar</button></a>
            </form>
        </div>
    </div>
</template>
  
  <script>
   import axios from '@/static/axios.js'
  export default {
    head:{
      title:'Cadastro de Clientes',
    },
  
  
    data(){
      return{
        movie:{
             name:'',
             description:''
        },
          load:false,
        
       
      };
    },
  
    methods:{
        async Save(){
          this.load=true
          try{
            let response = await axios.post('movies',this.movie)
         
          }catch(e){
            console.log(e);
          }finally{
            this.load=false
          }
      
        },

        async GET_DATA(path){
          let response = await axios.get(path)
          return response.data
        },
    },
  }
  </script>
  