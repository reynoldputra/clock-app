<script setup>
import WelcomeItem from './WelcomeItem.vue'
import IconAlarm from './icons/IconAlarm.vue'
import TheWelcome from './TheWelcome.vue'

</script>

<template>
    <TheWelcome />
    <div class="container d-flex justify-content-center mt-5">
        <div class="sub-container d-flex flex-column align-items-center">
            <h1 class="text-white">Set alarm</h1>
            <div class="cs-form mt-3 d-flex">
                <input v-model="dateValue" type="time" class="form-control" style="margin-right:10px; width: 200px;"/>
                <button @click="setAlarm(dateValue)" class="btn" style="background-color: hsla(160, 100%, 37%, 1)" >
                    <h4>Add</h4>
                </button>
            </div>
        </div>
    </div>
    <div class="mt-5">
        <WelcomeItem v-for="alarm in alarms" class="my-3">
            <template #icon>
                <IconAlarm />
            </template>
            {{ alarm }}
        </WelcomeItem>
    </div>
</template>

<script>
    export default {
    name: "Alarm",
    data() {
      return {
        date : 0,
        hours: 0,
        minutes: 0,
        seconds: 0,
        dateValue: "",
        now: "",
        alarms: []
      }
      },
    mounted() {
        setInterval(() => this.set(), 1000)
    },
    methods: {
        setAlarm(value){
            this.alarms.push(value)
            this.alarms.sort()
            console.log(this.alarms)
        },
        set() {
          const date = new Date();
          let hours = date.getHours();
          let minutes = date.getMinutes();
          let seconds = date.getSeconds();
          hours = hours <= 9 ? `${hours}`.padStart(2, 0) : hours;
          minutes = minutes <= 9 ? `${minutes}`.padStart(2, 0) : minutes;
          seconds = seconds <= 9 ? `${seconds}`.padStart(2, 0) : seconds;
          this.date = date.toDateString()
          this.hours = hours;
          this.minutes = minutes;
          this.seconds = seconds;
          this.now = `${hours}:${minutes}`;
          this.cek()
          console.log(this.now)
          console.log(this.alarms)
        },
        cek(){
            this.alarms.forEach(alarm => {
                if(this.now == alarm){
                    this.alertTime()
                    let ind = this.alarms.indexOf(alarm)
                    this.alarms.splice(ind)
                }
            });
        },
        alertTime(){
            let audio = new Audio('src/assets/audio/rington.wav');
            audio.play();
        }
    }
    }
  </script>