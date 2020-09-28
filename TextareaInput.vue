<template>
    <div>
        <label class="block text-xs mb-1 flex justify-between" :for="id">
            <p>{{label}}</p>
            <div class="inline-block w-auto">
                <slot name="detail"></slot>
            </div>
        </label>
        <textarea ref="input" v-bind="$attrs" :value="value" @input="input($event)" class="resize-y appearance-none block w-full bg-primaryBg-200 text-black border border-primaryBg-400 rounded py-3 px-4 mb-1 leading-tight focus:outline-none focus:bg-primaryBg-300 focus:border-primary-500" :id="id">
        </textarea>
        <p class="text-red-500 text-xs italic" v-if="error !== null">{{error}}</p>
    </div>
</template>

<script>
export default {
    name: 'TextareaInput',
    inheritAttrs: false,
    props:{
        label:String,
        error:{
            type: String,
            default: null
        },
        value: String,
    },
    data(){
        return{
            id: "id"+ Math.floor(Math.random() * 50000000)  
        }
    },
    methods:{
        input(event){
            return this.$emit('input',event.target.value)
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

<style>

</style>