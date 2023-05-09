<template>
    <div>
        <h2>CardContent</h2>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: "CardContent",
    data() {
        return {
            arrayMovies: [],
        }
    },
    mounted() {
        this.apiMovie()
    },
    methods: {
        apiMovie() {
            axios.get('https://api.themoviedb.org/3/movie/550?api_key=d7be0139fcfa8913f436bb5f5e9eb2fc')
                .then((res) => {
                    console.log(res.data)
                    this.arrayMovies = res.data
                })
        },
    }
}
</script>

<style scoped></style>