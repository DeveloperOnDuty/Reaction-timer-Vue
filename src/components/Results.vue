<template>
    <div class="result-box">
            <p>Reaction Time - {{ score }} ms</p>
            <p class="rank"> {{ rank}}</p>
    </div>
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
        if ( this.score < 250) {
            this.rank = 'WOW! Your score is less than 250'
        } else if (this.score < 400) {
            this.rank = 'Your score is less than 400'
        }else {
            this.rank = 'Cheers, try again!'
        }
    }
}
</script>
<style>
.result-box {
    margin: 0 auto;
    position: relative;
    left: 50%;
    transform: translateX(-50%);
    text-align: center;
    padding-top: 84px;
}
.rank {
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
}

</style>