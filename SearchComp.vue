<template>
    <div class="bg-white rounded-md" key="body">
        <div class="flex items-center w-full mb-5" v-if="noSearch == false">
            <form action="" @submit.prevent="makeFreshSearch" id="search-form"></form>
            <div class="flex-grow mr-2">
                <text-input v-model="searchParam" form="search-form" type="search" :placeholder="searchPlaceholder" />
            </div>
            <div>
                <primary-btn :loading="loading == true" type="submit" form="search-form">
                    Search
                </primary-btn>
            </div>
        </div>
        <div>
            <slot></slot>
            <!--Search Items end-->
            <!--Skeleton Start-->
            <div v-if="loading == true">
                <div v-for="(skeleton,index) in 5" :key="index" class="flex justify-between p-3 mb-3">
                    <div>
                        <span class="w-24 skeleton">
                            <span></span>
                        </span>
                        <span class="w-20 md:w-48 skeleton">
                            <span></span>
                        </span>
                    </div>
                    <div class="flex items-end flex-col">
                        <span class="w-24 md:w-32 skeleton">
                            <span></span>
                        </span>
                        <span class="w-10 md:w-20 skeleton">
                            <span></span>
                        </span>
                    </div>
                </div>
            </div>
            <!--Skeleton end-->
            <!--Try Again Box Start-->
            <div class="bg-white rounded-md p-3 py-10 text-center" v-if="loading == false && dataCount == 0">
                <div class="inline-block m-auto w-6/12 mb-10">
                    <slot name="not_found_image"/>
                </div>
                <span class="text-lg block text-gray-800 font-bold">No Result Found</span> <br><br>
                <div class="flex justify-center">
                    <secondary-btn @click="makeFreshSearch">Try Again</secondary-btn>
                </div>
            </div>
            <!--Try Again Box end-->
            <div class="flex justify-center p-3" v-if="loading == false && (dataCount > 0 && loadMore == true)">
                <primary-btn @click="loadMoreSearchItems" width="w-full">Load More</primary-btn>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            loading: {
                type: Boolean,
                default: false
            },
            dataCount: {
                type: Number,
                default: 0,
            },
            noSearch:{
                type: Boolean,
                default: false
            },
            loadMore:{
                type: Boolean,
                default: true
            }
        },
        data() {
            return {
                searchParam: '',
                searchPlaceholder: '',
            }
        },
        methods:{
            makeFreshSearch(){
                return this.$emit('freshSearch',this.searchParam)
            },
            loadMoreSearchItems(){
                return this.$emit('loadMore',this.searchParam)
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
