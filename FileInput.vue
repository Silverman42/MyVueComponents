<template>
    <div>
        <label class="text-xs mb-1 flex items-center justify-between">
            <p>{{label}}</p>
            <div class="inline-block w-auto">
                <slot name="detail"></slot>
            </div>
        </label>
        <label :for="id" class="container"
            :class="{'cursor-not-allowed':disabled == true, 'cursor-pointer' : disabled == false }">
            <input type="file" v-bind="$attrs" @input="input($event)" :id="id" class="hidden">
            <div class="flex items-center">
                <span v-if="fileCount > 0" class="file-counter">{{fileCount}}</span>
                {{fileName|truncateFileName}}
            </div>
            <div class="action">Browse</div>
        </label>
        <p class="text-red-500 text-xs italic" v-if="error !== null">{{error}}</p>
    </div>
</template>

<script>
    export default {
        name: 'FileInput',
        inheritAttrs: false,
        props: {
            disabled: Boolean,
            label: String,
            error: {
                type: String,
                default: null
            },
            value: String,
            type: {
                type: String,
                default: 'text'
            }
        },
        data() {
            return {
                id: "id" + Math.floor(Math.random() * 50000000),
                fileName: 'Choose File..',
                fileCount: 0
            }
        },
        filters: {
            truncateFileName(name) {
                if (name.length > 19) {
                    return (name.substring(0, 18)) + '..'
                }
                return name
            }
        },
        methods: {
            input(event) {
                this.changeFileName(event.target.files)
                this.getFileCount(event.target.files)
                return this.$emit('input', event.target.files[0])
            },
            changeFileName(file) {
                this.fileName = file[0].name
            },
            getFileCount(file) {
                this.fileCount = parseInt(file.length)
            },
            focus() {
                this.$refs.input.focus()
            },
            select() {
                this.$refs.input.select()
            },
            setSelectionRange(start, end) {
                this.$refs.input.setSelectionRange(start, end)
            }
        }
    }

</script>

<style scoped>
    .container {
        box-sizing: border-box;
        @apply flex h-12 w-full rounded border bg-primaryBg-100 items-center justify-between py-3 px-3 mb-1;
    }

    .file-counter {
        @apply inline-block w-auto bg-gray-400 rounded-lg px-2 py-1 text-xs text-white mr-1;
    }

    .action {
        @apply py-1 px-2 bg-gray-400 rounded text-sm font-bold inline-block w-auto text-white
    }

    .container:hover .action {
        @apply bg-gray-500
    }

</style>
