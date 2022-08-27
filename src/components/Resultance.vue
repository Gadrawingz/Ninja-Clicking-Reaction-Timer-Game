<template>
    <p>
        Reaction time is <span>{{ score }}</span> ms.
    </p>

    <p class="ranking">
        <strong>Acquired Rank: </strong> {{ rank }}.
    </p>
</template>

<script>
export default {
    // We need to accept this props before passing it to template
    props: ['score'],
    data() {
        return {
            rank: null,
        }
    },
    mounted() {
        if(this.score < 200) {
            this.rank = "Super Ninja Fingers"
        } else if (this.score < 300) {
            this.rank = "Ninja Fingers"
        } else if (this.score < 400) {
            this.rank = "Rapid Reflexes"
        } else {
            this.rank = "Snail Paces"
        }
    }
}
</script>


<style scoped>
p span {
    color: blue;
    font-weight: bolder;
}

.ranking {
    margin-top: 15px;
    border-top: 2px solid #2e86c1;
    background: #0b5345;
    color: #FFF;
    padding: 20px;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    font-size: 28px;
    text-transform: capitalize;
    margin-bottom: 0!important;
}
</style>