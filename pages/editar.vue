<template>
    <div>
      <loader :isLoading="load"></loader>
        <div class="container">
            <h1>Editar Cliente</h1>            <form method="" action="#">
                <label for="name">Nome</label><br>
                <input type="text" placeholder="Seu nome" v-model="movie.name"><br>
    
                <label for="description">Descrição</label><br>
                <input type="text" placeholder="Descrição" v-model="movie.description"><br>
                <a href="" @click="Put(m.id)"><button>Editar</button></a>
            </form>
        </div>
        {{ movie }}
    </div>
</template>
  
  <script>
   import axios from '@/static/axios.js'
  export default {
    head:{
      title:'Editar Clientes',
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
        async Put(id){
          this.load=true

          const data = {
            name: movies.name,
            description: movies.description
          }
          try{
            let response = await axios.put(`movies/${id}`,data)
         
          }catch(e){
            console.log(e);
          }finally{
            this.load=false
          }
      
        },
       
    },
   
  }
  </script>
  