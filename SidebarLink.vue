<template>
    <li>
        <router-link :to="to" class="sidebar-link" active-class="active-link" :exact="exact">
            <span class="icon">
                <slot name="icon">l</slot>
            </span>
            <span class="text">
                <slot name="text"></slot>
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
        },
        exact:{
            type: Boolean,
            default: false
        }
    }
}
</script>
<style scoped>
    .sidebar-link{
        @apply block p-3 flex flex-col items-center font-bold text-xs rounded-md;
    }
    .sidebar-link:hover>.text,
    .sidebar-link:hover>.icon,
    .active-link>.text,
    .active-link>.icon{
        @apply text-primary-600 !important;
    }
    .sidebar-link>.text{
        @apply inline-block text-gray-700
    }
    .sidebar-link>.icon{
        @apply inline-block font-light text-xl mb-1;
    }
    @screen md {
        .sidebar-link{
            @apply justify-start flex-row text-sm;
        }
        .sidebar-link:hover,.active-link{
            @apply bg-primary-200
        }
        .sidebar-link>.text{
            @apply ml-4
        }
        .sidebar-link>.icon{
            @apply mb-0;
        }
    }
</style>