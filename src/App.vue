<template>
  <div>
    <vagas-favoritas></vagas-favoritas>
    <topo-padrao @navegar="componente = $event"></topo-padrao>
    <Alerta v-if="exiberAlerta" :tipo="alerta.tipo">
      <template v-slot:titulo>
        <h5>{{alerta.titulo}}</h5>
      </template>
      <template v-slot:descricao>
        <h6>{{alerta.descricao}}</h6>
      </template>
    </Alerta>
    <conteudo v-if="visibilidade" :conteudo = "componente"></conteudo>
  </div>
</template>

<script>
import Conteudo from '@/components/layout/Conteudo.vue';
import TopoPadrao from '@/components/layout/TopoPadrao.vue';
import VagasFavoritas from '@/components/comuns/VagasFavoritas.vue';
import Alerta from './components/comuns/Alerta.vue';

export default {
  name: 'App',
  data: () => ({
    visibilidade: true,
    componente : 'Home',
    exiberAlerta: false,
    alerta: {titulo: '', descricao:'', tipo:''}
  }),
  acao(){
    console.log('chegamos ate aqui')
  },
  components: {
    Conteudo,
    TopoPadrao,
    VagasFavoritas,
    Alerta,
},
  mounted(){
    this.emitter.on('alerta', (a) =>{
      this.alerta = a
      this.exiberAlerta = true
      setTimeout(() =>this.exiberAlerta = false, 5000)

    })
  }
}
</script>

<style module>

</style>
