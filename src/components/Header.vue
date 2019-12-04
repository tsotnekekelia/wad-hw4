<template>
    <div class="container">
        <div class="date">
            <h1>{{day}}</h1>
            <div>
                <h4 class="strong">{{month | uppercase | abbreviate }}</h4>
                <h4>{{year}}</h4>
            </div>
        </div>
        <h4>{{weekday | uppercase}}</h4>
    </div>
</template>

<script>
    export default {
        name: "Header",
        data: () => {
            return {
                today: new Date()
            }
        },
        filters: {
            uppercase: function(value){
                return value.toUpperCase()
            },
            abbreviate: function(value){
                return value.slice(0,3)
            }
        },
        computed: {
            day: function() {
                let date = this.today.getDate();

                return date < 10 ?  `0${date}` : date
            },
            month: function() {
                let months = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October',	'November', 'December'];

                return months[this.today.getMonth()]
            },
            year: function() {
                return this.today.getFullYear()
            },
            weekday: function() {
                let weekdays = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'];

                return weekdays[this.today.getDay()]
            },
        }
    }
</script>

<style scoped>
    .container {
        display: flex;
        align-items: center;
        justify-content: space-between;
        color: #5c5e6b;
    }
    .date {
        display: flex;
        align-items: center;
    }
    h1{
        margin: 0;
        font-size: 42px;
    }
    h4{
        margin: 0;
    }
</style>