<template>
    <header>
        <h1>{{ title }}</h1>
        <Button @btn-click="$emit('toggleAddTask')" :text="showAddTask ? 'Close' : 'Add Task'" :color="showAddTask ? 'darkred' : 'green'"/>
    </header>
</template>

<script>
    import Button from './button'

    export default {

        name: 'Header',
        props: {
            title: String,
            showAddTask: Boolean,
        },
        components: {
            Button,
        },
    }
</script>

<style scoped>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
</style>