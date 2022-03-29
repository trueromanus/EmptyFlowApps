<template>
    <div class="anchor-link-container">
        <div
            class="anchor-link-item"
            v-for="(item, index) in titles"
            :key="index"
            @click="selectItem(index)">
            <span :style="{'font-size': selected === index ? '16px' : '14px'}">
                {{ item }}
            </span>
        </div>
    </div>
</template>

<script>
const { ref }  = vueInstance;

export default {
    name: `AnchorsLink`,
    props: {
        titles: Array
    },
    setup() {
        const selected = ref(0);

        function selectItem(index) {
            selected.value = index;
        }

        return {
            selected,
            selectItem
        }
    }
}
</script>

<style>
.anchor-link-container {
    display: flex;
    flex-direction: row;
    align-items: center;
    font-family: 'Open Sans', sans-serif;
    font-weight: bold;
    font-size: 14px;
}
.anchor-link-item {
    margin-right: 20px;
    color: white;
    width: 100%;
    height: 40px;
    display: flex;
    align-items: center;
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: transparent;
}
.anchor-link-item:hover {
    border-top-color: azure;
}
</style>