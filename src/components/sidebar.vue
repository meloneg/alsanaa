<script setup lang="ts">
import { useRouter } from 'vue-router';
import { ref } from 'vue';
import Sidebar from 'primevue/sidebar';

const { push, currentRoute } = useRouter();
const isMobExpanded = ref(true)
function scrollToSection(sectionId: any) {
    push({ path: '/', hash: `#${sectionId}` })
    const section = document.getElementById(sectionId);
    if (section) {
        section.scrollIntoView({ behavior: 'smooth' });
    }
}

</script>
<template>
    <span @click="isMobExpanded = true"
        class="material-symbols-outlined cursor-pointer text-6xl flex md:hidden fixed primaryColor font-bold"
        style="top: 1.5vh; right: 3vh; z-index: 999;">
        menu
    </span>
    <div class="  md:flex gredBg py-5 px-3 w-5rem flex-column justify-content-center align-items-center">
        <img src="../images/logo.png" class="w-6 absolute" style="top: 5vh;" alt="">
        <span class="material-symbols-outlined cursor-pointer primaryColor text-5xl my-3"
            @click="scrollToSection('section1')" :class="{ 'activeSection': currentRoute.hash == '#section1' }">
            pages
        </span>
        <span class="material-symbols-outlined cursor-pointer primaryColor text-5xl my-3"
            @click="scrollToSection('sectionHome1')"
            :class="{ 'activeSection': currentRoute.hash.includes('#sectionHome') }">
            home
        </span>
        <span class="material-symbols-outlined cursor-pointer primaryColor text-5xl my-3">
            build
        </span>
        <span class="material-symbols-outlined cursor-pointer primaryColor text-5xl my-3">
            engineering
        </span>
    </div>
    <div class="image-overlay"></div>
</template>
<style>
.activeSection {
    padding: 2px 0;
    border-bottom: 4px solid var(--primary-color);
}

.gredBg {
    height: 100vh;
    z-index: 9;
    position: fixed;
    background: linear-gradient(to bottom, rgb(19, 24, 28) 0%, rgb(30, 34, 42) 100%);
}

.p-sidebar-icon {
    display: none !important;
}

.image-overlay {
    width: 60%;
    height: 100%;
    background-image: url('../images/logoForBg.png');
    background-repeat: no-repeat;
    background-size: cover;
    position: fixed;
    right: 7.2%;
    opacity: 0.5;
    /* Adjust the opacity as needed */
}

.sidebar {
    display: flex;
    flex-direction: column;
    align-items: center;
    background: var(--gredient-color);
    width: 100px;
    border-end-end-radius: 25px;
    border-start-end-radius: 25px;
    box-shadow: 2px 0px 10px rgba(0, 0, 0, 0.81);
    height: 100vh;
    background-color: #f2f2f2;
    position: fixed;
    top: 0;
    right: 0;
    z-index: 9;
    transition: width 0.3s ease;
    overflow-y: auto;
}

@media screen and (max-width : 600px) {
    .image-overlay {
        right: 1%;
    }

}
</style>