<template>
    <div>
        <div class="header">
            <a href="/">
                <div class="logo_icon"></div>
            </a>
            <div class="secondaryNav">
                <SearchBar />
            </div>
        </div>
    </div>
</template>

<script>
import SearchBar from './SearchBar.vue';

export default {
    name: "HeaderComp",
    components: {
        SearchBar,
    },
    data() {
        return {

        }
    }
}
</script>

<style scoped>
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
    background-size: cover;
    width: 100%;
    height: 100%;
}

@media only screen and (max-width: 600px) {
    .header {
        height: 42px;
        padding: 0 4%;
    }

    .header a {
        width: 79px;
        height: 21px;
    }
}
</style>