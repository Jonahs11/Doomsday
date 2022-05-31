<template>
<div class="date">
 <h1> {{ date }}
 </h1>
 <!-- <ShowDayButton @clicked="show_day"> </ShowDayButton> -->
 <!-- <div class="flex"> 
    <AnswerButtonVue day=0 @clicked="check_answer"></AnswerButtonVue>
     <AnswerButtonVue day=1 @clicked="check_answer"></AnswerButtonVue>
     <AnswerButtonVue day=2 @clicked="check_answer"></AnswerButtonVue>
     <AnswerButtonVue day=3 @clicked="check_answer"></AnswerButtonVue>
     <AnswerButtonVue day=4 @clicked="check_answer"></AnswerButtonVue>
     <AnswerButtonVue day=5 @clicked="check_answer"></AnswerButtonVue>
     <AnswerButtonVue day=6 @clicked="check_answer"></AnswerButtonVue>


 </div> -->

<div class="flex-parent jc-center">

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
    components: { 
        // ShowDayButton, 
        NewDateButton, AnswerButtonVue},
    methods: {
        show_day: function() {
            // console.log("button has been clicked");

            let days_30 = new Set();
            days_30.add(3);
            days_30.add(5);
            days_30.add(8);
            days_30.add(10);

            let doom = this.get_doomsday(this.year);

            let leap = false;
            let day_1: number;
            let day_num  = 0;
            if (this.year % 4 == 0) {
                leap = true;
            }

            if (leap) {
                day_1 = (doom + 4) % 7;
            }
            else {
                day_1 = (doom + 5) % 7;
            }


            for (let i = 0; i < this.month - 1; i++) {
                if (i == 1) {
                    if (leap) day_num = day_num + 29;
                    else day_num = day_num + 28;
                }
                else {
                if (days_30.has(i)) day_num = day_num + 30;
                else day_num = day_num + 31;
                }
            }
            day_num = (day_num + this.day);
            day_num = day_num - 1;
            day_num = day_num % 7;

            let dow = (day_1 + day_num) % 7;
            return dow;


        },
        get_doomsday: function(year: number) {

            let x = Math.floor(this.year / 12);
            let y = Math.floor(this.year - (x * 12));
            let z = Math.floor((y / 4));
            let dooms = 2;

            let doomsday = (x + y + z + dooms) % 7;

            return doomsday;

            
        },  
        create_date: function() {
            console.log("new date required!");
            let days_30 = new Set();
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
            let correct = this.show_day();

            if (day == correct) this.correct_answer();
            else this.incorrect_answer();

        },

        correct_answer: function() {
            console.log("Correct answer chosen");
        },

        incorrect_answer: function() {
            console.log("Incorrect answer chosen");
            
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

.center {
    border: 5px solid;
    text-align: center;
}

.flex-parent {
    display: flex;
}

.jc-center {
    justify-content: center;
}

</style>