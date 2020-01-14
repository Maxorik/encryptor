<template>
    <div class="word-part">
        <textarea class="main-area" placeholder="введите или вставьте текст" v-model="enc_data" v-on:input="$emit('change_text', enc_data)"></textarea>
    </div>
</template>

<script>
    export default {
        name: "ToEncryp",
        props:['info'],
        data(){
            return{
                enc_data:this.info
            }
        }
    }
</script>

<style>
    .word-part{
        width:49%;
        border: 1px solid lightblue;
        margin: 10px;
        min-height: 400px;
        padding: 2px;
    }

    .main-area{
        width: 100%;
        height: 100%;
        margin: auto;
        resize: none;
        border: 1px solid lightblue;
    }
</style>