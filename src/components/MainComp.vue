<template>
    <!-- Comp Header -->
    <HeaderComp @callApi="apiMovies(), apiShows(), connectAllContent()" />
    <!-- Main -->
    <div class="mainView">
        <!-- Container Cards -->
        <div class="container_cards">
            <!-- Card ciclate per film -->
            <div v-if="store.arrayMovies.length >= 1" class="ccontainer_movies">
                <div class="container_heading">
                    <h2 class="Heading">Film</h2>
                </div>
                <div class="grid_card_container">
                    <div class="card" v-for="(element, index) in store.arrayMovies" :key="index">
                        <div class="imageWrap">
                            <img :src="`https://image.tmdb.org/t/p/w342/${element.poster_path}`" :alt="element.title">
                        </div>
                        <div class="infoWrap">
                            <h2 class="titleContent">{{ element.title }}</h2>
                            <h3 class="originalTitleContent" v-if="element.original_title !== element.title">{{element.original_title }}</h3>
                            <div class="container_language_container">
                                <img v-if="element.original_language == 'it'" class="flag_lang" src="/_resources/flags/it_flag.svg"
                                    alt="flag_it">
                                <img v-else-if="element.original_language == 'en'" class="flag_lang"
                                    src="/_resources/flags/en_flag.svg" alt="flag_en">
                                <img v-else-if="element.original_language == 'fr'" class="flag_lang"
                                    src="/_resources/flags/fr_flag.svg" alt="flag_fr">
                                <img v-else="element.original_language == 'sp' " class="flag_lang"
                                    src="/_resources/flags/sp_flag.svg" alt="flag_sp">
                            </div>
                            <div class="vote_rating_container">
                                <div v-if="parseInt(element.vote_average / 2) == 5">
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                </div>
                                <div v-else-if="parseInt(element.vote_average / 2) == 4">
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                </div>
                                <div v-else-if="parseInt(element.vote_average / 2) == 3">
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                </div>
                                <div v-else-if="parseInt(element.vote_average / 2) == 2">
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                </div>
                                <div v-else-if="parseInt(element.vote_average / 2) == 1">
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                </div>
                                <div v-else-if="parseInt(element.vote_average / 2) == 0">
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <!-- Card ciclate per serie tv -->
            <div v-if="store.arrayShows.length >= 1" class="ccontainer_shows">
                <div class="container_heading">
                    <h2 class="Heading">Serie TV</h2>
                </div>
                <div class="grid_card_container">
                    <div class="card" v-for="(element, index) in store.arrayShows" :key="index">
                        <div class="imageWrap">
                            <img :src="`https://image.tmdb.org/t/p/w342/${element.poster_path}`" :alt="element.title">
                        </div>
                        <div class="infoWrap">
                            <h2 class="titleContent">{{ element.name }}</h2>
                            <h3 class="originalTitleContent" v-if="element.original_name !== element.name">{{element.original_title }}</h3>
                            <div class="container_language_container">
                                <img v-if="element.original_language == 'it'" class="flag_lang" src="/_resources/flags/it_flag.svg"
                                    alt="flag_it">
                                <img v-else-if="element.original_language == 'en'" class="flag_lang"
                                    src="/_resources/flags/en_flag.svg" alt="flag_en">
                                <img v-else-if="element.original_language == 'fr'" class="flag_lang"
                                    src="/_resources/flags/fr_flag.svg" alt="flag_fr">
                                <img v-else="element.original_language == 'sp' " class="flag_lang"
                                    src="/_resources/flags/sp_flag.svg" alt="flag_sp">
                            </div>
                            <div class="vote_rating_container">
                                <div v-if="parseInt(element.vote_average / 2) == 5">
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                </div>
                                <div v-else-if="parseInt(element.vote_average / 2) == 4">
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                </div>
                                <div v-else-if="parseInt(element.vote_average / 2) == 3">
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                </div>
                                <div v-else-if="parseInt(element.vote_average / 2) == 2">
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                </div>
                                <div v-else-if="parseInt(element.vote_average / 2) == 1">
                                    <img src="/_resources/icons/star-solid.svg" alt="star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                </div>
                                <div v-else-if="parseInt(element.vote_average / 2) == 0">
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                    <img src="/_resources/icons/star-regular.svg" alt="half star" />
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from "axios";
import { store } from "../store"

import HeaderComp from "./HeaderComp.vue";

export default {
    name: "MainComp",
    components: {
        HeaderComp
    },
    data() {
        return {
            store,
        }
    },
    methods: {
        apiMovies() {
            axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${store.myApiKey}&query=${store.searchBar}&language=${store.languageApi}`)
                .then((res) => {
                    this.store.arrayMovies = res.data.results
                    // console.log(res.data)
                })
        },
        apiShows() {
            axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${store.myApiKey}&query=${store.searchBar}&language=${store.languageApi}`)
                .then((res) => {
                    this.store.arrayShows = res.data.results
                    // console.log(res.data)
                })
        },
        connectAllContent() {
            this.store.allContents = this.store.arrayMovies.concat(this.store.arrayShows)
        },
    },
}
</script>

<style scoped>
/* Main */
.mainView {
    position: relative;
    z-index: 1;
    width: 100%;
}

/* Container Cards */
.container_cards {
    width: 100%;
    padding: 3vw 60px;
}

.ccontainer_movies{
    margin-bottom: 6vw;
}

.container_heading{
    width: 100%;
    margin-bottom: 12px;
}

.Heading{
    color: #fff;
    font-size: 1.4rem;
    font-weight: 500;
}

.grid_card_container{
    display: grid;
    gap: 1em;
    grid-template-columns: repeat(6, 1fr);
}

/* Card */
.card {
    position: relative;
    width: 100%;
    height: auto;
    cursor: pointer;
    overflow: hidden;
    background: rgb(0, 0, 0);
    background: linear-gradient(0deg, rgba(8, 8, 8, 1) 0%, rgba(0, 0, 0, 0) 100%);
    transition: transform 250ms ease 100ms;
}

.imagwWrap {
    width: 100%;
    height: 100%;
}

.imagwWrap img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    aspect-ratio: 9 / 13;
}

.infoWrap {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    padding: 1em;
    display: none;
    flex-direction: column;
    overflow: auto;
    background: rgba(0, 0, 0, .7);
}

.infoWrap::-webkit-scrollbar {
    width: 0;
}

.card:hover {
    transform: scale(1.1);
}

.card:hover .infoWrap {
    display: flex;
}

.titleContent {
    color: #fff;
    font-size: 1rem;
    font-weight: 600;
    margin-bottom: 5px;
}

.originalTitleContent {
    color: #fff;
    font-size: .8rem;
    font-weight: 400;
    margin-bottom: 5px;
}

.synopsisContent {
    color: #aaa;
    font-size: .6rem;
    font-weight: 400;
}

.container_language_container,
.vote_rating_container {
    width: 100%;
    margin-bottom: 5px;
    display: flex;
    align-items: center;
}

.flag_lang {
    width: 23px;
    height: auto;
}

.vote_rating_container div {
    width: 18px;
    height: auto;
    display: flex;
    align-items: center;
}

@media only screen and (max-width: 700px) {
    .container_cards {
        padding: 3vw 4%;
    }
    .grid_card_container{
        grid-template-columns: repeat(3, 1fr);
    }

    .titleContent {
        font-size: .8rem;
    }

    .originalTitleContent {
        font-size: .6rem;
    }
}</style>