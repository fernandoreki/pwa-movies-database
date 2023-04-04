<template>
    <div class="container">
        <h1 class="mt-3 mb-3 text-light">Old movies database</h1>
        <MovieCard />
    </div>
</template>

<script>
import MovieCard from './MovieCard.vue';

export default {
    name: "Movies",
    props: {
        //define variables
    },
    data() {
        return {
            //initialize variables
        };
    },
    methods: {},
    components: { MovieCard }
}
</script>

<style scoped></style>