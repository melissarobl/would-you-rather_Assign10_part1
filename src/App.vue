<script setup>
import WouldYouRather from './components/WouldYouRather.vue'

import { ref } from 'vue' //declare reactive state

//declare reactive data for question, answer and userSelection
const wyrQuestion = ref('Would you rather be able to read minds or see one day into the future?')
const wyrAnswer1 = ref('Read Minds')
const wyrAnswer2 = ref('See One Day into Future')

// this will store the user's answer once they made a choice (also reactive data)
const userSelection = ref('')

function updateUserSelection(userChoice){
  userSelection.value = `Thanks! You Chose: ${userChoice}`
}
//what is in choice.value in child will end up as the argument, userChoice
// then userChoice will be set as userSelection.value and can be used by parent

</script>

<template>

  <div id="app-component">

    <h1>Would You Rather?</h1>

    <!--this information binds the reactive data in this parent with the reactive data in the child.
    Doesn't have to be reactive data, could be regular string, but in this case it is reactive. Has to be a string, though
    since that is what child is expecting based on Props info entered-->
    <WouldYouRather
        v-bind:question="wyrQuestion"
        v-bind:answer1="wyrAnswer1"
        v-bind:answer2="wyrAnswer2"
        v-on:answer-selected="updateUserSelection"
    ></WouldYouRather>
    <!--when answer-selected is received, updateUserSelection event is called -->

    <p> {{ userSelection }}</p>

    <!--userSelection can be displayed because it is made available through function updateUserSelection -->


  </div>

</template>


<style scoped>

#app-component {
  font-size: 1.5em;
  background-color: #535bf2;
  padding: 35px;
}

p{
  font-family: Gabriola;
  font-size: 30px;
  color: blanchedalmond;
}
</style>
