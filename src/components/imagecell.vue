<template>
    <div class="image-cell">
        <div class="image-buttons">
            <button role="button"
                @click="uploadImage"
            >
                Upload Image
            </button>
            <div class="spacer"></div>
            <button role="button"
                @click="downloadImage"
            >
                Download Image
            </button>
        </div>
    </div>
</template>

<script>
export default {
    /**
     * display thumbnail of assigned image
     * buttons: Upload/Replace Image & Download Image file
     */
    name: 'imagecell',
    // components: {},
    props: {
        imageData: {
            type: Object,
            default()  { return {} }
        }
    },
    // data () {
    //     return {}
    // },
    mounted () {},
    methods: {
        uploadImage: function() {
             console.log('Upload clicked');
        },
        downloadImage: function() {
            console.log('Download: ', this.imageData.url);
        }
    }
}
</script>

<style scoped>
    .image-cell {
        position: relative;
        width: 320px;
        height: 180px;
        margin-left: 5px;
        background-color: darkslateblue;
        border: 2px solid #333333;
    }
    .image-buttons {
        display: flex;
        width: 90%;
        margin: 5px auto;
    }
    .spacer {
        width: 10%;
    }
</style>
