<template>
    <label class="flex justify-between" :class="[uiLayouts[layout]]" :for="`switch-${id}`">
        <div class="flex-grow pr-3">
            <slot/>
        </div>
        <div class="inline-block w-auto">
            <input v-if="value" :value="value" type="checkbox" v-model="checked" hidden :id="`switch-${id}`">
            <input v-else type="checkbox" v-model="checked" hidden :id="`switch-${id}`">
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
                type: [Boolean,Number,String],
                default: null
            },
            name:String,
            label:String,
            layout:{
                default: 'widthFull',
                type: String
            },
            error:{
                type: String,
                default: null
            },
        },
        data(){
            return{
                id: "id"+ Math.floor(Math.random() * 50000000),
                checked: this.value,
                uiLayouts:{
                    widthFull: 'w-full',
                    widthFullReverse: 'w-full flex-row-reverse',
                    widthAuto: 'w-auto',
                    widthAutoReverse: 'w-auto flex-row-reverse'
                }
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
        @apply w-5 h-5 outline-none rounded-md bg-primaryBg-200 border flex justify-center items-center border-gray-400 cursor-pointer relative;
        @apply transition-all duration-300 ease-in-out;
    }
    .switch:hover,.switch:focus{
        @apply border-primary-500
    }
    .switch>span{
        transform-origin: center;
        transform: rotate(-45deg);
        @apply w-3 h-1 border-l border-b border-white invisible;
    }

    input[type=checkbox]:checked~.switch{
        @apply bg-primary-500 border-primary-500;
    }
    input[type=checkbox]:checked~.switch>span{
        @apply visible;
    }
</style>
