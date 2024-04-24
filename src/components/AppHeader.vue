<template>
    <header>
        <h1>{{title}}</h1>
        <AppButton :toggleForm="toggleForm" @btn-click="$emit('show-add-form')" :buttonText="!toggleForm ? 'Add Task' : 'Close'" :buttonColor="toggleForm ? 'red' : 'green'" />
    </header>
</template>

<script>
import AppButton from './AppButton.vue';

export default {
    name: "AppHeader",
    components: {
        AppButton,
    },
    props: {
        title: String,
        toggleForm: Boolean
    },
    $emits: ['show-add-form']
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
