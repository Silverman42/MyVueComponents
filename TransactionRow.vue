<template>
    <div @click="click(item)" class="flex w-full p-3 mb-3 cursor-pointer rounded-md bg-primaryBg-200 hover:bg-primaryBg-300">
        <div class=" w-16 h-16">
            <span class="w-10 h-10 rounded-full flex items-center justify-center bg-primary-400 text-white mr-2">
                <iconify-icon :icon="icons.transaction" />
            </span>
        </div>
        <div class="flex flex-grow flex-wrap ">
            <div class="font-bold capitalize w-6/12">{{item.type.replace(/_/g,' ')}}</div>
            <div class="font-bold text-right w-6/12">
                <p>${{item.amount}}</p>
            </div>
            <div class="w-6/12 md:w-4/12 text-xs">
                <p>{{item.transaction_id}}</p>
            </div>
            <div class="md:w-4/12 w-6/12 text-right text-xs md:text-center">
                <p class="text-white w-auto py-1 px-2 capitalize inline-block rounded-lg"
                    :class="{'bg-green-400': item.status == 'completed', 'bg-yellow-400': item.status == 'processing','bg-red-500': item.status == 'cancelled'}">
                    {{item.status}}
                </p>
            </div>
            <div class="w-4/12 hidden md:block text-right text-xs">
                <p>{{item.created_at}}</p>
            </div>
        </div>
    </div>
</template>

<script>
    import briefcaseIcon from '@iconify/icons-feather/briefcase';
    export default {
        props:{
            item: Object
        },
        data(){
            return{
                icons:{
                    transaction: briefcaseIcon,
                }
            }
        },
        methods:{
            click(itemData){
                this.$emit('click',itemData)
            }
        }
    }

</script>

<style>

</style>
