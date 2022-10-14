<template>
    <h1>{{countryInfo.name.common}}</h1>
    <p>Capital {{countryInfo.capital}}</p>
    <p>Area {{countryInfo.area}}</p>
    <p>Borders {{countryInfo.borders}}</p>

    <img src="" alt="">
</template>
<script setup>
import { ref, watch } from 'vue';
import { useRoute } from 'vue-router';
import countries from '../assets/countries.json'

const route = useRoute();
const codeCountry = ref('');
const countryInfo = ref(Object);
const findCountry = (countryCode) => {
    const getCountry = countries.filter(country => country.alpha3Code == countryCode);
    console.log(getCountry[0]);
    return getCountry[0];
}
//es una funcio que se li ha d'indicar quina variable ha de mirar i quan aixo passa s'executa
watch(() => route.params.code, newValue => {
    codeCountry.value = route.params.code;
    //  console.log(codeCountry.value);
    //  console.log(newValue);
    countryInfo.value = findCountry(route.params.code);
})

</script>
<style scoped>

</style>