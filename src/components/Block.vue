<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
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
            reationTime: 0
        }
    },
    mounted() {
        console.log ('components mounted')
        setTimeout(() => {
            this.showBlock =  true
            this.starTimer()
        }, this.delay)

    },
    
    methods: {
        starTimer() {
            this.timer = setInterval(() => {
             this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)

        }
    }

}
</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background-color: #0faf87;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}

</style>