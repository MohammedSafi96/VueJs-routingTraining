<template>
    <h1>Jobs</h1>
    <div v-for="job in jobs" :key="job.id" class="job">
        <router-link :to="{ name: 'JobDetailsView', params: { id: job.id, data: `${job.details} ${job.id}` } }">
            <h2>{{ job.title }}</h2>
        </router-link>
    </div>
    <br>
    <div v-if="WeatherForecast && WeatherForecast.length">
        <div v-for="weather in WeatherForecast" :key="weather.date" class="job">
            <h4>Date: {{ weather.date }}</h4>
            <h4>TemperatureC: {{ weather.temperatureC }}</h4>
            <h4>TemperatureF: {{ weather.temperatureF }}</h4>
            <h4>Summary: {{ weather.summary }}</h4>
            <br>
        </div>
    </div>
    <div v-else>
        <p>loading weathers...</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            jobs: [
                { title: 'Ninja UX Designer', id: 1, details: 'lorem' },
                { title: 'Ninja Web Developer', id: 2, details: 'lorem' },
                { title: 'Ninja Vue Developer', id: 3, details: 'lorem' },
            ],
            WeatherForecast: null
        }
    },
    mounted() {
        // POST data to BE
        fetch('https://localhost:7279/WeatherForecast', {
            method: 'POST',
            headers: { "Content-type": "application/json; charset=UTF-8"},
            body: JSON.stringify({'Date': '2023-05-04', 'TemperatureC': 12, 'Summary': '12345677889' }),
        })
        .then((b) => b.json())
            .then(data =>  alert(data))
            .catch(err => console.log(err.message))

         //fetch data from BE
        fetch('https://localhost:7279/WeatherForecast')
            .then((b) => b.json())
            .then(data => this.WeatherForecast = data)
            .catch(err => console.log(err.message))


    }
}
</script>

<style>
.job h2,
h4 {
    background: #f4f4f4;
    padding: 20px;
    border-radius: 10px;
    margin: 10px auto;
    max-width: 600px;
    cursor: pointer;
    color: #444;
}

.job h2:hover,
h4:hover {
    background: #ddd;
}

.job a {
    text-decoration: none;
}

.job h4 {
    background: burlywood
}</style>