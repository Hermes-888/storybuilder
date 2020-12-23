<template>
    <div class="storyboard">
        <div class="board-container">
            <div class="board-info">
                ID: {{courseId}} | Course: {{courseTitle}}
                <div class="course-info">
                    {{courseInfo}}
                </div>
            </div>
            <!-- Buttons -->
            <div class="button-container">
                <button role="button"
                    @click="importFile"
                >Import
                </button>
                <button role="button"
                     @click="exportFile"
                >Export
                </button>
            </div>
         </div>
        <div class="board-items">
            <story-table
                :itemHeaders="itemHeaders"
                :itemData="itemData"
            />
        </div>
    </div>
</template>

<script>
import StoryTable from './StoryTable.vue';

export default {
    /**
     * Course information [courseId, courseTitle, courseInfo]
     * Buttons: Import/Export xls? file
     * 
     * itemHeaders and itemData are passed to StoryTable
     */
    name: 'StoryBoard',
    components: {
        StoryTable
    },
    props: {
        courseId: {
            type: String,
            default: ''
        },
        courseTitle: {
            type: String,
            default: ''
        },
        courseInfo: {
            type: String,
            default: ''
        },
        itemHeaders: {
            type: Array,
            default() { return [] }
        },
        itemData: {
            type: Array,
            default() { return [] }
        }
    },
    // data () {
    //     return {}
    // },
    // mounted () {
    // },
    methods: {
        importFile: function() {
             console.log('Import xls file');
        },
        exportFile: function() {
            console.log('Export xls file');
        }
    }
}
</script>

<style scoped>
    .storyboard {
        width: 98vw;
        height: 98vh;
        border: 1px solid #888888;
        background-color: #e0e0e0;
    }
    .board-container {
        display: flex;
        padding: 7px;
        text-align: left;
        font-size: 18px;
        font-weight: 600;
        color:#333333;
    }
    .board-info {
        width: 85%;
        padding: 5px;
        border: 1px solid #333333;
    }
    .course-info {
        font-size: 16px;
        font-weight: 500;
        color:#333333;
        background-color: #ffffff;
    }
    .button-container {
        display: flex;
        width: 15%;
        text-align: center;
    }
    .button-container button {
        margin: 0 auto;
        max-height: 24px;
    }
    .board-items {
        height: 80vh;
        padding: 5px;
        overflow-x: auto;
        overflow-y: auto;
        border-top: 1px solid #333333;
        border-bottom: 1px solid #333333;
    }
</style>
