<template>
    <div class="documentation-container">
        <div class="documentation-content">
            <div class="documentation-header">
                Documentation
            </div>
            <div>
                <img src="/assets/icons/question.svg" width="50" height="50" />
            </div>
            <div class="documentation-columns" v-if="items">
                <div class="documentation-right-align">
                    <div v-for="(leftitem, index) in items.leftColumn" :key="index">
                        <span>{{ leftitem.title }} </span>
                    </div>
                </div>
                <div class="documentation-left-align">
                    <div v-for="(rightitem, index) in items.rightColumn" :key="index">
                        <span>{{ rightitem.title }} </span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: `DocumentationPreview`,
    props: {
        items: {
            type: Object,
            required: true
        }
    }
}
</script>

<style>
.documentation-container {
    width: 90%;
    border-collapse: collapse;
    font-family: 'Open Sans', sans-serif;
    display: flex;
    justify-content: center;
}
.documentation-content {
    margin-top: 20px;
    margin-bottom: 20px;
    max-width: 750px;
    width: 750px;
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: white;
}
.documentation-header {
    font-family: 'Roboto', sans-serif;
    font-size: 20px;
    font-weight: bold;
    margin-top: 40px;
    margin-bottom: 18px;
}
.documentation-columns {
    display: flex;
    flex-direction: row;
}
.documentation-columns > div {
    margin-top: 10px;
    width: 200px;
    display: flex;
    flex-direction: column;
    justify-content: center;
}
.documentation-right-align {
    align-items: flex-end;
    margin-right: 10px;
}
.documentation-left-align {
    align-items: flex-start;
    margin-left: 10px;
}
</style>