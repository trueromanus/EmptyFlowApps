<template>
    <div class="screenshoots-container">
        <div class="screenshoots-content">
            <div class="screenshoots-header">
                {{ selectedItem.title }}
            </div>
            <div>
                <img
                    class="screenshoots-image"
                    :src="selectedItem.link"
                />
            </div>
            <div
                class="screenshoots-pages">
                <div
                    class="screenshoots-page"
                    :class="{'screenshoots-page-selected': index === selected}"
                    v-for="(_, index) in items"
                    :key="index"
                    @click="select(index)">
                    <span>{{ index + 1 }}</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
const { ref, computed }  = vueInstance;

export default {
    name: `Screenshots`,
    props: {
        items: {
            type: Array,
            required: true
        }
    },
    setup(props) {
        const selected = ref(0);

        const selectedItem = computed(() => {
            if (!props.items) return {};

            return props.items[selected.value];
        });

        function select(index) {
            if (selected.value === index) return;

            selected.value = index;
        }

        return {
            selected,
            select,
            selectedItem
        };
    }
}
</script>

<style>
.screenshoots-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
}
.screenshoots-content {
    max-width: 750px;
    width: 750px;
    display: flex;
    flex-direction: column;
    align-items: center;
}
.screenshoots-header {
    font-family: 'Roboto', sans-serif;
    font-size: 20px;
    margin-bottom: 10px;
}
.screenshoots-image {
    width: 700px;
    object-fit: contain;
}
.screenshoots-pages {
    display: flex;
    flex-direction: row;
    align-items: center;
}
.screenshoots-page {
    padding: 10px;
    font-family: 'Open Sans', sans-serif;
    background-color: antiquewhite;
    border-radius: 4px;
    margin-right: 8px;
}
.screenshoots-page:hover {
    background-color: lightgray;
}
.screenshoots-page-selected {
    background-color: cornflowerblue;
    color: white;
}
.screenshoots-page-selected:hover {
    background-color: cornflowerblue;
}

</style>