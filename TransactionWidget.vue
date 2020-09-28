<template>
    <div class=" h-100 m-5 bg-primaryBg-300 rounded-md p-5 pb-8 shadow-lg">
        <h4 class="text-white font-bold mb-5">Transactions</h4>
        <div class="p-2 bg-primaryBg-400 rounded-md mb-5">
            <h4 class="mb-2 text-sm font-bold text-red-500">
                Withdrawals
            </h4>
            <div class="flex items-center mb-5">
                <span class="w-8 h-8 flex mr-2 items-center justify-center bg-red-900 text-red-500 rounded-full">
                    W
                </span>
                <div class="text-xs pr-2 mr-2 border-r border-primaryBg-200">
                    <h5 class="font-bold text-base">
                        <slot name="withdraw-count">{{withdrawalCount}}</slot>
                    </h5>
                    <p class="text-primaryBg-100">Withdrawals made</p>
                </div>
                <div class="text-xs pr-2">
                    <h5 class="text-base">
                        <span class="font-light"></span>$<span class="font-bold"><slot name="withdraw-total">{{withdrawalTotal|cashFormat}}</slot></span>
                    </h5>
                    <p class="text-primaryBg-100">Withdrawn</p>
                </div>
            </div>
        </div>
        <div class="p-2 bg-primaryBg-400 rounded-md">
            <h4 class="mb-2 text-sm font-bold text-primary-500">
                Deposits
            </h4>
            <div class="flex items-center mb-5">
                <span class="w-8 h-8 flex mr-2 items-center justify-center bg-primary-900 text-primary-500 rounded-full">
                    D
                </span>
                <div class="text-xs pr-2 mr-2 border-r border-primaryBg-200">
                    <h5 class="font-bold text-base"><slot name="deposit-count">{{depositCount}}</slot></h5>
                    <p class="text-primaryBg-100">Deposits made</p>
                </div>
                <div class="text-xs pr-2">
                    <h5 class="text-base">
                        <span class="font-light"></span>$<span class="font-bold"><slot name="deposit-total">{{depositTotal|cashFormat}}</slot></span>
                    </h5>
                    <p class="text-primaryBg-100">Deposited</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props:{
            depositTotal:{
                type: Number,
                default: 0
            },
            withdrawalTotal:{
                type: Number,
                default: 0
            },
            depositCount:{
                type: Number,
                default: 0
            },
            withdrawalCount: {
                type: Number,
                default: 0
            }
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
