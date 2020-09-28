<template>
    <div>
        <div class="mb-10 border-b pb-4 border-primaryBg-400">
            <h2 class="text-gray-800 mb-4 font-extrabold">Transfer Details</h2>
            <div class="mb-4">
                <h4 class="text-gray-500 text-xs">Bank Name</h4>
                <p class="capitalize">
                    {{details.bank_name || ''}}
                </p>
            </div>
            <div class="mb-4">
                <h4 class="text-gray-500 text-xs">Bank Address</h4>
                <p>
                    {{details.bank_address || ''}}
                </p>
            </div>
            <div class="mb-4">
                <h4 class="text-gray-500 text-xs">Account Number</h4>
                <p>
                    {{details.account_number || ''}}
                </p>
            </div>
            <div class="mb-4">
                <h4 class="text-gray-500 text-xs">Routine Number</h4>
                <p>
                    {{details.routine_number || ''}}
                </p>
            </div>
            <div>
                <h4 class="text-gray-500 text-xs">Your Account Balance</h4>
                <p>
                    ${{(details.debited_user_balance || 0)|cashFormat}}
                </p>
            </div>
        </div>
        <div class="mb-10">
            <h2 class="text-gray-800 mb-4 font-extrabold">Transfer Documents</h2>
            <div class="mb-3 ">
                <slot name="transferDocs"/>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'ModalTransferDetails',
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
