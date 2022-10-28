<template>
      <section>
        <loader :isLoading="load"></loader>
        <div class="container">
          <h1>Lista de Cliente Adx</h1>
          <table class="table">
              <thead>
                <tr>
                  <th scope="col">ID</th>
                  <th scope="col">Nome</th>
                  <th scope="col">Descrição</th>
                  <th scope="col">Ação</th>
                </tr>
              </thead>
              <tbody >
                <tr v-for="(m, i) in movies"
                :key="m.movies">
                  <td>{{ i+1 }}</td>
                  <td>{{ m.name }}</td>
                  <td>{{ m.description }}</td>
                  <td>
                    <a href="#" @click.stop.prevent="Delete(m.id)"><svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-trash" viewBox="0 0 16 16">
                    <path d="M5.5 5.5A.5.5 0 0 1 6 6v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm2.5 0a.5.5 0 0 1 .5.5v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm3 .5a.5.5 0 0 0-1 0v6a.5.5 0 0 0 1 0V6z"/>
                    <path fill-rule="evenodd" d="M14.5 3a1 1 0 0 1-1 1H13v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V4h-.5a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1H6a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1h3.5a1 1 0 0 1 1 1v1zM4.118 4 4 4.059V13a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1V4.059L11.882 4H4.118zM2.5 3V2h11v1h-11z"/>
                    </svg></a>
                  
                  <a href="editar"><svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-back" viewBox="0 0 16 16">
                    <path d="M0 2a2 2 0 0 1 2-2h8a2 2 0 0 1 2 2v2h2a2 2 0 0 1 2 2v8a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2v-2H2a2 2 0 0 1-2-2V2zm2-1a1 1 0 0 0-1 1v8a1 1 0 0 0 1 1h8a1 1 0 0 0 1-1V2a1 1 0 0 0-1-1H2z"/>
                    </svg></a>
                  </td>
                </tr>
              </tbody>
            </table>
        </div>
      </section>
</template>

    <script>
  import axios from '@/static/axios.js'
  import Loader from '../components/Loader.vue';

    export default {
  components: { Loader },
      name: 'IndexPage',
    

  head:{
      title:'Lista de Clientes',
    },

      data(){
          return{
            movies:[],
            load: true
          };
      },
    
      methods:{
        async GET_DATA(path){
          let response = await axios.get(path)
          return response.data
        },

        async Delete(id){
          let response = await axios.delete(`/movies/${id}`).then(()=>{
            const idx = this.movies.findIndex(o => o.id == id);
            this.movies.splice (idx, 1);
          })
      
        }
      
      },  
    
      mounted() {
        this.$nextTick(async() =>{
          let self = this
          try{
              await Promise.all([this.GET_DATA('movies')]).then((val) =>{
            self.movies= val[0]
          });

          }catch(e){
            consolelog(e);
          }finally{
            this.load=false
          }
      
        });
      },
    }
    </script>
    
