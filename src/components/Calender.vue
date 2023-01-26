<template>
    <section>
       <div class="container">
        <h2>Calender App With VueJs </h2>
       </div>
    </section> 
    <div class="container">
        <h2>{{ currentMonth }} 2023 </h2>
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
            <p class="text-center" v-for="date in 30" :key="date">{{ date }}</p>
        </div>
       </div>
    </section>
</template>

<script>
   export default {
    data(){
        return{
            days:["Sun", "Mond", "Wed", "Tue", "Thu", "Friday", "Sat"],
            // currentMonth:new Date().getMonth(),
            currentMonth:new Date(2023, 0,26).toLocaleString("default", {month:"long"})
        }
    }
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