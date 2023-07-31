<template >
    <div>
        <p>Reaction time: <span class="score"> {{ score }}</span> ms</p>
        <p>Rank: <span class="score"> {{ rank }}</span> </p>
    </div>
</template>
<script>
export default {
    props: ['score', 'rank'],






}

</script>
<style >
.score {
    color: blue;
}

p {
    font-weight: bold;
    font-family: monospace;
    font-size: 1.5em;
}
</style>