<template>
    <h1>Algodón</h1>
    <img src="" alt="">
</template>
<script setup>
import { ref, watch } from 'vue';
import { useRoute } from 'vue-router';
const route = useRoute();
const codeContry = ref('');
//es una funcio que se li ha d'indicar quina variable ha de mirar i quan aixo passa s'executa
watch(() => route.params.code, newValue => {
     codeContry.value = route.params.code;
}) 
// const countryFilter = ;
</script>
<style scoped>
</style>