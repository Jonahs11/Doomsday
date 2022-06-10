<template>

<h1> {{count}}</h1>

</template>

<script lang="ts">

import { defineComponent } from "vue";

export default defineComponent({
    name: "TimerComp",
    data () {
        return {
            count : 5
        }
    },
    watch: {
        count: {
            handler(value) {
                if (value > 0) {
                    setTimeout(() => {
                        this.count--;
                    }, 1000);
                }
                else {
                    console.log("Timer at 0");
                    this.time_out();
                }
            },
            immediate: true
        }
    },
    methods: {
        time_out: function() {
            console.log("time out");
        }
    }
})


</script>
