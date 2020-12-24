<template>
    <div class="image-cell">
        <div v-if="imageData.url">
            <img class="image-display"
                :src="imageData.url"
                @click="previewImage"
            />
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
        dataUrl: 'base64 of 320 x 180 thumbnail'
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
    data () {
        return {
            debug: false,// convertImageData to dataUrl
            dataUrl: null// maybe NOT see convertImageData
        }
    },
    mounted () {
        // convert for cell
        this.$nextTick(function () {
            // need to load the image
            if (this. debug && this.imageData.url) {
                // console.log('convert:', this.imageData.url);
                const me = this;
                const img = document.createElement('img');
                img.crossOrigin = 'anonymous';
                img.src = this.imageData.url;

                img.addEventListener('load', function(event) {
                    //console.log(event);
                    this.removeEventListener('load',function() {});// once
                    me.convertImageData(event.currentTarget);
                });
            }
        });
    },
    methods: {
        /**
         * open file browser and upload to Filepond
         * create base64 of a 320 x 180 thumbnail image
         * use the base64 for the thumbnail, instead of :src="imageData.url"
         * update imageData.dataUrl
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
         * Preview image in a modal
         * emit image url to StoryTable
         */
        previewImage: function() {
            // console.log('emit to StoryTable:', this.imageData.url);
            this.$emit('openModal', this.imageData.url);
        },

        /**
         * convert image for db? it's really large
         * create base64 of a 320 x 180 thumbnail image
         * update imageData.dataUrl
         */
        convertImageData: function(img) {
            console.log('convert img', img);
            // document.body.appendChild(img);

            this.dataUrl = this.imgToBase64(img);
            this.imageData.dataUrl = this.dataUrl;
            console.log('converted:', this.dataUrl);
            // const img2 = document.createElement('img');
            // img2.src = this.dataUrl;
            // document.body.appendChild(img2);
        },// combine functions?
        imgToBase64: function(img) {
            const canvas = document.createElement('canvas');
            const ctx = canvas.getContext('2d');

            canvas.width = 320;
            canvas.height = 180;// large dataUrl

            ctx.drawImage(img, 0, 0, img.width, img.height,// source rectangle
                   0, 0, canvas.width, canvas.height);// destination rectangle

            // resize canvas to 320 x 180
            // canvas.width = 320;// breaks image
            // canvas.height = 180;// smaller dataUrl
            // document.body.appendChild(canvas);

            // img.width = 320;
            // img.height = 180;
            // document.body.appendChild(img);// looks good

            return canvas.toDataURL();//'image/jpeg'
        },
        thumbnailify: function(base64Image, targetSize, callback) {
            var img = new Image();
            let targetWidth = 320;
            let targetHeight = 180;

            img.onload = function() {
                var width = img.width,
                    height = img.height,
                    canvas = document.createElement('canvas'),
                    ctx = canvas.getContext("2d");

                canvas.width = targetWidth
                canvas.height = targetHeight;

                ctx.drawImage(
                    img,
                    width > height ? (width - height) / 2 : 0,
                    height > width ? (height - width) / 2 : 0,
                    width > height ? height : width,
                    width > height ? height : width,
                    0, 0,
                    targetWidth, targetHeight
                );

                callback(canvas.toDataURL());
            };

            img.src = base64Image;
            },
            /*
            var sourceImage = document.getElementById("source-image"),
                    thumbnail = document.getElementById("thumbnail");

            thumbnailify(sourceImage.src, 100, function(base64Thumbnail) {
                thumbnail.src = base64Thumbnail;
            });
            */
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
