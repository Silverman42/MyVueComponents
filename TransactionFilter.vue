<template>
    <div class="py-3">
        <div class="mb-8">
            <h3 class="font-bold text-lg text-black">
                Filter Search
            </h3>
            <p class="text-xs">Search for transactions using precise parameters</p>
        </div>
        <div>
            <form @submit.prevent ="filterSearch" id="advanced_filter"></form>
            <div class="mb-5">
                <text-input label="Transaction id" type="number" form="advanced_filter" v-model="transaction_id"
                    placeholder="" />
            </div>
            <div class="mb-5">
                <div class="text-xs">Transaction Amount Between</div>
                <div class="flex items-center justify-between">
                    <div class="w-5/12">
                        <text-input label="" type="number" form="advanced_filter" v-model="lower_amount"
                            placeholder="" />
                    </div>
                    <div class="">&</div>
                    <div class="w-5/12">
                        <text-input label="" type="number" form="advanced_filter" v-model="higher_amount"
                            placeholder="" />
                    </div>
                </div>
            </div>
            <div class="mb-5">
                <div class="text-xs">Date range between</div>
                <div class="flex items-center justify-between">
                    <div class="w-4/12 mr-2">
                        <text-input label="" type="number" :hasMaxLength="true" :maxLength="2"  form="advanced_filter" v-model="from_day" placeholder="DD" />
                    </div>
                    <div class="w-4/12 mr-2">
                        <text-input label="" type="number" form="advanced_filter" :hasMaxLength="true" :maxLength="2"  v-model="from_month"
                            placeholder="MM" />
                    </div>
                    <div class="w-4/12">
                        <text-input label="" type="number" form="advanced_filter" :hasMaxLength="true" :maxLength="4"  v-model="from_year"
                            placeholder="YYYY" />
                    </div>
                </div>
                <p>&</p>
                <div class="flex items-center justify-between">
                    <div class="w-4/12 mr-2">
                        <text-input label="" type="number" form="advanced_filter" v-model="to_day" :hasMaxLength="true" :maxLength="2"  placeholder="DD" />
                    </div>
                    <div class="w-4/12 mr-2">
                        <text-input label="" type="number" form="advanced_filter" v-model="to_month" :hasMaxLength="true" :maxLength="2"  placeholder="MM" />
                    </div>
                    <div class="w-4/12">
                        <text-input label="" type="number" form="advanced_filter" :hasMaxLength="true" :maxLength="4"  v-model="to_year"
                            placeholder="YYYY" />
                    </div>
                </div>
            </div>
            <div class="mb-5">
                <div class="text-xs">Transaction on a specific date</div>
                <div class="flex items-center justify-between">
                    <div class="w-4/12 mr-2">
                        <text-input label="" type="number" form="advanced_filter" :hasMaxLength="true" :maxLength="2"  v-model="day" placeholder="DD" />
                    </div>
                    <div class="w-4/12 mr-2">
                        <text-input label="" type="number" form="advanced_filter" v-model="month" :hasMaxLength="true" :maxLength="2"  placeholder="MM" />
                    </div>
                    <div class="w-4/12">
                        <text-input label="" type="number" form="advanced_filter" v-model="year" :hasMaxLength="true" :maxLength="4"  placeholder="YYYY" />
                    </div>
                </div>
            </div>
            <div class="mb-5">
                <select-input form="advanced_filter" v-model="status" label="Transaction status" :value="status">
                    <option value=" ">Select status</option>
                    <option value="completed">Completed</option>
                    <option value="processing">Processing</option>
                </select-input>
            </div>
            <div class="mb-8">
                <select-input form="advanced_filter" v-model="type" label="Transaction type" :value="type">
                    <option value=" ">Select type</option>
                    <option value="transfer">Transfer</option>
                    <option value="withdrawal">Withdrawal</option>
                    <option value="deposit">Deposit</option>
                </select-input>
            </div>
            <div class="mb-5">
                <primary-btn type="submit" width="w-full" form="advanced_filter">
                    Search Transaction
                </primary-btn>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                transaction_id: '',
                higher_amount: '',
                lower_amount: '',
                type: ' ',
                status: ' ',
                month: '',
                year:'',
                day:'',
                from_month: '',
                from_year: '',
                from_day: '',
                to_month: '',
                to_year: '',
                to_day: ''
            }
        },
        computed:{
            getDate(){
                if(this.month !== '' && this.year !== '' & this.day !== ''){
                    return `${this.year}-${this.month}-${this.day}`
                }
                return ''
            },
            getFromDate(){
                if(this.from_month !== '' && this.from_year !== '' & this.from_day !== ''){
                    return `${this.from_year}-${this.from_month}-${this.from_day}`
                }
                return ''
            },
            getToDate(){
                if(this.to_month !== '' && this.to_year !== '' & this.to_day !== ''){
                    return `${this.to_year}-${this.to_month}-${this.to_day}`
                }
                return ''
            }
        },
        methods:{
            filterSearch(){
                const parameters = {
                    data: {
                        transaction_id : this.transaction_id,
                        higher_amount: this.higher_amount,
                        lower_amount: this.lower_amount,
                        type: this.type,
                        status: this.status,
                        date: this.getDate,
                        date_from: this.getFromDate,
                        date_to: this.getToDate
                    }
                }
                this.$emit('submitFilter',parameters)
            }
        }
    }

</script>

<style>

</style>
