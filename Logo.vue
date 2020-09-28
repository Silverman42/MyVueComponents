<template>
  <img class="inline-block w-20 h-auto" :src="`${baseUrl}/img/standard_chartered_logo_svg.svg`" alt="" />
</template>

<script>
import {BASEURL} from "../api_endpoint";
export default {
    name: 'Logo',
    data(){
      return {
        baseUrl: BASEURL
      }
    }
}
</script>
