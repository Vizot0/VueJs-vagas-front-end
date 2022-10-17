<template>
    <div class='h-100 p-5 bg-light border rounded-3 bg-dark text-white'>
        <p>{{titulo}}</p>
        <h2>{{indicador}}</h2>
    </div>
</template>
<script>
export default{
    name: 'Indicador',
    props:['titulo', 'indicador'],
    computed:{

    }
}
</script>