<template>
    <figure class="overflow-hidden rounded-full bg-primaryBg-300" :class="{md:size == 'md',lg:size == 'lg',sm:size == 'sm'}">
        <div v-if="src == ''" class="flex items-center justify-center w-full h-full"   >
            <iconify-icon :width="defaultAvatarSize" :height="defaultAvatarSize" :icon="user" />
        </div>
        <img v-else class="block object-center object-fill" :class="{md:size == 'md',lg:size == 'lg',sm:size == 'sm'}" :src="`${src}`" :alt="alt">
    </figure>
</template>

<script>
    // import {FILES,BASEURL} from '../api_endpoint'
    import user from '@iconify/icons-feather/user'
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
                user
            }
        },
        computed:{
            defaultAvatarSize(){
                if(this.size === 'sm') return 20
                if(this.size === 'md') return 40
                if(this.size === 'lg') return 70
            }
        }
    }
</script>
<style scoped>
    .lg{
        @apply w-40 h-40;
    }
    .md{
        @apply w-20 h-20;
    }
    .sm{
        @apply w-10 h-10;
    }
</style>
