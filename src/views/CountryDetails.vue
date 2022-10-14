<template>
    <h1 class="title">{{countryInfo.name.common}}</h1>
  <img :src="`https://flagpedia.net/data/flags/icon/72x54/${countryInfo.alpha2Code.toLowerCase()}.png`">
  <p class="title is-4">Capital {{countryInfo.capital}}</p>
  <p class="title is-4">Area {{countryInfo.area}}</p>
  <p class="title is-4">Borders {{countryInfo.borders}}</p>
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