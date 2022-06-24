<template>
    <div>
        <div class="documentation-content">
            <div class="documentation-header">
                {{ documentationPage.title }}
            </div>
            <div>
                <img src="/assets/icons/question.svg" width="50" height="50" />
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: `DocumentationPage`,
    data() {
        return {
            documentationPage: {}
        }
    }
}
</script>

<style>
 
</style>