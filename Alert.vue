<template>
    <transition name="fade">
        <div class="alert" :class="[`bg-${color}-100`, `border-${color}-200`]">
            <div class="inline-block w-auto">
                <div class="alert-icon" :class="[`border-${color}-500`,`text-${color}-500`]">
                    <slot />
                </div>
            </div>
            <div>
                <h6 class="font-bold text-sm" :class="[`text-${color}-500`]">{{heading}}</h6>
                <p class="text-xs">{{message}}</p>
            </div>
            <button class="alert-close_btn" @click="closeAlert">
                <span class="" style=""></span>
                <span class=""></span>
            </button>
        </div>
    </transition>
</template>

<script>
    export default {
        props: {
            message: String,
            heading: String,
            color: {
                type: String,
                default: 'red'
            },
            timeOutDuration: {
                type: Number,
                default: 5000
            }
        },
        methods: {
            closeAlert() {
                this.$emit('closeAlert')
            }
        },
        mounted() {},
    }

</script>

<style scoped>
    .fade-enter-active, .fade-leave-active {
        transition: all .5s ease-in-out .2s;
    }
    .fade-enter /* .fade-leave-active below version 2.1.8 */ {
        opacity: 0;
        transform: translateY(30px)
    }
    .fade-leave-to{
        opacity: 0;
        transform: translateY(-30px)
    }
    .alert-close_btn {
        @apply w-5 h-5 absolute flex flex-wrap justify-center items-center top-0 right-0 mr-1 outline-none
    }

    .alert-close_btn>span {
        transform-origin: center;
        -webkit-transform-origin: center;
        @apply inline-block border border-gray-500 w-3;
    }

    .alert-close_btn>span:first-child {
        margin-bottom: -20px;
        transform: rotate(45deg);
    }

    .alert-close_btn>span:nth-child(2) {
        transform: rotate(-45deg);
    }

    .alert {
        @apply p-5 w-full flex relative border rounded-md shadow-lg my-4;
    }

    .alert-icon {
        @apply rounded-full border flex justify-center items-center w-10 h-10 bg-white shadow-lg mr-3;
    }

    @screen md {
        .alert {
            width: 300px;
            @apply ml-auto;
        }
    }

</style>
