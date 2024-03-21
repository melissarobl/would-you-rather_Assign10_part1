<script setup>
import WouldYouRather from './components/WouldYouRather.vue'

import { ref } from 'vue'

const wyrQuestion = ref('Would you rather be able to read minds or see one day into the future?')
const wyrAnswer1 = ref('Read Minds')
const wyrAnswer2 = ref('See One Day into Future')

// this will store the user's answer once they made a choice

const userSelection = ref('')

function updateUserSelection(userChoice){
  userSelection.value = `Thanks! You Chose: ${userChoice}`
}

</script>

<template>

  <div id="app-component">

    <h1>Would You Rather?</h1>

    <WouldYouRather
        v-bind:question="wyrQuestion"
        v-bind:answer1="wyrAnswer1"
        v-bind:answer2="wyrAnswer2"
        v-on:answer-selected="updateUserSelection"
    ></WouldYouRather>

    <p>{{ userSelection }}</p>

  </div>

</template>


<style scoped>

#app-component {
  font-size: 1.5em;
  background-color: #535bf2;
  padding: 35px;
}

p{
  font-family: "Bauhaus 93";
  font-size: 20px;
}
</style>
