<template>
    <div class=" h-100 m-5 bg-primaryBg-300 rounded-md p-5 shadow-lg">
        <h4 class="text-white font-bold mb-5">Trades</h4>
        <div class="flex mb-5">
            <span class="w-8 h-8 flex mr-2 items-center text-lg justify-center bg-red-900 text-red-500 rounded-full">
                <span class="flaticon-loss"></span>
            </span>
            <div class="text-xs flex-grow">
                <div class="mb-3">
                    <h5 class="font-bold">Trades Lost</h5>
                </div>
                <div class="text-white ml-auto p-3 flex rounded-md bg-primaryBg-400">
                    <div class="w-6/12">
                        <slot name="total-trades">${{lostTradeReturn|cashFormat}}</slot><br>
                        <span class="text-primaryBg-200">Lost</span>
                    </div>
                    <div class="w-6/12 text-right">
                        <slot name="total-trades">{{lostTradeCount}}</slot><br>
                        <span class="text-primaryBg-200">Trades</span>
                    </div>
                </div>
            </div>
        </div>
        <div class="flex mb-5">
            <span class="w-8 h-8 flex mr-2 items-center justify-center bg-green-900 text-green-500 rounded-full">
                <span class="flaticon-revenue"></span>
            </span>
            <div class="text-xs flex-grow">
                <div class="mb-3">
                    <h5 class="font-bold">Trades won</h5>
                </div>
                <div class="text-white ml-auto p-3 flex rounded-md bg-primaryBg-400">
                    <div class="w-6/12">
                        <slot name="total-trades">${{wonTradeReturn|cashFormat}}</slot><br>
                        <span class="text-primaryBg-200">Won</span>
                    </div>
                    <div class="w-6/12 text-right">
                        <slot name="total-trades">{{wonTradeCount}}</slot><br>
                        <span class="text-primaryBg-200">Trades</span>
                    </div>
                </div>
            </div>
        </div>
        <div class="flex">
            <span class="w-8 h-8 flex mr-2 items-center justify-center bg-primary-900 text-primary-500 rounded-full">
                <span class="flaticon-bar-chart"></span>
            </span>
            <div class="text-xs flex-grow">
                <div class="mb-3">
                    <h5 class="font-bold">All Trades</h5>
                </div>
                <div class="text-white ml-auto p-3 flex rounded-md bg-primaryBg-400">
                    <div class="w-6/12">
                        <slot name="total-trades">${{allTradeReturn|cashFormat}}</slot><br>
                        <span class="text-primaryBg-200">Returns</span>
                    </div>
                    <div class="w-6/12 text-right">
                        <slot name="total-trades">{{allTradeCount}}</slot><br>
                        <span class="text-primaryBg-200">Trades</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props:{
            wonTradeReturn:{
                type: Number,
                default: 0
            },
            lostTradeReturn:{
                type: Number,
                default: 0
            },
            allTradeReturn:{
                type: Number,
                default: 0
            },
            wonTradeCount: [Number],
            lostTradeCount: [Number],
            allTradeCount: [Number],
        },
        filters:{
            cashFormat(number) {
                return (new Intl.NumberFormat().format(number))
            }
        }
    }

</script>

<style>

</style>
