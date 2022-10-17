<template>
    <div class="flex-comp">
        <div id="global">

            <div v-for="country in countries" class="section">
                <ul>
                    <router-link :to="{name: 'details', params : {code:country.alpha3Code}}">
                        <li>
                            <img
                                :src="`https://flagpedia.net/data/flags/icon/72x54/${country.alpha2Code.toLowerCase()}.png`">
                        </li>
                        <li>{{country.name.common}}</li>
                    </router-link>
                    <!-- //si veus que te un fill, mostra'l -->
                </ul>
            </div>
        </div>

        <div>
            <router-view></router-view>
        </div>

    </div>

</template>
<script setup>
import countries from '../assets/countries.json'
</script>
<style>
.section {
    width: 600px;
}

.flex-comp {
    display: flex;
}

#global {
    height: 100vh;
    overflow-x: hidden;
    overflow-y: scroll;
}
</style>