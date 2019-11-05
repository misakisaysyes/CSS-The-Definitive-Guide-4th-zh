<template>
    <div>
        <iframe 
            :src="frameSrc" 
            ref="frame"
            :width="frameWidth"
            :height="frameHeight"
            seamless 
            frameborder=0 
            scrolling="no"
            @load="getFix"
        ></iframe>
        <p>
            <slot name="original"></slot>
        </p>
        <p>
            <slot name="translation"></slot>
        </p>
    </div>
</template>

<script>
export default {
    name: 'Frame',
    data() {
        return {
            frameWidth: '',
            frameHeight: ''
        }
    },
    props: {
        url: {
            type: String,
            default: ''
        }
    },
    computed: {
        frameSrc() {
            return `./frame/${this.url}.html`
        }
    },
    methods: {
        getFix() {
            this.frameHeight =  this.$refs['frame'].contentWindow.document.body.scrollHeight 
            this.frameWidth =  this.$refs['frame'].contentWindow.document.body.scrollWidth
            this.$refs['frame'].contentWindow.document.body.style.margin="0"
        }    
    },
}
</script>

<style>
    p {
        text-align: center;
        margin: .5em;
    }
</style>