<template>
<div class="date">
 <h1> {{ date }}
 </h1>
 <ShowDayButton @clicked="show_day"> </ShowDayButton>
 <div class="flex"> 
     <AnswerButtonVue day=0 @clicked="check_answer"></AnswerButtonVue>
     <AnswerButtonVue day=1 @clicked="check_answer"></AnswerButtonVue>
     <AnswerButtonVue day=2 @clicked="check_answer"></AnswerButtonVue>
     <AnswerButtonVue day=3 @clicked="check_answer"></AnswerButtonVue>
     <AnswerButtonVue day=4 @clicked="check_answer"></AnswerButtonVue>
     <AnswerButtonVue day=5 @clicked="check_answer"></AnswerButtonVue>
     <AnswerButtonVue day=6 @clicked="check_answer"></AnswerButtonVue>

 </div>
 <NewDateButton @new-date="create_date"> </NewDateButton>

</div>
</template>


<script lang="ts">
import { defineComponent, toHandlers } from "vue";
import ShowDayButton from "./ShowDayButton.vue";
import ShowDayButtonVue from "./ShowDayButton.vue";
import NewDateButton from "./NewDateButton.vue";
import AnswerButtonVue from "./AnswerButton.vue";


export default defineComponent( {
    name: "DateComp",
    props: {
        written_date: String
    },
    components: { ShowDayButton, NewDateButton, AnswerButtonVue},
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

            this.date = this.month.toString() + "/" + this.day.toString() + "/" + this.year.toString();
        },
        randint: function(lower: number, upper: number) {
            let rand: number = (Math.floor(Math.random() * (upper - lower + 1))) + lower;
            return rand;
        },
        check_answer: function(day: number) {
            console.log(day);
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

</script>


<style scoped>
.flex {
    display: flex
}


</style>