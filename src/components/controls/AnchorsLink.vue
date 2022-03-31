<template>
    <div class="anchor-link-container">
        <div
            class="anchor-link-item"
            :class="{ 'anchor-link-item-seleted': selected === index }"
            v-for="(item, index) in titles"
            :key="index"
            @click="selectItem(index, item)">
            <span :style="{'font-size': selected === index ? '16px' : '14px'}">
                {{ item.title }}
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
    emits: [`item-selected`],
    setup() {
        const selected = ref(0);

        function selectItem(index, item) {
            selected.value = index;
            this.$emit(`item-selected`, item);
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
    height: 43px;
    display: flex;
    align-items: center;
    border-top-style: solid;
    border-top-width: 3px;
    border-bottom-style: solid;
    border-bottom-width: 4px;
    border-top-color: transparent;
    border-bottom-color: transparent;
}
.anchor-link-item:hover {
    border-top-color: azure;
}
.anchor-link-item-seleted {   
    border-bottom-color: white;
}
</style>