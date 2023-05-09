<template>
    <div>
        <div class="header">
            <a href="/">
                <div class="logo_icon"></div>
            </a>
            <div class="secondaryNav">
                <div class="search">
                    <div class="box_icon">
                        <i class="fa-solid fa-magnifying-glass"></i>
                    </div>
                    <input type="text" class="searchInput" placeholder="Cerca Film o Serie TV">
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "HeaderComp",
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

.search {
    position: relative;
    width: 250px;
    height: 30px;
}

.searchInput {
    width: 100%;
    height: 100%;
    border: 1px solid #fff;
    outline: none;
    background: rgba(0, 0, 0, .7);
    padding: 0 30px;
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
    width: 30px;
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

@media only screen and (max-width: 600px) {
    .header {
        height: 42px;
        padding: 0 4%;
    }

    .header a {
        width: 79px;
        height: 21px;
    }

    .search {
        width: 180px;
        height: 25px;
    }

    .box_icon .fa-magnifying-glass {
        font-size: .8rem;
    }
}
</style>