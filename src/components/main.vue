<script>
import axios from "axios";
export default {
    options: {
        method: 'GET',
        url: 'https://api.themoviedb.org/3?api_key=d7e474ca7946c8bafc272a2058d56cb0/movies',
        params: { include_adult: 'false', language: 'en-US', page: '1' },
        headers: {
            accept: 'application/json',
            Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJkN2U0NzRjYTc5NDZjOGJhZmMyNzJhMjA1OGQ1NmNiMCIsInN1YiI6IjY2NTczM2UxZTU3MjdjNDE2OTFhMWFhYSIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.btxNRj6OpZw8zU1TeDw-tgmXpNAdknVbaoCBcfMX4f4'
        }
    }
}
    .request(options)
    .then(function (response) {
        console.log(response.data);
    })
    .catch(function (error) {
        console.error(error);
    });
</script>

<template>
    <div class="navbar">
        <h1>Boolflix</h1>
        <button @click="request">cerca film</button>
    </div>
</template>

<style scoped>
.navbar {
    display: flex;
    justify-content: space-between;
}
</style>