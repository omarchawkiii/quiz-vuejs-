<template>
    <h1>Recap</h1>

    Score : {{ score }} /  {{ props.quiz.questions.length }}

    <div> {{ hasWon ? props.quiz.success_message : props.quiz.failure_message }}</div>
</template>

<script setup>
import {computed} from 'vue'
const props = defineProps({
    quiz: Object,
    answers:Array
})

const score = computed(() =>{
    return props.quiz.questions.reduce((acc,question , k) =>{
        console.log()
        if(props.answers[k] === question.correct_answer )
        {
            return acc +1 ;
        }
        else
        {
            return acc ; 
        }

    },0)
})

const hasWon = computed(() =>score.value> props.quiz.minimum_score)
</script>