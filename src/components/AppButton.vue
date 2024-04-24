<template>
    <button @click="onClick()" :style="{background: buttonColor}" class="btn">{{buttonText}}</button>
</template>

<script>
export default {
    name: "AppButton",
    props: {
        buttonText: String,
        buttonColor: String,
        toggleForm: Boolean
    },
    methods: {
        onClick() {
            this.$emit('btn-click')
            console.log("toggleForm", this.toggleForm);
        }
    },
}
</script>   