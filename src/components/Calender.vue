<template>
    <section>
       <div class="container">
        <h2>Calender App With VueJs </h2>
       </div>
    </section> 
    <div class="container">
        <h2>{{  currentMonthName }} 2023 </h2>
     <!-- {{ lastDateOfMonth }} -->
     {{ firstDay }}

    </div>
    <section>
       <div class='container'>
        <div class="days d-flex">
           <p class="text-center" v-for="(day,index) in days" :key="index">
            {{ day }}
            </p>
        </div> 
       </div>
    </section>
    <section>
       <div class="container">
        <div class="dates d-flex ">
            <p class="text-center" v-for="day in firstDay" :key="day"></p>
            <p class="text-center" v-for="date in lastDateOfMonth" :key="date">{{ date }}</p>
        </div>
       </div>
    </section>
    <section>
        <div class="container">
            <div class="d-flex justify-content-between">
                <button class="btn btn-primary" @click="prev"> Prev </button>
                <button class="btn btn-primary" @click="next"> Next </button>
            </div>
        </div>
    </section>
</template>

<script>
   export default {
    data(){
        return{
            days:["Sun", "Mon", "Wed", "Tue", "Thu", "Friday", "Sat"],
            currentMonthInNumber:new Date().getMonth(),
            currentYear:new Date().getFullYear(),
        }
    }, 
    computed:{
        currentMonthName(){
            return new Date(this.currentYear, this.currentMonthInNumber,26).toLocaleString("default", {month:"long"})
        },
        lastDateOfMonth(){
	        return new Date(this.currentYear, this.currentMonthInNumber+1, 0).getDate()
        },
        firstDay(){
	        return new Date(this.currentYear, this.currentMonthInNumber, 1).getDay() 
        }
    }, 
    methods:{
        prev(){
            console.log('prev');
        },
        next(){
         this.currentMonthInNumber++
        }
    },
   }
</script>

<style>
    .days p, .dates p {
        width: 14.28%;
    }
    .dates{
        flex-wrap: wrap;
    }
</style>