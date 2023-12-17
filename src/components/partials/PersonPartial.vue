<script setup lang="ts">
import type { PersonPartialProps } from '@/types/types'
// import AppImage from '@/components/app/AppImage.vue';
const props = defineProps<PersonPartialProps>()
const { image,
    name,
    position } = props.person
</script>
 <!-- zoominleft animation-duration-1000 animation-iteration-1 -->
<template>
    <div class="person md:flex flex-column align-items-center  justify-content-center">
        <AppImage :src="props.person.image" :size="props.size" />
        <div class="py-2 px-5 borderRound name-wrapper" style="background-color: #D9B58D;">
            <h1 class="title">{{ name }}</h1>
            <h4 class="position">{{ position }}</h4>
        </div>
    </div>
</template>
