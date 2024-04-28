<template>
    <div>
        <UModal v-model="modalIsOpen" class="fixed" prevent-close>
            <UCard :ui="{ ring: '', divide: 'divide-y divide-gray-100 dark:divide-gray-800' }">
                <div class="flex items-center justify-center flex-col">
                    <div class="h-32 text-6xl">🖕😀🖕</div>
                    <a href="https://www.bilibili.com/video/BV1wC411j7nj/" target="_blank">
                        <div class="m-4 hover:text-red-500">
                            <span class="text-gray-400">10 分钟循环</span>
                            <Icon name="iconamoon:link-external" color="gray" size="24" class="mx-2"/>
                        </div>
                    </a>
                    <UButton @click="play" :disabled="buttonIsLoading" class="text-2xl align-baseline">👍👍👍</UButton>
                </div>
            </UCard>
        </UModal>
        <div class="h-screen w-screen overflow-hidden">
            <video ref="videoRef" loop class="min-h-screen min-w-full object-cover">
                <source src="/video.mp4" type="video/mp4">
                Your browser does not support the video tag.
            </video>
        </div>

        <audio ref="audioRef" class="hidden" loop>
            <source src="/audio.MP3" type="audio/mpeg">
            Your browser does not support the audio tag.
        </audio>
    </div>
</template>

<script setup>
import {onMounted, ref} from 'vue';

useHead({
    title: '🖕是谢谢的意思',
});

const videoRef = ref(null);
const audioRef = ref(null);
const modalIsOpen = ref(true);
const buttonIsLoading = ref(true)

function play() {
    videoRef.value.play();
    audioRef.value.play();
    modalIsOpen.value = false
}

onMounted(() => {
    buttonIsLoading.value = false
});
</script>

<style scoped>
</style>
