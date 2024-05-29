<script>
import axios from "axios";
export default {
    options: {
        params: { include_adult: 'false', language: 'en-US', page: '1' },
    },
    methods: {
        options() {
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=d7e474ca7946c8bafc272a2058d56cb0&query= INPUT UTENTE')
                .then(function (result) {
                    console.log(result.data);
                });
        }
    }
};
</script>

<template>
    <div class="navbar">
        <h1>Boolflix</h1>
        <button @click="options">cerca film</button>
    </div>
</template>

<style scoped>
.navbar {
    display: flex;
    justify-content: space-between;
}
</style>