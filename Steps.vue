<template>
<keep-alive>
    <div>
      <header>
          <div class="h-2 rounded-md overflow-hidden w-full mb-8" :class="[`bg-${color}-100`]">
              <span class=" block h-2 transition-all duration-300 ease-out rounded-lg" :class="[`bg-${color}-500`]" :style="{width: `${stepPercentage}%`}">
              </span>
          </div>
      </header>
      <main class="tab-body">
         <slot :name="getStepBodyName"></slot>
      </main>
  </div>
</keep-alive>
</template>

<script>
export default {
    props:{
        defaultActiveStep: {
            type: Number,
            default: 1
        },
        steps:{
            type: Number,
            default: 5
        },
        color: {
            type: String,
            default: 'primary'
        }
    },
    computed:{
        getStepBodyName(){
            return `step-${this.defaultActiveStep}`
        },
        stepPercentage(){
            return Math.ceil((100 / this.steps) * this.defaultActiveStep)
        }
    },
    name: 'Tabs',
}
</script>

<style scoped>
    .tab-header{
        @apply bg-primaryBg-400 rounded-md p-2 flex items-center list-none overflow-x-auto
    }
    .tab-btns{
        @apply p-2 mx-2 cursor-pointer rounded-md inline-block w-auto font-bold text-primaryBg-200 text-xs capitalize whitespace-no-wrap;
        @apply transition-all duration-200 ease-in; 
    }
    .tab-btns:hover{
        @apply text-white;
    }
    .tab-btns.active{
        @apply bg-primaryBg-300 text-white;
    }
    @screen md{
        .tab-header{
            @apply flex-wrap
        } 
    }
</style>