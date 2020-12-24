<template>
    <div class="story-table">
        <v-table
            :data="itemData"
            selectionMode="single"
            selectedClass="selected-row"
            @selectionChanged="rowSelected"
        >
            <thead slot="head">
                <th v-for="(name, index) in itemHeaders"
                    :key="index"
                >
                    {{name}}
                </th>
            </thead>
            <tbody slot="body" slot-scope="{displayData}">
                <v-tr v-for="(row, index) in displayData" 
                    :key="index"
                    :row="row"
                >
                    <td v-if="row.type === 'slide'" class="slide-id cell-id">
                        {{ row.cellId }}
                    </td>
                    <td v-else class="cell-id">{{ row.cellId }}</td>

                    <td v-if="row.type === 'slide'" class="slide-id" colspan="2">
                        <strong>{{ row.fullText }}</strong>
                    </td>
                    <td v-else>{{ row.fullText }}</td>

                    <td v-if="row.type === 'slide'" class="slide-id" colspan="4">
                        {{ row.screenText }}
                        <button role="button" class="collapse-button"
                            @click="collapseSlide(index)"
                        >Collapse Slide</button>
                    </td>
                    <td v-else class="screen-text" v-html="row.screenText"/>

                    <td v-if="row.type === 'data'">{{ row.textPresentation }}</td>
                    <td v-if="row.type === 'data'" class="image-description" v-html="row.imageDescription"/>
                    <td v-if="row.type === 'data'">{{ row.imagePresentation }}</td>

                    <td v-if="row.type === 'data'">
                        <imagecell
                            :imageData="row.imageData"
                            @openModal="previewImage"
                            @click="setCurrentThumbnail"
                        />
                    </td>
                </v-tr>
            </tbody>
        </v-table>
        <!-- optional view of object data -->
        <div class="selected-output">
            <strong>Selected Data:</strong>
            <div v-if="selectedRows.length === 0" class="text-muted">No Rows Selected</div>
            <div v-for="(selected, index) in selectedRows"
                :key="index"
            >
                {{ selected }}
            </div>
        </div>
        <!-- overlay full image v-if="imagePath" -->
        <image-modal
            v-show="modalOpen"
            :imagePath="imagePath"
            @closeModal="modalOpen = !modalOpen"
        />
    </div>
</template>

<script>
import Imagecell from './imagecell.vue';
import ImageModal from './ImageModal.vue';

export default {
    /**
     * Storyboard Table
     * 
     * https://github.com/tochoromero/vuejs-smart-table
     * https://github.com/tochoromero/vuejs-smart-table/tree/master/docs
     * 
     * type: 'data', // or 'slide' to display Slide ID, title and info row
        cellId: '01-01',
        fullText: 'All the text for this cell. All the text for this cell. All the text for this cell. ',
        screenText: '<b>Qualifications for:</b> <br>html capable.',
        textPresentation: 'tags? for Add, Replace, Replace All, Remove, ... and notes field',
        imageDescription: 'Image with the <b>Qualifications for:</b> sign on the window.',
        imagePresentation: 'Radio Group and text field?',
        imageData: {
            url: 'path to image file',
            dataUri: '320 x 180 thumbnail of image'
        },
        learningExtras: {}
     */
    name: "StoryTable",
    components: {
        Imagecell,
        ImageModal
    },
    props: {
        itemHeaders: {
            type: Array,
            default() { return [] }
        },
        itemData: {
            type: Array,
            default() { return [] }
        }
    },
    data () {
        return {
            selectedRows: [],// single
            modalOpen: false,// thumbnail image full size, w/stats panel?
            imagePath: null,// url to full image
        }
    },
    mounted () {
        this.$nextTick(function () {
            // console.log('headers:', this.itemHeaders);
            // if (this.itemData[0].imageData) {
            //     this.imageData = this.itemData[0].imageData;// setCurrentThumbnail
            // }
        });
    },
    methods: {
        rowSelected: function(rows) {
            this.selectedRows = rows;
            // console.log('selectionChanged:', this.selectedRows.length, this.selectedRows);
            // console.log('headers:', this.itemHeaders);
        },
        collapseSlide: function(index) {
            console.log('collapse row', index, this.itemData[index]);
        },

        /**
         * set from ImageCell clicked
         */
        setCurrentThumbnail: function(cell) {
            console.log('setCurrentThumbnail:', cell);
        },

        /**
         * Preview image in a modal with stats panel?
         * click anywhere to close the modal
         */
        previewImage: function(imagePath) {
            // console.log('preview image in modal', imagePath);
            this.imagePath = imagePath;
            this.modalOpen = true;
        },
    }
}
</script>

<style scoped>
    .story-table {
        width: 96vw;
        overflow-x: auto;
        overflow-y: auto;
        font-size: 16px;
        background-color: #ffffff;
    }
    th {
        text-align: center;
        padding: 5px;
        border: 1px solid #333333;
    }
    td {
        vertical-align: top;
        padding: 5px;
        border: 1px solid #333333;
    }
    .selected-row {
        background-color: #d3d3d3;
    }
    .selected-row td {
        border: 2px solid #000000;
    }
    .selected-output {
        position: absolute;
        bottom: 2%;
        width: 96vw;
        padding: 5px;
        border: 1px solid #333333;
        background-color: #ffffff;
    }
    .text-muted {
        color: #888888;
    }
    .slide-id {
        background-color:#fdbe35;
    }
    .slide-id button {
        float: right;
    }
    .cell-id {
        width: 50px;
        text-align: center;
        font-weight: bold;
    }
    .cues {
        width: 18%;
    }
    .screen-text {
        width: 15%;
    }
    .text-presentation {
        width: 12%;
    }
    .image-description {
        width: 15%;
    }
    .image-presentation {
        width: 12%;
    }
</style>
