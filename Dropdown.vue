<template>
    <div class="dropdown" :class="[extraClass]">
        <span class="content">
            <slot></slot>
        </span>
        <ul class="box" :class="{'right': boxPosition === 'right', 'left': boxPosition === 'left'}">
            <slot name="box"></slot>
        </ul>
    </div>
</template>

<script>
    export default {
        props:{
            boxPosition:{
                type: String,
                default: 'right'
            },
            extraClass: String
        }
    }

</script>

<style scoped>
  .dropdown{
      @apply inline-block relative w-auto;
  }
  .dropdown>.box.left{
      left: 0
  }
  .dropdown>.box.right{
      right: 0
  }
  .dropdown>.box{
      @apply absolute rounded-md list-none inline-block p-3 invisible shadow-md bg-white border border-gray-200 transition-all duration-300 ease-out opacity-0;
      top: 150%;
      min-width: 120px;
      z-index: 40 !important
  }
  .dropdown:hover>.box, .dropdown:focus>.box{
      @apply visible opacity-100;
      top: 120%;
  }
</style>
