<template>
    <section>
       <div class="container">
        <h1 class="text-success"><b>Calender Project By VueJs-3</b> </h1>
       </div>
    </section> 
    <div class="container">
        <h2 class="my-4"> <button class="btn bg-success text-white">{{  currentMonthName }} </button> <b>{{ currentYear }} </b></h2>
     <!-- {{ lastDateOfMonth }} -->
     <!-- {{ firstDay }} -->
     <!-- {{ todayDate()}} -->

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
            <p class="text-center" v-for="date in lastDateOfMonth" :key="date" :class="todayDate(date)">{{ date }}</p>
            <!-- <p class="text-center" v-for="date in lastDateOfMonth" :key="date" :class="date===todayDate() ? 'text-danger' : '' ">{{ date }}</p> -->
            
        </div>
       </div>
    </section>
    <section>
        <div class="container">
            <div class="d-flex justify-content-between">
                <button class="btn btn-success" @click="prev"> Prev </button>
                <button class="btn btn-success" @click="next"> Next </button>
            </div>
        </div>
    </section>
</template>

<script>
   export default {
    data(){
        return{
            days:["Sun", "Mon",  "Tue", "Wed", "Thu", "Friday", "Sat"],
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
        },
     
    }, 
    methods:{
       
        next(){
            if(this.currentMonthInNumber === 11){
                this.currentYear++
                this.currentMonthInNumber = 0
            }else{
                this.currentMonthInNumber++
            }       
        },
        prev(){
            if(this.currentMonthInNumber === 0){
                this.currentYear--
                this.currentMonthInNumber = 11
            }else{
                this.currentMonthInNumber--
            }  
        },
        todayDate(date){
                let calenderDate = new Date(this.currentYear, this.currentMonthInNumber,date).
                toDateString()

                let today = new Date().toDateString()
                // console.log(calenderDate === today) 
                return calenderDate === today ? 'text-white bg-success' : ''
        },
        
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