<template>
    <div class="container" v-if="isOpen == true">
        <transition-group tag="div">
            <aside key="backdrop" @click.prevent="closeModal" class="modal-backdrop">   
            </aside>
            <div key="modal" class="modal">
                <header v-if="deactivateCloseBtn == false">
                <a href="" class="text-sm flex items-center" @click.prevent="closeModal">
                    <span class="flaticon-left-chevron"></span> &nbsp;
                    <span>Back</span>
                </a>
                </header>
                <div class="body">
                    <slot></slot>
                </div>
            </div>
        </transition-group>
    </div>
</template>

<script>
export default {
    props:{
        isOpen:{
            type: Boolean,
            default: false
        },
        deactivateCloseBtn:{
            type: Boolean,
            default: false
        }
    },
    methods:{
        closeModal(){
            if(this.deactivateCloseBtn === false){
                return this.$emit('update:isOpen',false)
            }
        }
    },
    mounted(){
        const v = this
        window.addEventListener('keyup',(event)=>{
            event.preventDefault()
            if(event.keyCode == 27) v.closeModal()
        })
    }
}
</script>

<style scoped>
    .modal-backdrop{
        background: rgba(0,0,0,0.6); 
        z-index: 1000;
        @apply w-screen h-screen block fixed top-0 left-0 right-0 bottom-0;
    }
    .modal{
        z-index: 1100;
        @apply w-screen h-screen bg-white fixed top-0 right-0 bottom-0;
    }
    .modal>header{
        height: 8vh;
        @apply border-b border-primaryBg-300 px-4 py-2;
    }
    .modal>.body{
        @apply overflow-y-auto p-5;
        height:92vh;
    }
    @screen md{
        .modal{
            @apply w-6/12;
        }
    }
    @screen lg{
        .modal{
            @apply w-3/12;
        }
    }
</style>