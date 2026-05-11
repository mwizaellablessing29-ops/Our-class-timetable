<template>

<div>

<h1>Our Class Timetable</h1>

<select v-model="day">

<option disabled value="">Choose day</option>

<option v-for="d in days" :key="d">
{{ d }}
</option>

</select>

<div v-if="day">

<h2>{{ day }}</h2>

<table border="1">

<tr>
<th>Time</th>
<th>Activity</th>
</tr>

<tr v-for="(a,index) in timetable[day]" :key="index">

<td>{{ a.time }}</td>
<td>{{ a.activity }}</td>

</tr>

</table>

<br>

<input v-model="time" placeholder="time">

<input v-model="activity" placeholder="activity">

<button @click="addActivity">
Add
</button>

</div>

</div>

</template>

<script>

export default {

data() {

return {

day: "",

days: [
"Monday",
"Tuesday",
"Wednesday",
"Thursday",
"Friday"
],

time: "",
activity: "",

timetable: {

Monday: [
{
time: "8:00",
activity: "Math"
}
],

Tuesday: [
{
time: "9:00",
activity: "English"
}
],

Wednesday: [
{
time: "10:00",
activity: "game in view"
}
],

Thursday: [
{
time: "11:00",
activity: "javascript"
}
],

Friday: [
{
time: "1:00",
activity: "UI/UX"
}
]

}

}

},

methods: {

addActivity() {

this.timetable[this.day].push({

time: this.time,
activity: this.activity

})

this.time = ""
this.activity = ""

}

}

}

</script>

<style>

h1{
text-align:center;
}

table{
margin-top:20px;
}

</style>