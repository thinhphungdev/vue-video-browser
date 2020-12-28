<template>
    <div>
        <input placeholder="Type the video name here to search" @input="onIput" />
    </div>
</template>

<script>
export default {
    name: "SearchBar",
    methods: {
        onIput: function(event) {
            this.$emit('termChange', event.target.value)
        }
    }
}
</script>

<style scoped>
    input {
        width: 75%;
    }
    div {
        text-align: center;
        margin: 20px;
    }
</style>