<template>
    <div>
        <div class="header">
            <a href="/">
                <div class="logo_icon"></div>
            </a>
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
</style>