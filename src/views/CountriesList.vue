<template>
    <div v-for="country in countries" class="section">
        <ul>
            <router-link :to="{name: 'details', params : {alpha3Code:country.alpha3Code}}">
                <li>
                    <img :src="`https://flagpedia.net/data/flags/icon/72x54/${country.alpha2Code.toLowerCase()}.png`">
                </li>
                <li>{{country.name.common}}</li>
            </router-link>
        </ul>
    </div>
</template>
<script setup>
import countries from '../assets/countries.json'
import { ref } from 'vue'
</script>
<style>

</style>