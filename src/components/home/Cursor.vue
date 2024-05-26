<script setup lang="ts">
import { onMounted } from 'vue';

onMounted(() => {
    const cursors = [
        "#cursor-inner",
        // "#cursor-outter"
    ].map((tag) => { return document.querySelector(tag); });

    window.addEventListener('mousemove', (e) => { // 移动 cursor
        let { clientX, clientY } = e;
        cursors.forEach((cursor) => {
            cursor.style.left = `${clientX}px`;
            cursor.style.top = `${clientY}px`;
        })
    })
})
</script>

<template>
    <div id="cursor-inner"></div>
    <!-- <div id="cursor-outter"></div> -->
</template>

<style>
/* 鼠标指针 */
#cursor-inner {
    pointer-events: none;
    z-index: 999;
    background-color: #fff;
    width: 5px;
    height: 5px;
    border-radius: 50%;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}
</style>