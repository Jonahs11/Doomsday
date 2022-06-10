<template>

    <button @click="go_home"> Back </button>
    <DateComp @correct-answer="correct_choice" @incorrect-answer="incorrect_choice"> </DateComp>
    <correct-counter-vue v-bind:counter="correct_in_row"> </correct-counter-vue>


</template>


<script lang="ts">
import { defineComponent } from "vue";
import DateComp from './Date.vue';
import CorrectCounterVue from "./CorrectCounter.vue";

export default defineComponent({
    name: "PracticeComp",
    components: {
        DateComp,
        CorrectCounterVue
    },
    data() {
        return {
            correct_in_row : 0
        }
    },

    methods: {
        go_home: function() {
            this.$emit("go-home");
        },
        correct_choice: function() {
            this.correct_in_row++;
        },
        incorrect_choice: function() {
            this.correct_in_row = 0;
        }
    }
})


</script>