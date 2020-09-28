<template>
    <li>
        <router-link :to="to" active-class="text-primary-900 bg-primary-300" class="nav-link">
            <span class="icon">
                <slot name="icon"></slot>
            </span>
            <span class="text">
                <slot></slot>
            </span>
        </router-link>
    </li>
</template>

<script>
    export default {
        props:{
            to: {
                type: [String, Object],
                default(){
                    return '/'
                }
            }
        }
    }

</script>

<style>
    .nav-link{
        @apply block p-3 flex items-center font-bold rounded-md text-sm mb-2;
    }
    .nav-link:hover{
        @apply bg-primary-100;
    }
    .nav-link:hover>.text, .nav-link:hover>.icon{
        @apply text-primary-700
    }
    .nav-link>.text{
        @apply inline-block ml-2 text-gray-800
    }
    .nav-link>.icon{
        @apply inline-block font-light text-xl;
    }
</style>
