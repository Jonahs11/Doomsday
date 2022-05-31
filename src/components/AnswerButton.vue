<template>
<div class="answerbutton">

    <button @click="answer_clicked"> {{day}} </button>

</div>

</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    name: "AnswerButton",
    props: {
        day: String,
        numerical_day: Number
    },
    methods: {
        answer_clicked: function() {
            this.$emit("clicked", this.numerical_day);   
        }
    }
})

</script>