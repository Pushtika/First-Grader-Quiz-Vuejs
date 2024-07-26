<template>
    <div class="q-pa-md row items-start q-gutter-md">
        <q-card class="my-card" @click="navigateToQuiz(q.id)" v-for="q in quiz.categories" :key="q.id">
            <img :src="q.img">
            
            <q-card-section>
                <div class="card-details">
                    <div class="text-subtitle2 q-pa-sm">{{ q.label }}</div>
                </div>
            </q-card-section>
        </q-card>
    </div>
</template>

<script setup>
import { useRouter } from 'vue-router';

const router = useRouter();

const { quiz } = defineProps(['quiz']);

const navigateToQuiz = (id) => {
    router.push(`/quiz/${quiz.subject}/${id}`)
}

</script>

<style scoped>

.my-card{
    width: 100%;
    max-width: 250px;
    background-color: #C9E3DB;
}

.my-card img{
    width: 250px;
    height: 250px;
}

.card-details{
    display: flex;
    justify-content: flex-end;
    height: 80px;
}

</style>