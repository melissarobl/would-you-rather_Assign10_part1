<script setup>
import { ref, watch } from 'vue'

defineProps({
  question: String,
  answer1: String,
  answer2: String,
})

const emit = defineEmits([
    'answer-selected'
])

const choice = ref('')

// function choiceMade() {
//   //emit even to tell parent that user has made choice.
//   emit('answer-selected', choice.value)
//  * have to add v-on:change="choiceMade" to each input below if using this
// }
// this takes care of returning all the data, functions, computed properties, so return statement not needed.

watch(choice, () => {
  emit('answer-selected', choice.value)
    })
</script>

<template>  <!--this is the HTML that VUE can use. Similar to <div id="app"> seen previously--> <!--'v-on:' is same as @click -->

  <div id="wyr">
    <h2>Make your choice!</h2>

    <p>{{ question }}</p>

      <div>
        <input v-model="choice" v-bind:value="answer1" type="radio" id="answer-1">
        <label for="answer-1">{{ answer1 }}</label>

        <!-- this value attribute is the HTML value, for what data an input stores -->
        <input v-model="choice" v-bind:value="answer2" type="radio" id="answer-2">
        <label for="answer-2">{{ answer2 }}</label>
      </div>
  </div>

</template>

<style scoped>
#wyr {
  background-color: greenyellow;
}

p{
  font-family: "Courier New"
}

</style> <!-- 'scope' meaning CSS here will apply to one component, not the entire page! -->
