
<template>
    <div class="card">
        <Carousel :value="persons" :numVisible="3" :numScroll="3" :responsiveOptions="responsiveOptions">
            <template #item="slotProps">
                <div class="border-1 surface-border border-round m-2 text-center py-5 px-3">
                    <div class="mb-3">
                        <img :src="slotProps.data.image" :alt="slotProps.data.name" class="w-6 shadow-2" />
                    </div>
                    <div>
                        <h4 class="mb-1">{{ slotProps.data.name }}</h4>
                        <h6 class="mt-0 mb-3">{{ slotProps.data.title }}</h6>


                    </div>
                </div>
            </template>
        </Carousel>
    </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";
import Carousel from "primevue/carousel";



const persons = [
    {
        image: "../images/asmaa.png",
        name: "أسماء الراشدي",
        title: "مسئولة الشباب"
    },
    {
        image: "../images/Group 1.png",
        name: "أسماء الراشدي",
        title: "مسئولة الشباب"
    },
    {
        image: "../images/Group 2.png",
        name: "أسماء الراشدي",
        title: "مسئولة الشباب"
    },
    {
        image: "../images/Group 3.png",
        name: "أسماء الراشدي",
        title: "مسئولة الشباب"
    },
    {
        image: "../images/Group 4.png",
        name: "أسماء الراشدي",
        title: "مسئولة الشباب"
    },
];
const responsiveOptions = ref([
    {
        breakpoint: '1400px',
        numVisible: 2,
        numScroll: 1
    },
    {
        breakpoint: '1199px',
        numVisible: 3,
        numScroll: 1
    },
    {
        breakpoint: '767px',
        numVisible: 2,
        numScroll: 1
    },
    {
        breakpoint: '575px',
        numVisible: 1,
        numScroll: 1
    }
]);


</script>
