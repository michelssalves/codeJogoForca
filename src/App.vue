<template>
  <div id="app">
    <h1>Jogo da Forca</h1>
    <section v-if="tela === 'inicio'" id="inicio">
      <Formulario/>
    </section>
    <section v-if="tela === 'jogo'" id="jogo">
      Jogo
    </section>
  </div>
</template>
<script>
import '@/assets/css/global.css';
import Formulario from '@/components/Formulario';
  export default{
    name: 'App',
    components:{
      Formulario
    },
    data(){
      return{
        tela: 'inicio',

      }
    }


  }
</script>
<style>
#app{
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
