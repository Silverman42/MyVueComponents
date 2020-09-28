<template>
  <div class="p-2 bg-primaryBg-300 relative rounded-md overflow-hidden">
    <span class="block absolute top-0 bottom-0 left-0 h-12 bg-primary-700" style="transition: all 0.3s ease-in-out" :style="{'width': `${length}%`}"></span>
  </div>
</template>

<script>
export default {
    name: 'ProgressBar',
    props:{
        length:{
            type:Number,
            default: 0
        }
    },
    computed:{
        maxLength(){
            if(this.length > 100){
                return 100
            }
            return this.length
        }
    }
}
</script>