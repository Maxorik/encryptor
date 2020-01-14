<template>
    <div class="word-part">
        <textarea class="decryp-area" v-model="encr_txt" readonly></textarea>
    </div>
</template>

<script>
    export default {
        name: "ToDecryp",
        props:['encr_txt']
    }
</script>

<style scoped>
    textarea{
        width: 100%;
        height: 100%;
        margin: auto;
        resize: none;
        border: 1px solid lightblue;
    }
</style>