<!-- 

<script setup>
import { ref, onMounted } from "vue";
import { ProductService } from '@/service/ProductService';

onMounted(() => {
    ProductService.getProductsSmall().then((data) => (products.value = data.slice(0, 9)));
})

const products = ref();
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

const getSeverity = (status) => {
    switch (status) {
        case 'INSTOCK':
            return 'success';

        case 'LOWSTOCK':
            return 'warning';

        case 'OUTOFSTOCK':
            return 'danger';

        default:
            return null;
    }
};

</script> -->
<script setup lang="ts">
import type { Person } from '@/types/types';
import PersonPartial from '../partials/PersonPartial.vue';
import Carousel from 'primevue/carousel';
import Galleria from './GalleriaComponent.vue';
const persons: Person[] = [
    {
        id: 1,
        name: "شريف الليثي",
        image: "sherif.png",
        position: "مؤسس دار تويا للنشر و التوزيع",

    },
    {
        id: 2,
        name: "شريف سعيد",
        image: "sherif.png",
        position: "مؤسس دار تويا للنشر و التوزيع",

    }
]

</script>
<template>
    <div class="card">
        <Galleria />
    </div>
</template>