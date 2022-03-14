<template>
    <div class="active-link-container" @click="$emit('link-pressed')">
        {{ title }}
    </div>
</template>

<script>
export default {
    name: `ActiveLink`,
    props: {
        title: {
            type: String,
            required: true
        }
    }
};
</script>

<style>
.active-link-container {
    color: black;
    font-size: 18px;
    text-decoration: underline;
    text-transform: uppercase;
    cursor: pointer;
}
</style>