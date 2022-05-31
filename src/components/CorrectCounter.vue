<template>
<div class="boxed">
    {{counter}}
</div>
</template>


<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    name: "CorrectAnswerCounter",
    props: {
        counter: Number
    },
    // data() {
    //     return {
    //         counter: 0
    //     }
    // },
    methods: {
        // increment_counter: function() {
        //     this.counter++;
        // }
    },
})

</script>

<style scoped>

.boxed {
    border: 1px solid green;
}

</style>