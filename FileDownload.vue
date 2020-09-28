<template>
  <a target="_blank" :href="href" :class="[extend,{'opacity-25':loading == true || disabled == true,
        'cursor-not-allowed' : disabled == true,
        'cursor-wait' : loading == true}]" :disabled="disabled" class="file_download">
      <div class="w-8/12 text-left">
            <h1 class="font-bold text-sm capitalize">{{label}}</h1>
            <p class="uppercase text-xs text-gray-500">{{type}}</p>
      </div>
      <div>
          <span class="text-primary-500">
              <iconify-icon :icon="icons.file" width="30"/>
          </span>
      </div>
  </a>
</template>

<script>
import fileIcon from '@iconify/icons-feather/file'
export default {
    name: 'FileDownload',
    props:{
        label: String,
        type: String,
        extend: String,
        disabled: Boolean,
        loading: Boolean,
        href: {
            default: '#',
            type: String
        }
    },
    data(){
        return {
            icons:{
                file: fileIcon
            }
        }
    }
}
</script>

<style>
.file_download{
    @apply p-5 flex w-full items-center justify-between border rounded-md transition-shadow ease-out duration-300;
}
.file_download:hover{
    @apply shadow-xl
}
</style>