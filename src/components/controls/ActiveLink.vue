<template>
    <div
        class="active-link-container"
        :style="{'color': color, 'text-transform': textTransform, 'text-decoration': textDecoration }"
        @click="$emit('link-pressed')">
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
        },
        color: {
            type: String,
            default: _ => `black`
        },
        textTransform: {
            type: String,
            default: _ => `uppercase`
        },
        textDecoration: {
            type: String,
            default: _ => `underline`
        }
    }
};
</script>

<style>
.active-link-container {
    font-size: 18px;
    cursor: pointer;
}
</style>