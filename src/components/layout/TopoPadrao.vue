<template>
<nav class="navbar navbar-expand-sm bg-dark navbar-dark">
  <div class="container-fluid">
    <ul class="navbar-nav">
      <li class="nav-item">
          <a class="nav-link" aria-current="page" href="#" @click="navegarPara('Home')">Vagas</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#"  @click="navegarPara('Publicar')">Publicar vaga</a>
        </li>
    </ul>
  </div>
</nav>

</template>

  <script>
    export default{
      name: 'TopoPadrao',
      methods: {
        navegarPara(p){
          this.$emit('navegar', p)
        }
      }
    }
  </script>
  <!--Estilo-->
  <style>

  </style>