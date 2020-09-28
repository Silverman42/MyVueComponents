<template>
  <div class="rounded-md overflow-hidden bg-white shadow-xl mb-8" key="avatar">
        <div class="h-32"
            :style="{'background-image': `url(${baseUrl}/img/profile_bg.png)`,'background-size':'100%'}">
        </div>
        <div class="flex flex-col text-center items-center p-3 mb-3">
            <figure class="inline-block w-auto mb-3" style="margin-top:-4.5rem">
                <avatar size="md" :src="src" :alt="alt"/>
            </figure>
            <div v-if="loading == true">
                <span class="w-20 skeleton">
                    <span></span>
                </span>
            </div>
            <div v-else>
                <slot/>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    components:{
        Avatar: () => import( /* webpackChunkName: "components" */ '../components/Avatar')
    },
    props:{
        baseUrl: {
            type: String,
            default: ''
        },
        src: String,
        alt: String,
        loading:{
            type: Boolean,
            default: false
        }
    }
}
</script>

<style scoped>
    .skeleton {
        @apply block h-3 mb-2 rounded-md bg-primaryBg-400 overflow-hidden
    }

    .skeleton span {
        @apply h-3 w-20 block;
        background: linear-gradient(90deg, theme('colors.primaryBg.400'), theme('colors.primaryBg.300'), theme('colors.primaryBg.400'));
        animation: slide 2s ease-in-out infinite;
    }

    @keyframes slide {
        from {
            transform: translateX(-5rem);
        }

        to {
            transform: translateX(200%);
        }
    }
</style>