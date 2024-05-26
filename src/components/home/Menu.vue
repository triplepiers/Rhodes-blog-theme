<script setup lang="ts">
import SideBar from '@/components/home/menu/SideBar.vue'
import Main from '@/components/home/menu/Main.vue'
</script>

<template>
    <!-- 此处 active 为调试用，部署时需删除 -->
    <div class="section menu active">
        <SideBar />
        <Main />
    </div>
</template>

<style>
.menu {
    flex-direction: row !important;
    column-gap: 20px;
}

.basecard {
    flex: 1;
    height: 100%;
    border: 1px solid var(--light);
    padding: 5px 15px;
    background-color: rgba(0, 0, 0, .2);
    backdrop-filter: blur(3px);
    overflow-y: hidden;
}

.basecard .basecard-title {
    user-select: none;
    position: relative;
    width: 100%;
    color: var(--hilight);
    padding: 5px 0;
}

.basecard .basecard-title span {
    padding-left: 1rem;
    font-size: .8rem;
}

/* 部分下划线 */
.basecard .basecard-title::after {
    position: absolute;
    left: 0;
    bottom: -5px;
    content: "";
    display: block;
    background-color: var(--hilight);
    width: 200px;
    height: 5px;
}
</style>