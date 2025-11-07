<template>
    <div>
        <NuxtLayout>
            <NuxtPage />
        </NuxtLayout>
    </div>
</template>

<script setup>
    const gameStore = useGameStore()

    // callOnce(() => {
    //     if (localStorage.getItem('questionIndex') != null) {
    //         gameStore.questionIndex = parseInt(localStorage.getItem('questionIndex'))
    //     }
    //     if (localStorage.getItem('chapterIndex') != null) {
    //         gameStore.chapterIndex = parseInt(localStorage.getItem('chapterIndex'))
    //     }
    //     if (localStorage.getItem('lineIndex') != null) {
    //         gameStore.lineIndex = parseInt(localStorage.getItem('lineIndex'))
    //     }
    //     if (localStorage.getItem('isMonitorOpen') != null) {
    //         gameStore.isMonitorOpen = localStorage.getItem('isMonitorOpen') === 'true'
            
    //     }
    // })
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Tiny5&display=swap');
    body {
        font-family: "Tiny5", sans-serif;
        font-weight: 400;
        font-style: normal;
        background-color: black;
        background-image:  linear-gradient(#011d04 0.1px, transparent 1px), linear-gradient(to right, #011d04 0.1px, transparent 1px);
        background-size: 30px 30px;
        margin: 0;
    }
</style>