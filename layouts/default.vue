<template>
    <div>
      <nav>
        <div class="container">
          <ul>
          <NuxtLink to="/lista"><li>Lista</li></NuxtLink>
            <NuxtLink to="/cadastro"><li>Cadastro</li></NuxtLink>
          </ul>
        </div>
      </nav>
      <Nuxt/>
    </div>
</template>
  
  <script>
  export default {
    name: '',
  
    data(){
      return{
  
      };
    },
  
    methods:{
  
    },
  }
  </script>
  