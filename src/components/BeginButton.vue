<template>

<div class="beginbutton">
    <button class="button" @click="clicked"> Practice Guessing </button>
</div>

</template>


<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    name: "BeginButton",
    methods: {
        clicked: function() {
            console.log("Beging button was clicked");
            this.$emit("begin-clicked");
        }
    }
})
</script>


<style scoped>

.button {
    background-color: greenyellow;
    text-align: center;
    font-size: 16px;
}

</style>