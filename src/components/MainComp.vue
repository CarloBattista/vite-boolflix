<template>
    <div class="mainView">
        <div class="header">
            <a href="/">
                <div class="logo_icon"></div>
            </a>
            <div class="container_search">
                <div class="box_icon">
                    <i class="fa-solid fa-magnifying-glass"></i>
                </div>
                <input v-model="this.store.searchBar" @keyup="apiMovies(), apiShows(), connectAllContent()"
                    class="searchInput" type="text" placeholder="Cerca Film o Serie TV">
            </div>
        </div>
        <div class="container_cards">
            <div class="card" v-for="(element, index) in store.allContents" :key="index">
                <div class="imageWrap">
                    <img :src="`https://image.tmdb.org/t/p/w342/${element.poster_path}`" alt="element.title">
                </div>
                <div class="infoWrap">
                    <h2 class="titleContent">{{ element.title }}</h2>
                    <h2 class="titleContent">{{ element.name }}</h2>
                    <h3 class="originalTitleContent">{{ element.original_title }}</h3>
                    <h3 class="originalTitleContent">{{ element.original_name }}</h3>
                    <div class="container_language_container">
                        <img v-if="element.original_language == 'it'" class="flag_lang" src="/_resources/flags/it_flag.svg"
                            alt="">
                        <img v-else-if="element.original_language == 'en'" class="flag_lang"
                            src="/_resources/flags/en_flag.svg" alt="">
                        <img v-else-if="element.original_language == 'fr'" class="flag_lang"
                            src="/_resources/flags/fr_flag.svg" alt="">
                        <img v-else="element.original_language == 'sp' " class="flag_lang"
                            src="/_resources/flags/sp_flag.svg" alt="">
                    </div>
                    <p class="synopsisContent">{{ element.overview }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from "axios";
import { store } from "../store"

export default {
    name: "MainComp",
    data() {
        return {
            store
        }
    },
    methods: {
        apiMovies() {
            axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${store.myApiKey}&query=${store.searchBar}&language=${store.languageApi}`)
                .then((res) => {
                    this.store.arrayMovies = res.data.results
                    console.log(res.data)
                })
        },
        apiShows() {
            axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${store.myApiKey}&query=${store.searchBar}&language=${store.languageApi}`)
                .then((res) => {
                    this.store.arrayShows = res.data.results
                    console.log(res.data)
                })
        },
        connectAllContent() {
            this.store.allContents = this.store.arrayMovies.concat(this.store.arrayShows)
        },
    },
}
</script>

<style scoped>
.mainView {
    position: relative;
    z-index: 1;
    width: 100%;
}

.header {
    position: sticky;
    z-index: 999;
    width: 100%;
    height: 68px;
    padding: 0 60px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: rgb(0, 0, 0);
    background: linear-gradient(0deg, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, 1) 100%);
}

.header a {
    width: 92px;
    height: 25px;
}

.logo_icon {
    background-image: url(/_resources/netflix_logo.svg);
    background-position: center;
    background-repeat: no-repeat;
    background-size: contain;
    width: 100%;
    height: 100%;
}

.container_search {
    position: relative;
    width: 250px;
    height: 30px;
}

.searchInput {
    width: 100%;
    height: 100%;
    padding: 0 35px;
    outline: none;
    border: 1px solid rgba(255, 255, 255, .7);
    background: rgba(0, 0, 0, .7);
}

.searchInput::placeholder {
    color: #aaa;
    font-size: .8rem;
    font-weight: 400;
}

.searchInput[type=text] {
    color: #fff;
    font-size: .8rem;
    font-weight: 400;
}

.box_icon {
    position: absolute;
    top: 0;
    left: 0;
    width: 35px;
    height: 100%;
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
}

.box_icon .fa-magnifying-glass {
    color: #fff;
    font-size: 1rem;
}

.container_cards {
    width: 100%;
    padding: 30px 60px;
    display: grid;
    gap: 1em;
    grid-template-columns: repeat(6, 1fr);
}

.card {
    position: relative;
    width: 100%;
    height: auto;
    cursor: pointer;
    overflow: hidden;
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

.container_language_container {
    width: 100%;
    margin-bottom: 5px;
    display: flex;
    align-items: center;
}

.flag_lang {
    width: 23px;
    height: auto;
}

@media only screen and (max-width: 700px) {
    .header {
        padding: 0 4%;
    }

    .container_search {
        width: 200px;
    }

    .box_icon .fa-magnifying-glass {
        font-size: .8rem;
    }

    .container_cards {
        padding: 0 4%;
        grid-template-columns: repeat(3, 1fr);
    }
}</style>