<template>
    <div>
        <div class="mb-10 border-b pb-4 border-primaryBg-400">
            <h2 class="text-gray-800 mb-4 font-extrabold">Deposit Details</h2>
            <div class="mb-4">
                <h4 class="text-gray-500 text-xs">Depositor's Name</h4>
                <p class="capitalize">
                    {{details.depositor_name || ''}}
                </p>
            </div>
            <div class="mb-4">
                <h4 class="text-gray-500 text-xs">Depositor's Address</h4>
                <p>
                    {{details.depositor_address || ''}}
                </p>
            </div>
            <div class="mb-4">
                <h4 class="text-gray-500 text-xs">Depositor's Phone Number</h4>
                <p>
                    {{details.depositor_phone || ''}}
                </p>
            </div>
            <div>
                <h4 class="text-gray-500 text-xs">Your Account Balance</h4>
                <p>
                    ${{(details.user_balance || 0)|cashFormat}}
                </p>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'ModalDepositDetails',
        props:{
            details:{
                type: Object,
                default(){
                    return {}
                }
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
