<template>
<div class="newdate">

    <button type="button" @click="new_date"> Generate New Date </button>

</div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    name: "NewDate",
    methods: {
        new_date: function() {
            this.$emit("new-date");
        }
    }
})
</script>