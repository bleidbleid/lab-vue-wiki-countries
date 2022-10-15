<template>
    <!-- 
        <div class="section">
        <figure class="image is-128x128">
            <img :src="`https://flagpedia.net/data/flags/icon/72x54/${countryInfo.alpha2Code.toLowerCase()}.png`">
        </figure>
        <div class="title">{{countryInfo.name.common}}</div>
        <table class="table is-fullwidth">
            <tbody>
                <tr>
                    <td>Capital</td>
                    <td>{{countryInfo.capital}}</td>
                </tr>
                <tr>
                    <td>Area</td>
                    <td>{{countryInfo.area}} km <sup>2</sup></td>
                </tr>
                <tr>
                    <td>Borders</td>
                    <td>
                        <ul>
                            <li>{{countryInfo.borders}}</li>
                            <li><a href="/BEL">Belgium</a></li>
                            <li><a href="/DEU">Germany</a></li>
                            <li><a href="/ITA">Italy</a></li>
                            <li><a href="/MCO">Monaco</a></li>
                            <li><a href="/ESP">Spain</a></li>
                            <li><a href="/CHE">Switzerland</a></li>
                        </ul>
                    </td>
                </tr>

            </tbody>
        </table>
    </div>
     -->
    <section class="section" v-if="!isLoading">

        <figure class="image is-128x128">
            <img :src="`https://flagpedia.net/data/flags/icon/72x54/${country.alpha2Code.toLowerCase()}.png`">
        </figure>
        <div class="title">{{country.name.common}}</div>
        <table class="table is-fullwidth">
            <tbody>
                <tr>
                    <td>Capital</td>
                    <td>{{country.capital[0]}}</td>
                </tr>
                <tr>
                    <td>Area</td>
                    <td>{{country.area}} km <sup>2</sup></td>
                </tr>
                <tr>
                    <td>Borders</td>
                    <td>
                        <ul>
                            <li v-for="border in country.borders">
                                <router-link :to="{name: 'details', params: {code: border}}">
                                    {{findCountry(border).name.common}}</router-link>
                            </li>
                        </ul>
                    </td>
                </tr>

            </tbody>
        </table>
    </section>
</template>
<script setup>
// import { ref, watch } from 'vue';
// import { useRoute } from 'vue-router';
// import countries from '../assets/countries.json'

// const route = useRoute();
// const codeCountry = ref('');
// const countryInfo = ref(Object);
// const findCountry = (countryCode) => {
//     const getCountry = countries.filter(country => country.alpha3Code == countryCode);
//     console.log(getCountry[0]);
//     return getCountry[0];
// }
// //es una funcio que se li ha d'indicar quina variable ha de mirar i quan aixo passa s'executa
// watch(() => route.params.code, newValue => {
//     codeCountry.value = route.params.code;
//     //  console.log(codeCountry.value);
//     //  console.log(newValue);
//     countryInfo.value = findCountry(route.params.code);
// })

import { ref, onMounted, watch } from 'vue'
import { useRoute } from 'vue-router'
import countries from '../assets/countries.json'

const route = useRoute();
const country = ref();
const isLoading = ref(true)

// onMounted es una funcion que se llama en el momento que el componente esta listo para renderizarse
onMounted(() => {
    country.value = findCountry(route.params.code);
    console.log(country.value)
    isLoading.value = false;
})

watch(() => route.params.code, newValue => {
    country.value = findCountry(route.params.code);
   
})

const findCountry = (code) => {
    // Nos busca el pais en la array
    return countries.find((country) => {
        return country.alpha3Code === code
    })

}



</script>
<style scoped>

</style>