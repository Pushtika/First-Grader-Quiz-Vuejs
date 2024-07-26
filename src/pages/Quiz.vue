<template>
    <div class="quiz-container">
        <div class="controls-container">
            <q-btn class="btn-go-back" label="Go back" glossy @click="goBack"/>
            <q-select
            v-model="numberOfQuestions"
            :options="options"
            label="Choose the number of questions"
            class="number-of-questions-select"
            :disable="answered"
            />
        </div>
        <div v-for="question in numberOfQuestionsDisplayed" :key="question.id">
            <Question :question="question" :answered="answered" @update-answer="updateAnswer" />
        </div>
        <div class="submit-container">
            <q-btn v-if="!answered" class="btn-submit" label="Submit" @click="submitAnswers()" glossy />
            <p v-else class="text-h4 text-center" style="color: #E42C6A">Total: {{ numberOfCorrectAnswers }} correct answers out of {{ numberOfQuestionsDisplayed.length }} </p>
        </div>
    </div>
</template>

<script setup>
import Question from '../components/Question.vue';
import {useRoute, useRouter} from 'vue-router';
import english from '../data/English.json';
import math from '../data/Math.json';
import french from '../data/French.json';
import { ref, computed  } from 'vue';

const route = useRoute();
const router = useRouter();
const mergedData = [
{ id: math.id, subject: math.subject, categories: math.categories },
{ id: english.id, subject: english.subject, categories: english.categories },
{ id: french.id, subject: french.subject, categories: french.categories },
];
const quizes = ref(mergedData);
const options = [5, 10, 15];
const answered = ref(false);
const numberOfQuestions = ref(5);

const quizId = parseInt(route.params.id);
const subject = route.params.subject;

const categories = quizes.value.find(q => q.subject === subject).categories;
const questions = categories.find(q => q.id === quizId).questions;

const numberOfQuestionsDisplayed = computed(() => {
    const shuffled = [...questions].sort(() => 0.5 - Math.random());
    
    // Slice the array to get the number of questions required
    return shuffled.slice(0, numberOfQuestions.value);
})

const goBack = () => {
    router.push('/');
}

const numberOfCorrectAnswers = ref(0);

const updateAnswer = (id, answer) => {
    const question = numberOfQuestionsDisplayed.value.find(q => q.id === id);
    if (question){
        question.userAnswer = answer;
    }
}

const submitAnswers = () => {
    answered.value = true;
    numberOfQuestionsDisplayed.value.forEach(question => {
        if (question.answer){
            question.isCorrect = question.userAnswer?.toLocaleLowerCase() === question.answer.toLocaleLowerCase();
        }
        else{
            question.isCorrect = question.userAnswer == eval(question.question);
        }
        
        if (question.isCorrect) {
            numberOfCorrectAnswers.value++;
        }
    });
}

</script>

<style scoped>
.banner{
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #e6f7e0;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.logo{
    height: 80px;
}

.quiz-container{
    background-color: #5AB190;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.submit-container{
    display: flex;
    justify-content: center;
    margin-top: 20px;
}

.btn-submit{
    font-size: 1.5em;
    background-color: #FA1E44;
    color: white;
    border-radius: 10px;
    transition: transform 0.2s;
}

.btn-submit:hover{
    transform: scale(1.1);
}

.controls-container {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 20px;
    gap: 15px; 
}

.btn-go-back {
    font-size: 1.2em;
    background-color: #FA1E44; 
    color: white;
    border-radius: 10px;
    transition: transform 0.2s;
}

.btn-go-back:hover {
    transform: scale(1.1);
}

.number-of-questions-select {
    font-size: 1.2em;
    background-color: #C9E3DB; 
    border: 2px solid #FA1E44; 
    border-radius: 10px;
    width: 100%;
    max-width: 220px;
}

</style>