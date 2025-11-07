<template>
    <div class="background" id="background" :style="backImage"></div>

</template>

<script setup>
    const gameStore = useGameStore()

    const backImage = computed(() => ({
        background: `url("/images/${gameStore.chapters[gameStore.chapterIndex][gameStore.lineIndex].background}.jpg") no-repeat center/cover`
    }))
</script>

<style scoped>
    .background {
        background-size: cover;
        background-position: center;
    }
</style>