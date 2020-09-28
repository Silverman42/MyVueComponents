<template>
    <div>
        <label class="text-xs mb-1 flex w-full items-center justify-between" :for="id">
            <p class="text-sm">{{label}}</p>
            <div class="inline-block w-auto">
                <slot name="detail"></slot>
            </div>
        </label>
        <input ref="input" v-bind="$attrs" :value="value" @input="input($event)" class="appearance-none block w-full bg-primaryBg-200 text-black border border-primaryBg-400 rounded py-3 px-4 mb-1 leading-tight focus:outline-none focus:bg-primaryBg-300 focus:border-primary-400 h-12" :id="id" :type="type">
        <p class="text-red-500 text-xs italic" v-if="error !== null">{{error}}</p>
    </div>
</template>

<script>
export default {
    name: 'TextInput',
    inheritAttrs: false,
    props:{
        label:String,
        error:{
            type: String,
            default: null
        },
        value: [String,Number],
        type:{
            type: String,
            default: 'text'
        },
        hasMaxLength:{
            type:Boolean,
            default: false
        },
        maxLength:{
            type:Number,
            default: 0
        },
        hasMinLength:{
            type:Boolean,
            default: false
        },
        minLength:{
            type:Number,
            default: 0
        }
    },
    data(){
        return{
            id: "id"+ Math.floor(Math.random() * 50000000)  
        }
    },
    methods:{
        input(event){
            if(this.hasMinLength){
                return this.checkMinLength(event.target.value, this.minLength)
            }
            if(this.hasMaxLength){
                return this.checkMaxLength(event.target.value, this.maxLength)
            }
            return this.$emit('input',`${event.target.value}`)
        },
        checkMinLength(value, length){
            if(String(value).length >= length){
                this.$emit('input',`${value}`)
            }
            this.$forceUpdate()
        },
        checkMaxLength(value,length){
            if(String(value).length <= length){
                this.$emit('input',`${value}`)
            }
            this.$forceUpdate()
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