<template>
<div class="container py-4">
        <div class="row">
          <div class="col">
            <PesquisarVaga></PesquisarVaga>
          </div>
        </div>

        <ListaVagas></ListaVagas>
    
        <div class="row mt-5">
          <div class="col-4">
            <Indicador titulo="Vagas abertas" indicador="1" ></Indicador>
          </div>

          <div class="col-4">
            <Indicador titulo="Profissionais cadastrado" indicador="250" ></Indicador>
          </div>

          <div class="col-4">
            <Indicador titulo="Visitantes online" :indicador="usuariosOnline" ></Indicador>
          </div>

        </div>
</div>

</template>
  <script>
import PesquisarVaga from '@/components/comuns/PesquisarVaga.vue';
import Indicador from '@/components/comuns/Indicador.vue';
import ListaVagas from '@/components/comuns/ListaVagas.vue';


export default{
  name: 'Home',
  components:{
    PesquisarVaga,
    Indicador,
    ListaVagas
},

data: () => ({
  usuariosOnline: 0,
}),
methods:{
  getUsuariosOnline(){
    this.usuariosOnline = Math.floor(Math.random() * 101)
  }
},
  created(){
    setInterval(this.getUsuariosOnline, 1000)
  },
}
  </script>
  <!--Estilo-->
  <style module>

  </style>
  