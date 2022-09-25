<template>
    <div class="container d-flex justify-content-around" style="width: 400px;">
        
        <h2 style="width: 50px;">{{ minute }}</h2>
        <h2>:</h2>
        <h2 style="width: 50px;">{{ second }}</h2>
        <h2>:</h2>
        <h2 style="width: 50px;">{{ milisecond }}</h2>
    </div>

    <div class="container d-flex justify-content-center mt-5 " style="width: 400px;">
        <button @click="start()" class="btn" style="background-color: hsla(160, 100%, 37%, 1); margin-right: 10px">Start</button>
        <button @click="stop" class="btn" style="background-color: hsla(160, 100%, 37%, 1); margin-right: 10px">Stop</button>
        <button @click="reset" class="btn" style="background-color: hsla(160, 100%, 37%, 1); margin-right: 10px">Reset</button>
    </div>
    
</template>


<script>
    export default {
        name: "Timer",
        data () {
            return {
                milisecond: 0,
                minute: 0,
                second: 0,
                isStart: false,
                interval: ''
            }
        },
        mounted() {
        
        },
        methods: {
            start() {
                this.interval = setInterval(this.startTimer, 10);
            },
            stop() {
                clearInterval(this.interval)
            },
            reset() {
                this.milisecond = 0
                this.minute = 0
                this.second = 0
            },
            startTimer() {
                this.milisecond++;
                if(this.milisecond == 100){
                   this.second++
                   this.milisecond = 0
                }
                if(this.second == 60){
                   this.minute++
                    this.second = 0
                }
            }
        }
    }
</script>