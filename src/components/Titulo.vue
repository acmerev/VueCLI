<template>
    <div class="titulo">
        <h1>{{texto}}</h1>
    </div>
</template>

<script>
export default {
    name: 'Titulo',
    props: {
        texto : String
    }
}
</script>

<style scoped>
h1 {
    color: coral;
}
</style>