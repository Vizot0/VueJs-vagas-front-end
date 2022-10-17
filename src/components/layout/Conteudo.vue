<template>
    <div>
    <keep-alive>
      <component :is="conteudo"/>
    </keep-alive>
  </div>
  </template>
  
  <script>
    import Home from '@/components/views/Home.vue';
    import Publicar from '@/components/views/Publicar.vue'

export default{
   name: 'Conteudo',
   props: {
    conteudo:{
      type: String,
      required: true
    }
   },
    components:{
      Home,
      Publicar,

  }, 
  

}
  </script>
  <!--Estilo-->
  <style module>

  .teste-1{
    background-color: red;
  }
  #teste-2{
    background-color: brown;
  }

  </style>
  