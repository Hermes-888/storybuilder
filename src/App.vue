<template>
    <div id="app">
        <Board
            :courseId=courseId
            :title=title
            :moreInfo=courseInfo
            :itemHeaders=itemHeaders
            :itemData=items
        ></Board>
    </div>
</template>

<script>
import Board from './components/board.vue';

export default {
    name: 'App',
    components: {
        Board
    },
    data () {
        return {
            courseId: '012345',
            title: 'Name of course',
            courseInfo: 'Additional course information.',
            itemHeaders: ['ID','Cues','Screen Text', 'Text Action', 'Image Info', 'Image Action', 'Image'],
            items: [
                {
                    type: 'slide',
                    cellId: 'A',
                    slideTitle: 'Introduction to Logic',
                    slideInfo: 'modified from another course'
                },
                {
                    type: 'data',
                    cellId: '01-01',
                    fullText: 'All the text for this cell. All the text for this cell. All the text for this cell. ',
                    screenText: '<b>Qualifications for:</b> <br>html capable.',
                    textPresentation: 'tags? for Add, Replace, Replace All, Remove, ... and notes field',
                    imageDescription: 'Image with the <b>Qualifications for:</b> sign on the window.',
                    imagePresentation: 'Radio Group and text field?',
                    imageData: {
                        url: 'path to image file',
                        dataUrl: '320 x 180 thumbnail of image'
                    }
                },
                {
                    type: 'data',
                    cellId: '01-02',
                    fullText: 'All the text for this cell. All the text for this cell. All the text for this cell. ',
                    screenText: '<b>Qualifications for:</b> <br>html capable.',
                    textPresentation: 'tags? for Add, Replace, Replace All, Remove, ...',
                    imageDescription: 'Animate the smoke.',
                    imagePresentation: 'same tags?',
                    imageData: {
                        url: 'path to image file',
                        dataUrl: '320 x 180 thumbnail of image'
                    }
                },
                {
                    type: 'data',
                    cellId: '01-03',
                    fullText: 'All the text for this cell. All the text for this cell. All the text for this cell. ',
                    screenText: '<b>Qualifications for:</b> <br>html capable.',
                    textPresentation: 'tags? for Add, Replace, Replace All, Remove, ...',
                    imageDescription: 'white background with image in <u>bottom <b>left</b> corner</u>.',
                    imagePresentation: 'same tags?',
                    imageData: {
                        url: 'path to image file',
                        dataUrl: '320 x 180 thumbnail of image'
                    }
                },
                {
                    type: 'slide',
                    cellId: 'B',
                    slideTitle: 'Getting Started',
                    slideInfo: 'modified from another course'
                },
                {
                    type: 'data',
                    cellId: '01-01',
                    fullText: 'All the text for this cell. All the text for this cell. All the text for this cell. ',
                    screenText: '<b>Qualifications for:</b> <br>html capable.',
                    textPresentation: 'tags? for Add, Replace, Replace All, Remove, ... and notes field',
                    imageDescription: 'Image with the <b>Qualifications for:</b> sign on the window.',
                    imagePresentation: 'Radio Group and text field?',
                    imageData: {
                        url: 'path to image file',
                        dataUrl: '320 x 180 thumbnail of image'
                    }
                },
                {
                    type: 'data',
                    cellId: '01-03',
                    fullText: 'All the text for this cell. All the text for this cell. All the text for this cell. ',
                    screenText: '<b>Qualifications for:</b> <br>html capable.',
                    textPresentation: 'tags? for Add, Replace, Replace All, Remove, ...',
                    imageDescription: 'white background with image in <u>bottom <b>left</b> corner</u>.',
                    imagePresentation: 'same tags?',
                    imageData: {
                        url: 'path to image file',
                        dataUrl: '320 x 180 thumbnail of image'
                    }
                }
            ]
        }
    },
    mounted () {
        /**
         * load data from db to vuex store
         */
    },
    methods: {}
}
</script>

<style>
#app {
    font-family: 'Arimo', Helvetica, Arial, sans-serif;/* Segoe for Spanish? */
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-size: 18px;
    text-align: left;
    color: #000000;
}
</style>
