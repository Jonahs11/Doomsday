<template>

<button @click="go_home"> Back </button>
<DateComp> </DateComp>
<TimerComp> </TimerComp>

</template>


<script lang="ts">

import { defineComponent } from "vue";
import DateComp from "./Date.vue";
import TimerComp from "./Timer.vue";

export default defineComponent({
    name: "ChallengeComp",
    components: {
        DateComp,
        TimerComp
    },
    data () {
        return {
            new_date : false
        }
    },
    methods: {
        go_home: function() {
            this.$emit("go-home");
        }
    }

})

</script>