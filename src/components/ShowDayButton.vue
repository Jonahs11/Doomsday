<template>
<div class="answerbutton">
    <button type="button" @click="button_clicked"> Show Day of Week </button>
</div>
</template>


<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    name: 'AnswerButton',
    data() {
        return {
            clicked: "Button has been clicked"
        }
    },
    methods: {
        button_clicked: function () {
            this.$emit("clicked", this.clicked);
        }
    }
})

</script>