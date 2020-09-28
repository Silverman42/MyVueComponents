<template>
    <div>
        <label class="block text-xs mb-1 flex justify-between" :for="id">
            <p>{{label}}</p>
            <div class="inline-block w-auto">
                <slot name="detail"></slot>
            </div>
        </label>
        <div class="mb-1">
            <slot></slot>
        </div>
        <p class="text-red-500 text-xs italic" v-if="error !== null">{{error}}</p>
    </div>
</template>

<script>
export default {
    name: 'FormGroup',
    props:{
        label: String,
        error:{
            type: String,
            default: null
        }
    },
    data(){
        return{
            id: "id"+ Math.floor(Math.random() * 50000000)  
        }
    }
}
</script>

<style>

</style>