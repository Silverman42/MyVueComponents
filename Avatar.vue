<template>
    <figure class="overflow-hidden rounded-full border-4 bg-primary-100" :class="{md:size == 'md',lg:size == 'lg',sm:size == 'sm'}">
        <div v-if="src == ''" class="flex items-center justify-center" :class="{md:size == 'md',lg:size == 'lg',sm:size == 'sm'}" :src="`${filePath}${src}`" :alt="alt">
            <img style="width: 50%; height: auto" :src="`${filePath}user.svg`" :alt="alt">
        </div>
        <img v-else class="block" :class="{md:size == 'md',lg:size == 'lg',sm:size == 'sm'}" :src="`${filePath}${src}`" :alt="alt">
    </figure>
</template>

<script>
    import {FILES,BASEURL} from '../api_endpoint'
    export default {
        props:{
            src: {
                default: '',
                type: String
            },
            alt: String,
            size: {
                default: 'sm',
                type: String
            }
        },
        data(){
            return{
                filePath: BASEURL+FILES.AVATAR
            }
        }
    }
</script>
<style scoped>
    .lg{
        @apply w-56 h-56;
    }
    .md{
        @apply w-32 h-32;
    }
    .sm{
        @apply w-10 h-10;
    }
</style>
