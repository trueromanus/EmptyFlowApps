<template>
    <div class="documentation-container">
        <img src="/assets/icons/question.svg" width="50" height="50" />
    </div>
</template>

<script>
export default {
    name: `DocumentationPreview`,
    props: {
        documentation: {
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
    border: 1px solid lightgray;
    font-family: 'Open Sans', sans-serif;
}
</style>