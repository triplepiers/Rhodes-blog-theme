<script setup lang="ts">
import { getCurrentInstance, onMounted } from 'vue';

import { SideBarHandler } from '@/tools/menu.js';
import data from '@/data/data.js';

onMounted(() => {
    const sideBarHandler = new SideBarHandler(
        '.menu .basecard.sideBar',
        '.basecard.sideBar ul.menu',
        '.menu .basecard.main .basecard-title',
        data['menu']
    );

    sideBarHandler.init();
    window.addEventListener('resize', () => {
        sideBarHandler.isSideBarFold(); // 判断侧边目录是否展开
    })
})
</script>

<template>
    <div class="basecard sideBar">
        <div class="basecard-title">目录<span>Menu</span></div>
        <ul class="menu"></ul>
    </div>
</template>


<style>
.basecard.sideBar {
    flex: 0 0 230px;
    transition: flex .3s;
}

.basecard.sideBar[fold] {
    flex: 0 0 0px;
    padding: 0;
    border: 0px solid transparent;
    overflow: hidden;
}

.basecard.sideBar[fold] * {
    opacity: 0;
}

.basecard.sideBar ul.menu {
    margin-top: 10px;
    width: 100%;
    height: 100%;
    list-style-type: none;
    color: var(--light);
    font-size: .9em;
    font-weight: 300;
    display: flex;
    flex-direction: column !important;
}

.basecard.sideBar ul.menu li {
    width: fit-content;
    pointer-events: none;
    user-select: none;
    margin: 5px 0;
    height: calc(1rem + 8px);
    display: flex;
    align-items: center;
    /* 常态下不显示 */
    opacity: 0;
    transform: translateX(70%);
    transition: .3s;
    transition-delay: 0s;
}


/* menu Unfold 时显现 */
.basecard.sideBar ul.menu.unfold li {
    pointer-events: all;
    transition-delay: calc(var(--i) * .1s);
    opacity: 1;
    transform: translateX(0%);
}

.basecard.sideBar ul.menu li .text {
    position: relative;
}

/* 当前选中的一级菜单 */
.basecard.sideBar ul.menu li .text::after {
    content: "";
    display: block;
    position: absolute;
    width: 0%;
    height: 2px;
    background-color: var(--hilight);
    transition: width .6s;
}

.basecard.sideBar ul.menu li[active] .text::after {
    width: 100%;
}

/* 英文标题 */
.basecard.sideBar ul.menu li span {
    padding-left: 1em;
    font-size: .8em;
}

/* hover */
.basecard.sideBar ul.menu li:hover .hover {
    margin-right: .5em;
    width: 1em;
}

.basecard.sideBar ul.menu li .hover {
    display: inline-block;
    height: 100%;
    background-color: var(--hilight);

    margin-right: 0;
    width: 0;
    transition: .3s;
}
</style>