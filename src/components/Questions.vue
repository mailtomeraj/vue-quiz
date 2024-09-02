<template>
    <div class="questions-ctr">
        <div class="progress">
            <div class="bar"
            :style="{width:`${(questionAnswered/questions.length)*100}%`}"
            ></div>
            <div class="status">{{questionAnswered}} out of {{questions.length}} questions answered</div>
        </div>
        <div class="single-question" v-for="(question, qi) in props.questions" 
        :key="question.q"  v-show="questionAnswered == qi">
            <div class="question">{{question.q}}</div>
            <div class="answers">
                <div class="answer" v-for="answer in question.answers" :key="answer.text"
                @click.prevent="selectAnswer(answer.is_correct)"
                >
                    {{answer.text}}
                </div>               
            </div>
        </div>
    </div>
</template>
<script setup>
import { defineProps } from 'vue';
import { defineEmits } from 'vue'

const emit = defineEmits(['question-answered'])

const props = defineProps(['questions','questionAnswered'])

const selectAnswer = (is_correct) => {
    
    emit("question-answered", is_correct)

}

</script>

<style lang="scss" scoped>

</style>