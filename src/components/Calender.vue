<template>
    <section>
       <div class="container">
        <h2>Calender App With VueJs </h2>
       </div>
    </section> 
    <section>
       <div class='container'>
        <div class="days d-flex">
           <p class="text-center" v-for="(day,index) in days" :key="index">
            {{ day }}
            </p>
        </div> 
       </div>
    </section>
</template>

<script>
   export default {
    data(){
        return{
            days:["Sun", "Mond", "Wed", "Tue", "Thu", "Friday", "Sat"]
        }
    }
   }
</script>

<style>
    .days p {
        width: 14.28%;
    }
</style>