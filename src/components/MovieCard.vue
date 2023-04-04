<template>
    <div v-if="isMounted" class="row row justify-content-center bg-dark p-5 rounded">
        <div class="card m-2" v-for="(movie, idx) in movies" :key="idx" style="width: 20rem;">
        <ul class="p-2">
            <ol class="col" >
                <br>
                <img v-if="movie.primaryImage" :src="movie?.primaryImage.url" alt="image" class="card-img-top img-fluid">
                <img v-else src="../assets/notfound.jpg" alt="image" class="card-img-top img-fluid">
                <div class="card-body text-dark">
                    <h3 class="card-title">{{ movie?.titleText.text}}</h3> <br>
                    <p>
                        Title type: {{ movie?.titleType.text}} <br>
                        Year: {{ movie?.releaseYear.year}}
                    </p>
                </div>
            </ol>
        </ul>
    </div>
    </div>
    
</template>

<script>
import axios from "axios";
export default {
    name: 'MovieCard',
    props: {
        //define variables
    },
    async mounted() {
        await this.getMovies();
        this.isMounted = true;
    },
    data() {
        return {
            //initialize variables
            movies: null,
            isMounted: false
        }
    },
    methods: {
        async getMovies() {

            const options = {
                method: 'GET',
                url: 'https://moviesdatabase.p.rapidapi.com/titles',
                headers: {
                    'X-RapidAPI-Key': '054519b369mshc592475765dd6abp195e71jsn26afe0d6c042',
                    'X-RapidAPI-Host': 'moviesdatabase.p.rapidapi.com'
                }
            };
            await axios.request(options)
                .then(response => {
                    this.movies = response.data.results;
                })
                .catch(error => console.log(error));
        }
    }
}
</script>

<style scoped>
img {
    width: 200px;
}


</style>