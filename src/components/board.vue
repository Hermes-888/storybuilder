<template>
    <div class="storyboard">
        <div class="board-container">
            <div class="board-info">
                ID: {{courseId}} | Course: {{title}}
                <div class="course-info">
                    {{moreInfo}}
                </div>
            </div>
            <!-- Buttons -->
            <div class="button-container">
                <button role="button"
                    @click="importFile"
                >Import</button>
                <button role="button"
                     @click="exportFile"
                >Export</button>
                <br>
                <button role="button"
                    @click="addSlide"
                >Add Slide</button>
                <button role="button"
                    @click="addRow"
                >Add Row</button>
            </div>
         </div>
        <hr>
        <div class="column-headers"
            v-html="columnHeader"   
        >
        </div>
        <div class="board-items">
            <Boardrow
                v-for="(rowColumns, index) in itemData"
                :key="index"
                :rowId="index"
                :cellData="rowColumns"
            />
        </div>
    </div>
</template>

<script>
import Boardrow from './boardrow.vue';

export default {
    /**
     * Course information row [ID, Name, Misc]
     * container for list of board-rows
     * Buttons: Import/Export xls? file
     * itemHeaders
     */
    name: 'board',
    components: {
        Boardrow
    },
    props: {
        courseId: {
            type: String,
            default: ''
        },
        title: {
            type: String,
            default: ''
        },
        moreInfo: {
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
    computed: {
        columnHeader: function() {
            //return this.itemHeaders.join(' -||- ');
            // let header = [];
            // this.itemHeaders.forEach(element => {
            //     let el = document.createElement('div');
            //     el.classList.add('header-item');
            //     el.textContent = element;
            //     header.push(el);
            // });// doesn't apply css
            let header = '';
            this.itemHeaders.forEach(element => {
                let el = '<div style="width:11%; text-align:center;">';
                // let el = '<div class="header-item">';// doesn't apply css
                el += element;
                el += '</div>';
                header += el;
                // console.log(el);
            });
            // console.log(header);
            return header;
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
        },
        addSlide: function() {
            console.log('Add a slide row');
        },
        addRow: function() {
            console.log('Add a data row');
        }
    },
    beforeDestroy() {
        this.editor.destroy();
    }
}
</script>

<style scoped>
    .storyboard {
        width: 98vw;
        height: 98vh;
        border: 1px solid grey;
    }
    .board-container {
        display: flex;
        padding: 10px;
        text-align: left;
        font-size: 22px;
        font-weight: 600;
        color:#333333;
        background-color: #e0e0e0;
        border: 1px solid #333333;
    }
    .board-info {
        width: 80%;
        float: left;
        border: 1px solid #333333;
    }
    .course-info {
        font-size: 18px;
        font-weight: 500;
        color:#333333;
        background-color: #ffffff;
    }
    .button-container {
        width: 20%;
        float: right;
        border: 1px solid #333333;
    }
    .column-headers {
        display: flex;
    }
    .header-item {
        width: 12%;
        text-align: center;
    }
    .board-items {
        height: 80vh;
        padding: 5px;
        overflow-x: auto;
        overflow-y: auto;
        border: 1px solid #333333;
    }
</style>
