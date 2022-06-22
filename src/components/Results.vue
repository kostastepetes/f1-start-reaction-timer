<template>
    <p>Reaction time - {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 250) { this.rank = "Proper F1 Driver" }
        else if (this.score < 400) { this.rank = "Almost as rapid as a F1 Driver" }
        else { this.rank = "Way Too Slow" }
    }
}
</script>

<style>
.rank {
    font-size: 1.4em;
    color: #c3c5ca;
    font-weight: bold;
}
</style>