
<script setup lang="ts">
import type { Person } from '@/types/types';
import HomeSlider from '@/components/home/HomeSlider.vue';

const persons: Person[] = [
    {
        id: 1,
        name: "شريف الليثي",
        image: "sherif.png",
        position: "مؤسس دار تويا للنشر و التوزيع",

    }
]


</script>
<template>
    <div class="home-view">
        <section class="slider">
            <HomeSlider />
        </section>

        <section class="about">

        </section>

        <section class="video">

        </section>

        <section class="testemonial">

        </section>
        <section class="factory">

        </section>
        <section class="event">

        </section>

    </div>
</template>


<style>
.home-view {}
</style>