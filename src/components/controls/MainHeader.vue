<template>
    <div class="main-header-container">
        <div class="main-header-content-container">
            <img src="/assets/icons/emptyflow.svg" width="30" height="30" />
            <a>EmptyFlow Software</a>
            <div class="divider"></div>
            <active-link
                title="Products"
                @link-pressed="$router.push(`/`)">
            </active-link>
            <active-link
                title="Support"
                @link-pressed="$router.push(`/support`)">
            </active-link>
            <active-link
                title="Learning"
                @link-pressed="$router.push(`/learning`)">
            </active-link>
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
    background-color: rgba(204, 204, 204, .9);
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
    align-items: center;
}
.main-header-content-container > img {
    margin-right: 10px;
}
.main-header-content-container > a {
    font-family: 'Open Sans', sans-serif;
}
.main-header-content-container > .active-link-container {
    margin-left: 10px;
}
</style>