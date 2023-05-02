<template>
   <h1>Job Details Page</h1>
   <p>The job id is: {{ $route.params.id }}</p>
   <p>The job id is: {{ id }}</p>
   <p>another route data: {{ data }}</p>
</template>

<script>
export default {
    props: ['data'],
    data() {
        return {
            id: this.$route.params.id
        }
    }
}
</script>

<style>

</style>