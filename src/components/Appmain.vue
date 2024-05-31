<script>
import axios from 'axios';
export default {
    data() {
        return {
            search: "",
            myfilms: [],
            image: 'https://image.tmdb.org/t/p/w342'
        }
    },
    methods: {
        movies() {
            const options = {
                method: 'GET',
                url: 'https://api.themoviedb.org/3/search/movie',
                params: { include_adult: 'false', language: 'en-US', page: '1', query: this.search },
                // inserire searchbar in modo tale da cercare solo i film cercati dall'utente usando il v-model
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
    <div class="cards">
        <div v-for="film in myfilms">
            <img style="width: 7rem;" :src="image + film.poster_path">
            <h5>Titolo: {{ film.title }}</h5>
            <p style="font-size: 0.7rem;">voto: {{ (film.vote_average / 2) }}</p>
            <p style="font-size: 0.7rem;">Data uscita:{{ film.release_date }}</p>
        </div>
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

.cards {
    display: flex;
    justify-content: start;
    flex-wrap: wrap;
}
</style>