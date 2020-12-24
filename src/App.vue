<template>
    <div id="app">
        <story-board
            :courseId="courseId"
            :courseTitle="courseTitle"
            :courseInfo="courseInfo"
            :itemHeaders="itemHeaders"
            :itemData="items"
        ></story-board>
    </div>
</template>

<script>
import StoryBoard from './components/StoryBoard.vue';

export default {
    name: 'App',
    components: {
        StoryBoard
    },
    data () {
        return {
            courseId: '012345',
            courseTitle: 'Name of course',
            courseInfo: 'Additional course information.',
            itemHeaders: ['ID','Cues','Screen Text', 'Text Action', 'Image Info', 'Action', 'Image'],
            items: [
                {
                    type: 'slide',
                    cellId: 'A',
                    fullText: 'Introduction to Logic',
                    screenText: 'modified from another course'
                    // it would be nice to store the data rows here
                    // or the data rows count, for Collapse Slide group
                },
                {
                    type: 'data',
                    cellId: '01-01',
                    fullText: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
                    screenText: '<b>Qualifications for:</b> <br>html capable.',
                    textPresentation: 'tags? for Add, Replace, Replace All, Remove, ... and notes field',
                    imageDescription: 'Image with the <b>Qualifications for:</b> sign on the window.',
                    imagePresentation: 'Radio Group and text field?',
                    imageData: {
                        url: 'images/sampleImage.png',
                        dataUrl: '320 x 180 thumbnail of image'
                    },
                    learningExtras: {}
                },
                {
                    type: 'data',
                    cellId: '01-02',
                    fullText: 'Lorem ipsum dolor sit amet, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.',
                    screenText: '<b>Qualifications for:</b> <br>html capable.',
                    textPresentation: 'tags? for Add, Replace, Replace All, Remove, ...',
                    imageDescription: 'Animate the smoke.',
                    imagePresentation: 'tags?',
                    imageData: {
                        url: '',
                        dataUrl: ''
                    },
                    learningExtras: {}
                },
                {
                    type: 'data',
                    cellId: '01-03',
                    fullText: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor ut labore et dolore magna aliqua.',
                    screenText: '<b>Qualifications for:</b> <br>html capable.',
                    textPresentation: 'tags? for Add, Replace, Replace All, Remove, ...',
                    imageDescription: 'white background with image in <u>bottom <b>left</b> corner</u>.',
                    imagePresentation: 'tags?',
                    imageData: {
                        url: 'images/sampleImg.jpg',
                        dataUrl: '320 x 180 thumbnail of image'
                    },
                    learningExtras: {}
                },
                {
                    type: 'slide',
                    cellId: 'B',
                    fullText: 'Getting Started',
                    screenText: 'modified from another course'
                },
                {
                    type: 'data',
                    cellId: '02-01',
                    fullText: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor ut labore et dolore magna aliqua.',
                    screenText: '<b>Qualifications for:</b> <br>html capable.',
                    textPresentation: 'tags? for Add, Replace, Replace All, Remove, ...',
                    imageDescription: 'white background with image in <u>bottom <b>left</b> corner</u>.',
                    imagePresentation: 'same tags?',
                    imageData: {
                       url: 'images/sampleImage.png',
                        dataUrl: '320 x 180 thumbnail of image'
                    },
                    learningExtras: {}
                },
                {
                    type: 'data',
                    cellId: '02-02',
                    fullText: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor ut labore et dolore magna aliqua.',
                    screenText: '<b>Qualifications for:</b> <br>html capable.',
                    textPresentation: 'tags? for Add, Replace, Replace All, Remove, ...',
                    imageDescription: 'white background with image in <u>bottom <b>left</b> corner</u>.',
                    imagePresentation: 'same tags?',
                    imageData: {
                       url: 'images/sampleImg.jpg',
                        dataUrl: '320 x 180 thumbnail of image'
                    },
                    learningExtras: {}
                },
                {
                    type: 'data',
                    cellId: '02-03',
                    fullText: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor ut labore et dolore magna aliqua.',
                    screenText: '<b>Qualifications for:</b> <br>html capable.',
                    textPresentation: 'tags? for Add, Replace, Replace All, Remove, ...',
                    imageDescription: 'white background with image in <u>bottom <b>left</b> corner</u>.',
                    imagePresentation: 'same tags?',
                    imageData: {
                       url: 'images/sampleImage.png',
                        dataUrl: '320 x 180 thumbnail of image'
                    },
                    learningExtras: {}
                },
                {
                    type: 'data',
                    cellId: '02-04',
                    fullText: '',
                    screenText: '',
                    textPresentation: '',
                    imageDescription: '',
                    imagePresentation: '',
                    imageData: {
                        url: '',
                        dataUrl: ''
                    },
                    learningExtras: {}
                }
            ]
        }
    },
    mounted () {
        /**
         * load data from db to vuex store
         */
    },
    //methods: {}
}
</script>

<style>
#app {
    font-family: 'Arimo', Helvetica, Arial, sans-serif;/* Segoe for Spanish? */
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-size: 16px;
    text-align: left;
    color: #000000;
}
</style>
