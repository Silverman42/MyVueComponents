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
        <!-- <div class="mb-8 border-b border-primaryBg-400 pb-4">
            <h2 class="text-gray-800 mb-4 font-extrabold">Transfer Documents</h2>
            <div class="mb-3 ">
                <slot name="transferDocs"/>
            </div>
        </div> -->
        <div class="mb-8 border-b border-primaryBg-400 pb-4">
            <h2 class="text-gray-800 mb-4 font-extrabold">Send Transfer OTP</h2>
            <div class="mb-3 ">
                <p class="text-xs">Send One Time Password (OTP) to the transfer client's mail box</p>
                <div class="mt-4">
                    <slot name="transferOTPButton"/>
                </div>
            </div>
        </div>
        <div class="mb-8 border-b border-primaryBg-400 pb-4">
            <h2 class="text-gray-800 mb-4 font-extrabold">Process Transfer</h2>
            <div class="mb-3 ">
                <p class="text-xs">In the event you do not wish to send an OTP to the transfer executor, click this button to process the client's transfer </p>
                <div class="mt-4">
                    <slot name="processTransferButton"/>
                </div>
            </div>
        </div>
        <div class="mb-8">
            <h2 class="text-gray-800 mb-4 py-3 font-extrabold">Cancel Transfer</h2>
            <div class="mb-3 ">
                <p class="text-xs">Cancel a transfer in processing state. This action is irrevesible</p>
                <div class="mt-4">
                    <slot name="transferCancelButton"/>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'ModalTempTransferDetails',
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
