<template>
<keep-alive>
    <div>
      <header>
          <ul class="tab-header">
              <li v-for="(tab,index) in tabArray" 
              :key="index" class="tab-btns" 
              :class="{'active': activeTab == tab}"
              @click="setActiveTab(tab)">
                  <slot :name="createTabSlotName(tab)">{{tab}}</slot>
              </li>
          </ul>
      </header>
      <main class="tab-body">
         <slot :name="getTabBodyName"></slot>
      </main>
  </div>
</keep-alive>
</template>

<script>
export default {
    props:{
        tabs:Array,
        defaultActiveTab: String
    },
    data(){
        return {
            activeTab: this.defaultActiveTab,
            tabArray: this.tabs
        }
    },
    computed:{
        getTabBodyName(){
            return `tab-body-${this.activeTab}`
        }
    },
    methods:{
        generateRandomKeys(){
            return Math.ceil(Math.random() * 500000000)
        },
        createTabSlotName(tab){
            return `tab-${tab}`
        },
        setActiveTab(tab){
            this.activeTab = tab
            this.$emit('tabSwitch',tab)
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
        @apply p-2 mx-2 cursor-pointer rounded-md inline-block w-auto font-bold text-xs capitalize whitespace-no-wrap;
        @apply transition-all duration-200 ease-in; 
    }
    .tab-btns:hover{
        @apply bg-primaryBg-300;
    }
    .tab-btns.active{
        @apply bg-primaryBg-300;
    }
    @screen md{
        .tab-header{
            @apply flex-wrap
        } 
    }
</style>