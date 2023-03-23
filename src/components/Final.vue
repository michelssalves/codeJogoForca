<template>
  <div class="final">
    <div :class="`final-texto ${etapa}`">
        {{texto}}
    </div>
    <button @click="jogarNovamente" class="final-botao">Play Again</button>
  </div>
</template>
<script>
export default {
    // eslint-disable-next-line 
    name: 'Final',
    props:{
      etapa: String, 
      texto: String, 
      jogarNovamente:Function
    },
    data(){
        return{
            

        }

    },
    methods: {

    }

}
</script>

<style>
    .final-botao{
        margin:20px 0px;
        font-size: 24px;
        font-weight: bold;
    }   
    .final-texto.enforcado{
        margin-top: 20px;
        color: var(--color-text-error);

    }
    .final-texto.ganhador{
        margin-top: 20px;
        color: var(--color-text-success);
    }
</style>