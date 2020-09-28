<template>
    <div class="p-6 md:p-12 rounded-lg shadow-lg bg-primary-900 reveal-up" style="--delay: 0.3s ; min-height: 8rem" :style="{'background-image' : `url(${hostName}/${boardBgLink || ''})`}">
        <slot/>
        <div class="flex justify-between items-center">
            <div class="w-56 md:w-6/12">
                <h1 class="text-2xl mb-2 text-white antialiased reveal-left" style="--delay: 0.3s">{{boardTitle || ''}}</h1>
                <p class="text-primary-100 text-sm reveal-left" style="--delay: 0.5s">{{boardText || ''}}</p>
            </div>
            <div v-if="boardImgLink" class="w-20 md:w-30 reveal-up" style="--delay: 0.7s">
                <img class="w-full" :src="hostName+'/'+boardImgLink" />
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'TitleProps',
        props:{
            boardImgLink: String,
            boardBgLink: String,
            boardText: String,
            boardTitle: String,
            hostName: String,
        }
    }

</script>

<style>

</style>
