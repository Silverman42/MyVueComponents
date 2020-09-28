<template>
    <div class="crypto-card">
        <header class="text-xs mb-2 flex items-center text-yellow-600">
            <span class=" flaticon-blockchain"></span><span
                class="inline-block ml-2 font-bold">{{coinName || '---------'}}</span>
        </header>
        <div class="mb-2 text-center">
            <span class="text-xs uppercase tracking-widest">Address</span> <br>
            <span class="text-white">{{coinAddress || '-----------------'}}</span>
        </div>
        <div class="mb-2">
            <h4 class="text-xl text-center">
                <span class="font-light flaticon-coin"></span>
                <span class="font-bold">
                    <slot>{{amount||'0'|cashFormat}}</slot>
                </span>
            </h4>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Coin',
        props:{
            coinName:String,
            coinAddress: String,
            amount: [String,Number]
        },
        filters:{
            cashFormat(number) {
                return (new Intl.NumberFormat().format(number))
            }
        }
    }
</script>

<style>
    .crypto-card {
        @apply p-3 rounded-md shadow-lg;
        background-image: linear-gradient(45deg, theme('colors.black'), theme('colors.gray.800'), theme('colors.black'));
    }
</style>
