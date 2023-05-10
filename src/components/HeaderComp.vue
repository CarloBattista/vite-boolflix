<template>
    <!-- Header -->
    <div class="header">
        <a href="/">
            <div class="logo_icon"></div>
        </a>
        <div class="container_search">
            <div class="box_icon">
                <i class="fa-solid fa-magnifying-glass"></i>
            </div>
            <input v-model="this.store.searchBar" @keyup="$emit('callApi')" @input="showDiv" class="searchInput" type="text"
                placeholder="Cerca Film o Serie TV">
        </div>
    </div>
    <!-- SubHeader -->
    <div v-if="showSubHeader" class="subHeader">
        <div class="region_left">
            <h2 class="title">Hai cercato: <span class="searchResult">{{ this.store.searchBar }}</span></h2>
        </div>
    </div>
</template>

<script>
import { store } from "../store"

export default {
    name: "HeaderComp",
    data() {
        return {
            store,
            showSubHeader: false,
        }
    },
    methods: {
        // Quando nell input si inizia a scrivere qualcosa appare il subHeader
        showDiv() {
            if (this.store.searchBar.length > 0) {
                this.showSubHeader = true;
            } else {
                this.showSubHeader = false;
            }
        },
    }
}
</script>

<style scoped>
/* Header */
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

/* Search */
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

/* SubHeader */
.subHeader {
    width: 100%;
    height: 68px;
    padding: 0 60px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    user-select: none;
}

.title {
    color: #fff;
    font-size: 1rem;
    font-weight: 500;
}

.searchResult {
    color: #fff;
    font-weight: 700;
}

@media only screen and (max-width: 700px) {

    .header,
    .subHeader {
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