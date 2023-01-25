<script setup>
defineProps({
    section: Object,
});
</script>

<template>
    <section>
        <div class="section-name">
            <span>{{ section.title }}</span>
        </div>
        <div class="section-content">
            <div v-for="item in section.items" :key="item.title" class="item">
                <div v-if="item.title" class="item-header">
                    <div class="item-title">{{ item.title }}</div>
                    <div class="item-sub-title">{{ item.subTitle }}</div>
                    <div class="dates" v-html="item.date"></div>
                </div>
                <div v-if="item.p || item.points" class="item-content">
                    <p v-for="(p, j) in item.p" v-html="p" :key="'p' + j" class="paragraph" />
                    <ul v-if="item.points" class="points">
                        <li v-for="(point, k) in item.points" v-html="point" :key="'point' + k" />
                    </ul>
                </div>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>
section {
    display: flex;
    gap: 10px;
    margin-bottom: 40px;
    opacity: 0.85;

    .section-name {
        width: 140px;
        text-align: right;
        font-weight: bold;
        font-size: 1.4rem;
        font-style: italic;
    }
    .section-content {
        padding-left: 20px;
        width: 100%;
        border-left: 1px solid #aaa;
        display: flex;
        flex-direction: column;
        gap: 20px;
        .item {
            display: flex;
            flex-direction: column;
            gap: 10px;
            .item-header {
                position: relative;
                .item-title {
                    font-size: 1.2rem;
                    font-weight: bold;
                    color: $color;
                }
                .item-sub-title {
                    color: #777;
                }
                .dates {
                    position: absolute;
                    font-style: italic;
                    font-size: 0.9rem;
                    top: 0;
                    right: 0;
                    color: $color;
                }
            }
            .item-content {
                .paragraph:not(:first) {
                    margin-top: 20px;
                }
                .paragraph:not(:last-child) {
                    margin-bottom: 20px;
                }
                .points:not(:first) {
                    margin-top: 20px;
                }
                .points:not(:last-child) {
                    margin-bottom: 20px;
                }
                .points {
                    margin-left: 20px;
                    li {
                        list-style-position: inside;
                    }
                }
                :deep(.quote) {
                    font-style: italic;
                    font-weight: 300;
                    border-left: 5px solid $color;
                    padding-left: 15px;
                }
            }
        }
    }
}
</style>
