<template>
  <div class="formulario">
    <div class="formulario-title">Defina a palavra</div>
    <input type="text" class="formulario-input">
    <button>Próximo</button>
  </div>

</template>

<script>
export default {
    // eslint-disable-next-line 
    name: 'Formulario'

}
</script>

<style>
    .formulario{
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
        justify-content: center;
        margin-top: 20px;
    }

    .formulario-input{
        padding: 10px 5px;
        border:0;
        border-radius: 5px;
        margin:10px 0px;
    }
</style>