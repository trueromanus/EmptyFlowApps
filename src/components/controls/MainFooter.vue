<template>
    <div class="main-footer-container">
        <div class="main-footer-content">
            <div class="main-footer-group-container">
                <div class="main-footer-group">Information</div>
                <a href="#">Blog</a>
                <a href="#">Subscribe</a>
            </div>
            <div class="main-footer-group-container">
                <div class="main-footer-group">Maintenance</div>
                <a href="#">Report a Bug</a>
                <a href="#">To suggest an idea</a>
            </div>
            <div class="main-footer-group-container">
                <div class="main-footer-group">Documentation</div>
                <a href="#">FAQ</a>
                <a href="#">Guides</a>
            </div>
            <div class="main-footer-group-container">
                <div class="main-footer-group">Social</div>
                <a href="#">Youtube</a>
                <a href="#">Telegram</a>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: `MainFooter`
}
</script>

<style>
.main-footer-container {
    width: 100%;
    height: 150px;
    background-color: rgba(204, 204, 204, .9);
    display: flex;
    font-family: 'Open Sans', sans-serif;
    justify-content: center;
}
.main-footer-content {
    width: 900px;
    display: flex;
    flex-direction: row;    
}
.main-footer-group-container {
    display: flex;
    flex-direction: column;
    font-size: 14px;
    flex: 1;
    margin-top: 18px;
}
.main-footer-group-container > * {
    margin-top: 10px;
}
.main-footer-group {
    font-size: 15px;
    font-weight: bold;
    margin-bottom: 8px;
}
.main-footer-group-container > a {
    text-decoration: none;
    color: black;
}
.main-footer-group-container > a:link {
    text-decoration: none;
    color: black;
}
.main-footer-group-container > a:visited {
    text-decoration: none;
    color: black;
}
.main-footer-group-container > a:hover {
    text-decoration: underline;
    color: black;
}
.main-footer-group-container > a:active {
    text-decoration: none;
    color: black;
}
</style>