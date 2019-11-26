<template>

    <panel-item :field="field">

        <file-pond-wrapper
                slot="value"
                :disabled="true"
                :allow-image-preview="!field.multiple"
                :limit="field.value.length"
                :field="field"
                v-if="!pdf && !word && !excel"
                />

        <file-pond-wrapper2
                slot="value"
                :disabled="true"
                :allow-image-preview="!field.multiple"
                :limit="field.value.length"
                :field="field"
                v-if="pdf"
        />

        <file-pond-wrapper3
                slot="value"
                :disabled="true"
                :allow-image-preview="!field.multiple"
                :limit="field.value.length"
                :field="field"
                v-if="word"
        />

        <file-pond-wrapper4
                slot="value"
                :disabled="true"
                :allow-image-preview="!field.multiple"
                :limit="field.value.length"
                :field="field"
                v-if="excel"
        />


    </panel-item>


</template>

<script>

    import FilePondWrapper from './FilePondWrapper'
    import FilePondWrapper2 from './FilePondWrapper2'
    import FilePondWrapper3 from './FilePondWrapper3'
    import FilePondWrapper4 from './FilePondWrapper4'

    export default {
        components: {FilePondWrapper,FilePondWrapper2,FilePondWrapper3,FilePondWrapper4},
        props: ['resource', 'resourceName', 'resourceId', 'field'],
        data: function () {
            return {
                pdf: false,
                word: false,
                excel: false
            }
        },
        mounted() {
            var file = this.field.thumbnails[0];
            var ext = file.substr(file.lastIndexOf('.') + 1);
            if (ext == 'pdf') {
                this.pdf = true;
            }
            else if (ext == 'doc' || ext == 'docx'){
                this.word = true;
            }
            else if (ext == 'xl' || ext == 'xla' || ext == 'xls' || ext == 'xlsx'){
                this.excel = true;
            }
        }
    }
</script>
