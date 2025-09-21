<template>
    <div>
        <h1>{{ quiz.title }}</h1>
        <Progress :value="step" :max="quiz.questions.length-1" v-if="state==='question'"/>

        <Question v-if="state==='question'" :key="question.question" :question="question" @answer="addAnswer" />
        <Recap v-if="state==='recap'"  :answers="answers" :quiz="quiz" />

  
    </div>
</template>

<script setup>
import { ref, computed} from 'vue'
import Progress from './Progress.vue'
import Question from './Question.vue'
import Recap from './Recap.vue'
const props = defineProps  ({
    quiz:Object
})

const step = ref(0)
const answers = ref(props.quiz.questions.map(() => null))
const state =ref('question')
const addAnswer = (answer) =>{

  
    answers.value[step.value] = answer;
    step.value++; 
    if(step.value  == props.quiz.questions.length)
    {
        state.value='recap'
       
    }
    
}
const question = computed (() =>
    props.quiz.questions[step.value]
)
</script>