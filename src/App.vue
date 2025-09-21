<template>
 
  <div v-if="state == 'error'">
    Imposible de charger les données 
  </div>
  <div :aria-busy="state == 'loading'">
    <Quiz :quiz="quiz" v-if="quiz" />
    <div v-else>
      pas de titre 
    </div>  
  </div>
 
 
  
</template>
<script setup>

  import {  ref , onMounted} from "vue";
  import Quiz from './Components/Quiz.vue'

  const quiz = ref('')
  const state = ref('loading')

onMounted(() =>{
  fetch('/quiz.json')
  .then(r => {
    if(r.ok)
    {
      return r.json()
      
    }
    throw new Error('Impossible de recupier le Json ')
  })
  .then(data => {
   
    quiz.value = data
    state.value='idle'
  })
  .catch(e =>{
    state.value = 'error' ; 
  })
  
})
  
 

</script>
