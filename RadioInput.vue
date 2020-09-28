<template>
  <label :for="id" class="container" >
      <input type="radio" v-model="checked" @change="getInputValue($event)" :name="name" :value="value" class="radio" :id="id">
      <div class="background">
          <span class="tick"></span>
            <p class="label capitalize">
                {{title}}
            </p>
      </div>
  </label>
</template>

<script>
export default {
    name: 'RadioInput',
    props:{
        title:String,
        defaultValue:String,
        value:String,
        name:String
    },
    data(){
        return{
            id: "id"+ Math.floor(Math.random() * 50000000),
            checked: this.defaultValue,
        }
    },
    methods:{
        getInputValue(event){
            return this.$emit('input',event.target.value)
        }
    }
}
</script>

<style scoped>
    .container{
        @apply inline-block w-auto mr-2;
    }
    .container:last-child{
        @apply mr-0;
    }
    .container>.radio{
        @apply hidden h-0 w-0;
    }
    .background{
        @apply inline-flex rounded-md h-12 w-auto px-4 items-center overflow-hidden bg-primaryBg-200;
        @apply transition-all duration-300 ease-in-out;
    }
    .radio:checked~.background{
        @apply bg-primary-600
    }
    .tick{
        @apply w-3 h-3 border-2 rounded-full inline-block mr-2 border-primaryBg-400;
        @apply transition-all duration-300 ease-in-out;
    }
    .radio:checked~.background>.tick{
        @apply border-white bg-white;
    }
    .label{
        @apply font-bold;
        @apply transition-all duration-300 ease-in-out;
    }
    .radio:checked~.background>.label{
        @apply text-white;
    }
</style>