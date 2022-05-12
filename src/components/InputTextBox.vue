<template>
    <div id="inputTextBox">
        <textarea :model="message"
                  placeholder="Input Text Box"
                  rows="10"
                  cols="40"></textarea>
    </div>
</template>

<script>
    export default {
        name: 'InputTextBox',
        components: {},
        props: {
            inputText: String
        }
    }
</script>

<style scoped>
    textarea {
        border: 2px solid #888;
        resize: none;
    }
</style>