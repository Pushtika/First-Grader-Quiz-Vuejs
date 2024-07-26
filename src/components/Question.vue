<template>
  <div class="question-container">
    <div class="row q-gutter-md items-center justify-center">
      <div v-if="question.question" class="col-xs-12 col-sm-12 col-md-8 text-h4 q-pa-sm question-text">
        {{ question.question }}
      </div>
      <div v-else class="col-xs-12 col-sm-12 col-md-8 q-pa-sm question-image">
        <img :src="question.img" />
      </div>
      <div class="col-xs-12 col-sm-12 col-md-4 justify-center items-center">
        <q-input class="text-subtitle2 answer-input q-pa-sm" v-model.trim="answer" :readonly="answered" label="Answer" />
      </div>
      <div class="col-xs-12 col-sm-12 col-md-8 q-pa-sm justify-center items-center icon-container">
        <q-icon v-if="answered && question.isCorrect" class="icon q-pa-md" name="img:https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRXXTc21MFYYenRyJ9md9VBn6YSfDBP9W_l2w&s"/>
        <p v-if="answered && !question.isCorrect" class="text-subtitle1 correct-answer">
          <q-icon name="img:https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTYB-ojpXUTVz0hJzgV6Kfl5zEpVJGzd6nDZg&s" class="icon q-pa-md" />
          The correct answer is: {{ correctAnswer }}
        </p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed, watch } from 'vue';

const { question, answered } = defineProps(['question', 'answered']);
const answer = ref('');
const emit = defineEmits(["update-answer"])

watch(answer, (newVal) => {
  emit("update-answer", question.id, newVal)
})

const correctAnswer = computed(() => {
  return question.answer ?? eval(question.question);
})

</script>

<style scoped>
.question-container{
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #C9E3DB; 
  padding: 15px;
  margin-bottom: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.question-text{
  color: #FA1E44;
  text-align: center;
}

.row {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
  width: 100%;
}

.icon{
  width: 50px;
  height: 50px;
  margin-right: 8px;
}

.question-image{
  display: flex;
  justify-content: center;
  align-items: center;
}

.question-image img{
  width: 100%;
  max-width: 225px;
  height: auto;
  border: 2px solid #FA1E44;
  border-radius: 10px;
}

.answer-input{
  border: 2px solid #FA1E44;
  border-radius: 10px;
  transition: transform 0.2s, background-color 0.2s;
}

.answer-input:hover{
  transform: scale(1.05);
}

.correct-answer {
  color: red; 
  text-align: center;
}

.icon-container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}

</style>