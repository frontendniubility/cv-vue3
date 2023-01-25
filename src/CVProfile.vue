<script setup>
import { profile } from '@/data.js';
</script>

<template>
    <section>
        <img v-bind:src="profile.image" />
        <h1>{{ profile.name }}</h1>
        <div class="data">
            <div v-for="item in profile.data" :key="item.label">
                <label>{{ item.label }}:</label>
                <span v-html="item.value"></span>
            </div>
        </div>
        <p class="quote">{{ profile.quote }}</p>
    </section>
</template>

<style lang="scss" scoped>
section {
    margin-bottom: 50px;
    opacity: 0.85;
}

h1 {
    margin-bottom: 1.6rem;
    border-bottom: 15px solid $color;
    border-image-slice: 1;
    border-image-source: linear-gradient(90deg,
        $gradient3 10%,
        $gradient2 50%,
        $gradient1 100%
    );
}
label {
    font-weight: 600;
    margin-right: 10px;
}
img {
    float: right;
    margin: -40px 50px 0;
    max-height: 280px;
}

.data {
    margin-bottom: 1.6rem;
}

.quote {
    color: $color-quote;
    font-style: italic;
    font-weight: 300;
    border-left: 5px solid $color;
    padding-left: 15px;
}
.email::after {
    display: none;
}
</style>
