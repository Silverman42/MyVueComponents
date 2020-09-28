<template>
    <div>
        <div class="mb-10 border-b pb-4 border-primaryBg-400">
            <h2 class="text-gray-800 mb-4 font-extrabold">Withdrawal Details</h2>
            <div class="mb-4">
                <h4 class="text-gray-500 text-xs">Withdrawal Location</h4>
                <p class="capitalize">
                    {{details.location || ''}}
                </p>
            </div>
            <div class="mb-4">
                <h4 class="text-gray-500 text-xs">Withdrawer</h4>
                <p class="capitalize">
                    {{details.withdrawer || ''}}
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
