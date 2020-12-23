<template>
    <div class="image-cell">
        <div v-if="imageData.url">
            <img class="image-display" :src="imageData.url" />
        </div>
        
        <div class="image-buttons">
            <button role="button"
                @click="uploadImage"
            >
                Upload
            </button>
            <button role="button"
                 v-if="imageData.url"
                @click="removeImage"
            >
                Remove
            </button>
            <button role="button"
                v-if="imageData.url"
                @click="downloadImage"
            >
                Download
            </button>
        </div>
    </div>
</template>

<script>
/**
 * display image thumbnail
 * buttons: Upload/Replace Image, Remove Image, Download Image file
 * 
 * imageData: {
        url: 'path to image file',
        dataUri: '320 x 180 thumbnail of image'
    }
*/
export default {
    name: 'imagecell',
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
        /**
         * open file browser and upload to Filepond
         * update data
         */
        uploadImage: function() {
             console.log('Upload clicked:', this.imageData);
        },

        /**
         * remove from table and update data
         */
        removeImage: function() {
            if (this.imageData.url) {
                console.log('Remove image from data');
                this.imageData.url = '';
                // emit event to update data
            }
        },

        /**
         * download image file
         */
        downloadImage: function() {
            console.log('Download: ', this.imageData.url);
        },

        /**
         * convert image for db? unused
         */
        convertImageData: function() {
            console.log('convert to dataUri');
        }
    }
}
</script>

<style scoped>
    .image-cell {
        position: relative;
        min-width: 250px;
        min-height: 20px;
    }
    .image-buttons {
        display: flex;
        position: absolute;
        bottom: 2%;
        left: 2%;
        width: 96%;
    }
    .image-buttons button {
        margin: 0 auto;
    }
    .image-display {
        max-width: 320px;
        max-height: 180px;
    }
</style>
