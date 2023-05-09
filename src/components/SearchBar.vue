<template>
    <div>
        <div class="search">
            <div class="box_icon">
                <i class="fa-solid fa-magnifying-glass"></i>
            </div>
            <input v-model="this.store.searchBar" type="text" class="searchInput" placeholder="Cerca Film o Serie TV">
        </div>
    </div>
</template>

<script>
import { store } from "../store";

export default {
    name: "SearchComp",
    data() {
        return {
            store
        }
    }
}
</script>

<style scoped>
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
    .search {
        width: 180px;
        height: 25px;
    }

    .box_icon .fa-magnifying-glass {
        font-size: .8rem;
    }
}
</style>