<template>
    <div class="atm-card">
        <div></div>
        <div class="text-center mb-3">
            <span class="text-xs tracking-widest uppercase">{{ cardName ||'CARD NAME'}}</span><br>
            <span class="text-white tracking-wider">{{(cardCC || 'xxxxxxxxxxxxxxxx') | cardNumberFormat}}</span>
        </div>
        <div class="flex justify-between">
            <div class="text-left">
                <span class="text-xs tracking-widest">EXPIRES AT</span><br>
                <span
                    class="text-white tracking-wider">{{(expiryMonth || '00')|expiryMonthFormat }}/{{(expiryYear || '00')|expiryYearFormat }}</span>
            </div>
            <div class="text-right">
                <span class="text-xs tracking-widest">CCV</span><br>
                <span class="text-white tracking-wider">{{cardCCValue || '---'}}</span>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Card',
        props:{
            cardName:String,
            cardCC:[String,Number],
            expiryMonth: [String,Number],
            expiryYear: [String,Number],
            cardCCValue: [String,Number]
        },
        filters:{
             cardNumberFormat(number) {
                let numberArray = (`${number || 'xxxxxxxxxxxxxxx'}`).split('')
                const set = []
                set[0] = (numberArray.slice(0, 4)).join('')
                set[1] = (numberArray.slice(4, 8)).join('')
                set[2] = (numberArray.slice(8, 12)).join('')
                set[3] = (numberArray.slice(12, numberArray.length)).join('')
                return `${set[0]}  ${set[1]}  ${set[2]}  ${set[3]}`
            },
            expiryMonthFormat(number) {
                if(number == '' || number == null){
                    return 0
                }
                return (parseInt(number) > 12 ? 12 : number)
            },
            expiryYearFormat(number) {
                if(number == '' || number == null){
                    return '00'
                }
                const set = `${number}`.split('')
                let [first, second] = [(set[set.length - 2] || 0), (set[set.length - 1] || 0)]
                return (`${first}${second}`)
            }
        }
    }
</script>

<style scoped>
    .atm-card {
        @apply p-3 rounded-md shadow-lg;
        background-image: linear-gradient(45deg, theme('colors.red.600'), theme('colors.primary.600'), theme('colors.red.700'));
    }
</style>
