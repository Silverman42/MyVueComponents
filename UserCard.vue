<template>
    <!-- {name:'admin.clients.view',params:{client_id:item.uuid}} -->
    <router-link :to="route" v-if="item !== null"
        class="flex items-center justify-between cursor-pointer p-3 mb-3 rounded-md bg-primaryBg-300 hover:bg-primaryBg-400">
        <div class="flex items-center" style="max-width:80%">
            <div class="mr-2">
                <span>
                    <avatar :src="item.avatar || '' " />
                </span>
            </div>
            <div>
                <p class="font-bold text-xs md:text-sm capitalize break-words">{{item.first_name}}
                    {{item.last_name}}</p>
                <p class="text-xs ">
                    Ac. No - {{item.account_number || 'No account number'}}
                </p>
            </div>
        </div>
        <div class="text-right justify-end items-center flex">
            <div class="md:mr-3">
                <h4 class="text-xs md:text-lg font-bold">${{item.balance|cashFormat}}</h4>
            </div>
            <div class="hidden md:block">
                <div class="h-3 p-1 rounded-md"
                    :class="{'bg-green-500':item.is_active == 1, 'bg-red-500':item.is_active == 0 }">
                </div>
            </div>
        </div>
    </router-link>
</template>

<script>
    export default {
        name: 'UserCard',
        components:{
            Avatar: () => import( /* webpackChunkName: "components" */ './Avatar'),
        },
        props:{
            item:{
                type: Object,
                default(){
                    return {}
                }
            },
            route: Object
        },
        filters: {
            cashFormat(number) {
                return (new Intl.NumberFormat().format(number))
            }
        }
    }

</script>

<style>

</style>
