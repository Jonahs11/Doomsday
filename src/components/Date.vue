<template>
<div class="date">
 <h1> {{ written_date }} </h1>
 <ShowDayButton @clicked="show_day"> </ShowDayButton>
 <NewDateButton @new-date="create_date"> </NewDateButton>

</div>
</template>


<script lang="ts">
import { defineComponent, toHandlers } from "vue";
import ShowDayButton from "./ShowDayButton.vue";
import ShowDayButtonVue from "./ShowDayButton.vue";
import NewDateButton from "./NewDateButton.vue";


export default defineComponent( {
    name: "DateComp",
    props: {
        written_date: String
    },
    components: { ShowDayButton, NewDateButton },
    methods: {
        show_day: function() {
            console.log("button has been clicked");
            console.log(this.day);
        },
        create_date: function() {
            console.log("new date required!");
            const days_30 = new Set();
            days_30.add(4);
            days_30.add(6);
            days_30.add(9);
            days_30.add(11);

            this.month = this.randint(1, 12);
            this.year = this.randint(0, 99);
            let upper: number;
            if (this.month == 2) {
                if (this.year % 4 == 0) {
                    upper = 29;
                }
                else {
                    upper = 28;
                }
            }
            else if (days_30.has(this.month)) upper = 30;
            this.day = this.randint(1, 30);


            console.log(this.month.toString() + "/" + this.day.toString());

        },
        randint: function(lower: number, upper: number) {
            let rand: number = (Math.floor(Math.random() * (upper - lower + 1))) + lower;
            return rand;
        }
    },
    data() {
        return {
            day : 11,
            month : 8,
            year : 2000,
            date : ""
        }
    }
});

// let day: number = 11
// let month: number = 08
// let year: number = 2000


</script>