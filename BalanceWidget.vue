<template>
  <div class=" h-100 m-5 bg-white rounded-md p-3 shadow-lg text-center">
    <h4 class="text-xl">
      <span class="font-light flaticon-coin"></span> 
      <span class="font-bold text-black"><slot>{{ amount|cashFormat }}</slot></span>
    </h4>
    <p class="text-xs">Current balance</p>
</div>
</template>

<script>
export default {
  name: 'BalanceWidget',
  props:{
    amount: {
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