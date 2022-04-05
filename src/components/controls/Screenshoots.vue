<template>
    <div class="screenshoots-container">
        <div class="screenshoots-content">

        </div>
    </div>
</template>

<script>
export default {
    name: `Screenshoots`
}
</script>

<style>
.screenshoots-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
}
.screenshoots-content {
    max-width: 500px;
    width: 500px;
    display: flex;
    flex-direction: row;
    align-items: center;
}
</style>