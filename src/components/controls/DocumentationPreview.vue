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
                    <div
                        class="documentation-item-container"
                        v-for="(leftitem, index) in items.leftColumn"
                        :key="index">
                        <active-link
                            :title="leftitem.title"
                            text-decoration="none"
                            text-transform="none"
                            color="blue"
                            @link-pressed="$router.push(leftitem.route)">
                        </active-link>
                    </div>
                </div>
                <div class="documentation-left-align">
                    <div
                        class="documentation-item-container"
                        v-for="(rightitem, index) in items.rightColumn"
                        key="index">
                        <active-link
                            :title="rightitem.title"
                            color="blue"
                            text-decoration="none"
                            text-transform="none"
                            @link-pressed="$router.push(rightitem.route)">
                        </active-link>
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
    margin-bottom: 60px;
}
.documentation-columns > div {
    margin-top: 10px;
    width: 300px;
    display: flex;
    flex-direction: column;
    justify-content: center;
}
.documentation-right-align {
    align-items: flex-end;
    margin-right: 30px;
}
.documentation-left-align {
    align-items: flex-start;
    margin-left: 30px;
}
.documentation-item-container {
    margin-top: 10px;
}
</style>