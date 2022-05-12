<template>
    <span>Message is: {{ message }}</span>
    <div id="inputTextBox">
        <textarea v-model="message"
                  placeholder="Input Text Box"
                  rows="10"
                  cols="40"></textarea>
    </div>
    <button @click="fetchAudio()">Get TTS</button>

    <audio id="audio" controls>
        <source id="audioSource" type="audio/wav" :src="sourceURL" />
    </audio>
</template>

<script>
    export default {
        name: 'InputTextBox',
        components: {},
        data() {
            return {
                message: 'Input Text Box',
                sourceURL: null
            }
        },
        methods: {
            async fetchAudio() {
                let audioRequest = await fetch('https://api.streamelements.com/kappa/v2/speech?voice=Brian&text=' + encodeURIComponent(this.message.trim()));
                console.log(audioRequest)
                let audioData = await audioRequest.blob();
                let blobURL = URL.createObjectURL(audioData);
                this.sourceURL = blobURL;

                document.getElementById('audio').load();
            }
        }
    }
</script>

<style scoped>
    textarea {
        border: 2px solid #888;
        resize: none;
    }
</style>