<template>
    <li class="movie">
        <div class="header">
            <div class="left">
                <h3>{{ movie.title }}</h3>
                <div class="countries">
                    <span class="country" v-for="(c, index) in movie.countries" :key="index">{{ c }}</span>
                </div>
                <div class="year">{{ movie.year }}</div>
            </div>

            <div class="score">
                <span><b>imdb:</b> {{ movie.imdb.rating }}</span>
                <span><b>votes:</b> {{ movie.imdb.votes }}</span>
            </div>

        </div>
        <div class="body">
            <p class="plot">{{ movie.plot }}</p>
            <h5>Cast:</h5>
            <ul class="cast-list">
                <li v-for="(person, index) in movie.cast" :key="index" class="cast">
                    {{ person }}
                </li>
            </ul>

        </div>
    </li>
</template>
<script>
export default {
    name: 'MovieCard',
    props: {
        movie: Object
    }
}
</script>
<style scoped>
.movie {
    display: flex;
    flex-direction: column;
    padding: 12px 16px;
    background-color: white;
    border-radius: 12px;
    /* border: 1px solid #2c3e50; */
    filter: drop-shadow(0 0 20px rgba(0, 0, 0, 0.1));
    z-index: 1;

    transition: all 100ms ease-in-out;
}

.movie:hover {
    transform: scale(1.02);
    filter: drop-shadow(0 0 30px rgba(0, 0, 0, 0.1));
    z-index: 2;
    cursor: pointer;

    transition: all 100ms ease-in-out;
}

.movie .header {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
}

.movie .header .left {
    display: flex;
    align-items: baseline;
    gap: 12px;
}

.countries {
    display: flex;
    gap: 8px;
}

.year {
    font-size: 14px;
    font-weight: 600;
    color: #535f6a;
}

.score {
    display: flex;
    gap: 12px;
}

p.plot {
    margin-bottom: 8px;
}

.cast-list {
    /* padding-left: 17px; */
    margin-top: 4px;
    display: flex;
    gap: 8px;
}

.cast {
    font-size: 12px;
    display: flex;
    padding: 4px 12px;
    border-radius: 20px;
    background-color: rgb(225, 225, 225);
}

.cast::marker {
    padding-left: 12px;
}
</style>