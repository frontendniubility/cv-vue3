<script setup>
import { onMounted, onUnmounted } from 'vue'
const emit = defineEmits(['closeModal'])

defineProps({
    image: String,
});

function keypress(e) {
    if (e.key === 'Escape') {
       emit('closeModal')
    }
}

onMounted(() => {
    window.addEventListener('keydown', keypress)
    document.body.style['overflow-y'] = 'hidden'
})
onUnmounted(() => {
    window.removeEventListener('keydown', keypress)
    document.body.style['overflow-y'] = 'auto'
})
</script>

<template>
    <div @click="$emit('closeModal')" class="image-modal">
        <img :src="image" />
    </div>
</template>

<style scoped>
.image-modal {
    position: fixed;
    top: 0;
    width: 100vw;
    height: 100vh;
    background-color: #2c2c2cee;
    z-index: 10;
    cursor: url('/img/zoom-out.svg'), pointer;
    display: flex;
    justify-content: center;
    align-items: center;
}
.image-modal img {
    max-width: 90vw;
    max-height: 90vh;
}
</style>
