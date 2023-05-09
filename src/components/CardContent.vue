<template>
    <div>
        <h2>CardContent</h2>
    </div>
</template>

<script>
import axios from 'axios';
import { store } from "../store";

export default {
    name: "CardContent",
    data() {
        return {
            store
        }
    },
    mounted() {
        this.apiMovie()
    },
    methods: {
        apiMovie() {
            axios.get('')
                .then((res) => {
                    console.log(res.data)
                    this.store.arrayMovies = res.data
                })
        },
    }
}
</script>

<style scoped></style>