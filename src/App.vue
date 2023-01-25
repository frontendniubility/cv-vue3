<script setup>
import { ref } from 'vue'
import CVProfile from '@/CVProfile.vue';
import CVSection from '@/CVSection.vue';
import ImageModal from '@/ImageModal.vue';
import { sections } from '@/data.js';

const image = ref(null)

function interceptClickEvent(e) {
    if (e.target.tagName === 'A') {
        if (/^\/img\//.test(e.target.getAttribute("href"))) {
            e.preventDefault()
            image.value = e.target.href
        } else if (!e.target.target) {
            e.target.target = '_blank'
        }
    }
}
if (document.addEventListener) {
    document.addEventListener('click', interceptClickEvent);
} else if (document.attachEvent) {
    document.attachEvent('onclick', interceptClickEvent);
}
</script>

<template>
    <main>
        <CVProfile />
        <div v-for="section in sections" :key="section.title" class="sections">
            <CVSection :section="section" />
        </div>
    </main>
    <ImageModal v-if="image" :image="image" @closeModal="image = null" />

</template>

<style lang="scss" scoped>
main {
    background-color: $color-bg-paper;
    background-image: url('/img/paper.jpg');
    padding: 50px;
    margin: 40px;
    box-shadow: 0px 0px 15px 10px rgba(0, 0, 0, 0.5);
    margin: 40px auto;
    display: block;
    .sections {
        display: flex;
        flex-direction: column;
        gap: 30px;
    }
}

@media print {
    main {
        box-shadow: none;
        background-image: none;
        margin: 0;
    }
}
</style>
