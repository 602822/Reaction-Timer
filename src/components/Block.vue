<template>
    <div v-if="showBlock" @click="stopTimer" class="block">
        click me
    </div>
</template>
<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0,
        }
    },

    mounted() {
        console.log('mounted');
        setTimeout(() => {
            this.showBlock = true;
            this.startTimer();
            console.log(this.delay);
        }, this.delay)




    }
    ,
    updated() {
        console.log('updated');
    },

    unmounted() {
        console.log('unmounted');

    },

    methods: {

        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10;
            }, 10)

        },

        stopTimer() {
            clearInterval(this.timer);
            console.log(this.reactionTime);
            this.$emit('block-clicked', this.reactionTime);
        },
    }


}

</script>
<style>
.block {
    width: 400px;
    border-radius: 20px;
    background: lightgreen;
    color: darkgreen;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>