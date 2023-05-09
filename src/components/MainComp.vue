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
                <input v-model="this.store.searchBar" class="searchInput" type="text" placeholder="Cerca Film o Serie TV">
            </div>
        </div>
        <div class="container_cards">
            <div class="card">
                <div class="imageWrap">
                    <img src="" alt="">
                </div>
                <div class="infoWrap">
                    <h2 class="titleContent"></h2>
                    <h2 class="originalTitleContent"></h2>
                    <p class="synopsisContent"></p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
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
            axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${store.myApiKey}&query=${store.searchBar}`)
                .then((res) => {
                    this.store.arrayMovies = res.data.results
                    console.log(res.data)
                })
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
}
</style>