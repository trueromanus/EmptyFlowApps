<template>
    <div class="main-header-container">
        <div class="main-header-content-container">
            <span>EmptyFlowApps</span>
            <div class="divider"></div>
            <span>Products</span>
            <span>Support</span>
        </div>
    </div>
</template>

<script>
export default {
    name: `MainHeader`
};
</script>

<style>
.main-header-container {
    width: 100%;
    height: 60px;
    background-color: #cccccc;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
}
.main-header-content-container {
    max-width: 900px;
    width: 900px;
    display: flex;
    flex-direction: row;
}
</style>