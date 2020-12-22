<template>
    <div class="board-row">
        <div v-if="cellData.type === 'slide'" class="slide-row">
            <div class="slide-id">{{cellData.cellId}}</div>
            <div class="slide-text">{{cellData.slideTitle}}</div>
            <div class="slide-text">{{cellData.slideInfo}}</div>
        </div>

        <div v-else class="data-row">
            <!-- Table? -->
            <div class="cell-id">{{cellData.cellId}}</div>
            <div class="cues">{{cellData.fullText}}</div>
            <!-- <Textcell
                :textData="cellData.screenText"
            /> -->
            <div class="screen-text"
                v-html="cellData.screenText"
            ></div>
            <div class="text-presentation">{{cellData.textPresentation}}</div>
            <div class="image-description"
                v-html="cellData.imageDescription"
            ></div>
            <div class="text-presentation">{{cellData.imagePresentation}}</div>
            <!-- single -->
            <Imagecell
                :imageData="cellData.imageData"
            />
        </div>
    </div>
</template>

<script>
// import Textcell from './textcell.vue';
import Imagecell from './imagecell.vue';

export default {
    /**
     * storyboard Row for cell columns
     * drag rows to change order
     * columns are resizeable
     * 
        type: 'slide / data',
        cellId: '01-01',
        fullText: 'All the text for this cell. All the text for this cell. All the text for this cell. ',
        screenText: '<b>Qualifications for:</b> <br>html capable.',
        textPresentation: 'text or tags? for Add, Replace, Replace All, Remove, ...',
        imageDescription: 'Image with the <b>Qualifications for:</b> sign on the window.',
        imagePresentation: 'same tags?',
        imageData: '{url, dataURL thumbnail 320 x 180}'
     */ 

    name: 'boardrow',
    components: {
        // Textcell, // html editor?
        Imagecell
    },
    props: {
        rowId: {
            type: Number,
            default: 0
        },
        rowType: {
            type: String,
            default: ''// Slide or Cell
        },
        cellData: {
            type: Object,
            default()  { return {} }
        }
    },
    // data () {
    //     return {}
    // },
    // mounted () {},
    methods: {}
}
</script>

<style scoped>
    .board-row {
        display: flex;
        padding: 5px;
        font-size: 16px;
        font-weight: 500;
        background-color: #e0e0e0;
        border: 1px solid #333333;
    }
    .slide-row {
        display: flex;
        width: 98%;
        padding: 5px 0;
        font-weight: 600;
        background-color: gold;
    }
    .slide-id {
        width: 5%;
        text-align: center;
        border: 1px solid #333333;
    }
    .slide-text {
        width: 30%;
        text-align: left;
        margin-left: 10px;
        border: 1px solid #333333;
    }
    .data-row {
        display: flex;
        width: 98%;
    }
    .cell-id {
        width: 70px;
        text-align: center;
        /* font-size: 18px; */
        font-weight: 600;
        border: 1px solid #333333;
        background-color: #ffffff;
    }
    .cues {
        width: 18%;
        margin-left: 5px;
        border: 1px solid #333333;
        background-color: #ffffff;
    }
    .screen-text {
        width: 12%;
        margin-left: 5px;
        border: 1px solid #333333;
        background-color: #ffffff;
    }
    .text-presentation {
        width: 12%;
        margin-left: 5px;
        border: 1px solid #333333;
        background-color: #ffffff;
    }
    .image-description {
        width: 18%;
        margin-left: 5px;
        border: 1px solid #333333;
        background-color: #ffffff;
    }
    .image-presentation {
        width: 12%;
        margin-left: 5px;
        border: 1px solid #333333;
        background-color: #ffffff;
    }
</style>
