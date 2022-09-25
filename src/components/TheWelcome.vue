<script setup>
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'
</script>

<script>
  
  export default {
    name: "Clock",
    data() {
      return {
        date : 0,
        hours: 0,
        minutes: 0,
        seconds: 0
      }
    },
    mounted() {
      setInterval(() => this.set(), 1000)
    },
    methods: {
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
    
      },
    }
  }
</script>

<template>

  <div class="container d-flex justify-content-center">
    <div class="LCD d-flex ">
      <h1 class="hours">{{ hours }}</h1>
      <h1 class="h1ider px-3">:</h1>
      <h1 class="minutes">{{ minutes }}</h1>
      <h1 class="h1ider px-3">:</h1>
      <h1 class="seconds">{{ seconds }}</h1>
    </div>
  </div>
  <div class="container d-flex justify-content-center">
    <div class="d-flex ">
        <h1>{{ date }}</h1>
    </div>
  </div>

  </template>
