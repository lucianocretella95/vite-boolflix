<script>
import axios from 'axios';
export default {
    data() {
        return {
            search: "",
            myfilms: [],
        }
    },
    methods: {
        
        movies() {
            const options = {
                method: 'GET',
                url: 'https://api.themoviedb.org/3/search/movie',
                params: { include_adult: 'false', language: 'en-US', page: '1', query: this.search },
                // inserire searchbar al posto di dragon ball in modo tale da cercare solo i film cercati dall'utente usando il v-model
                headers: {
                    accept: 'application/json',
                    Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJkN2U0NzRjYTc5NDZjOGJhZmMyNzJhMjA1OGQ1NmNiMCIsInN1YiI6IjY2NTczM2UxZTU3MjdjNDE2OTFhMWFhYSIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.btxNRj6OpZw8zU1TeDw-tgmXpNAdknVbaoCBcfMX4f4'
                }
            };
            axios
                .request(options)
                .then((response) => {
                    // console.log(response.data.results);
                    this.myfilms = response.data.results;
                })
                .catch(function (error) {
                    console.error(error);
                });
        }

    }
}
</script>

<template>
    <div class="navbar">
        <h1>Boolflix</h1>
        <div class="find">
            <input style="margin-right: 0.5rem;" v-model="search">
            <button @click="movies">cerca film</button>
        </div>
    </div>
    <div v-for="film in myfilms">
        <img v-bind:src="film.poster_path">
        <h5>Titolo: {{ film.title }}</h5>
        <p>voto: {{ film.vote_average }}</p>
        <p>Data uscita:{{ film.release_date }}</p>
    </div>
    <!-- scrivere ciclo v-for per togliere le quadre dell'array vuoto in browser -->
</template>

<style scoped>
.navbar,
.find {
    display: flex;
    justify-content: space-between;
}

.navbar h1 {
    color: red;
}

img {
    width: 15rem;
}
</style>