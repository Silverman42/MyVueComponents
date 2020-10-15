<template>
    <div class="alert-container">
        <slot/>
    </div>
</template>

<script>
export default {
    name: 'AlertContainer'
}
</script>

<style scoped>
    .alert-container {
        @apply fixed w-full bg-transparent bottom-0 left-0 right-0 px-2;
        z-index: 900000;
    }
    @screen md {
        .alert-container {
            @apply left-auto w-auto;
        }
    }
</style>