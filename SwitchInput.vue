<template>
    <label class="flex justify-between w-auto" :for="`switch-${id}`">
        <div class="flex-grow pr-3">
            <p>{{label}}</p>
            <small class="text-red-500 text-xs italic" v-if="error !== null">{{error}}</small>
        </div>
        <div class="inline-block w-auto">
            <input type="checkbox" v-model="checked" hidden :id="`switch-${id}`">
            <div class="switch" tabindex="-1">
                <span></span>
            </div>
        </div>
    </label>
</template>

<script>
    export default {
        name:"SwitchInput",
        props:{
            title:String,
            value:{
                type: [Boolean,Number],
                default: false
            },
            name:String,
            label:String,
            error:{
                type: String,
                default: null
            },
        },
        data(){
            return{
                id: "id"+ Math.floor(Math.random() * 50000000),
                checked: this.value,
            }
        },
        watch:{
            checked(newVal,oldVal){
                return this.$emit('input',newVal)
            }
        }
    }
</script>

<style scoped>
    .switch{
        border-radius: 15px;
        @apply flex items-center outline-none bg-primaryBg-200 border border-primaryBg-400 p-1 w-12 cursor-pointer;
        @apply transition-all duration-300 ease-in-out;
    }
    .switch:hover,.switch:focus{
        @apply border-primary-500
    }
    .switch>span{
        @apply inline-block rounded-full shadow-lg w-5 h-5 bg-white border border-primaryBg-400;
        @apply transition-all duration-300 ease-in-out;
    }

    input[type=checkbox]:checked~.switch{
        @apply bg-primary-500;
    }
    input[type=checkbox]:checked~.switch>span{
        @apply transform translate-x-full border-primary-500;
    }
</style>
