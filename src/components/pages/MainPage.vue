 <template>
    <div class="mainpage-container">
        <div class="main-page-products-container">
            <div v-for="(item, index) in appList" :key="index" @click="$router.push('/apps/' + item.route)">
                <div class="main-page-app-title" :style="{'background-color': item.backgroundColor }">
                    <span>
                        {{ item.title }}
                        <span
                            v-if="item.branch !== 'stable'"
                            class="main-page-branch">
                            {{ item.branch }}
                        </span>
                    </span>
                    <image :src="'/assets/icons/' + item.icon" width="40" height="40" />
                </div>
                <div class="main-page-app-content">
                    {{ item.description }}
                </div>
                <div class="main-page-app-platforms">
                    <span>Platforms:</span>
                    <img
                        v-for="(platform, index) in item.platforms"
                        :src="'/assets/icons/' + platform + '.svg'"
                        :key="index"
                        width="30"
                        height="30"
                    />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default async function () {
    const appsResponse = await fetch(`/assets/apps.json`);
    const apps = await appsResponse.json();

    return {
        name: `MainPage`,
        data() {
            return {
                appList: apps
            }
        }
    }
}
</script>

<style>
.mainpage-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 20px;
    margin-bottom: 20px;
}
.main-page-products-container {
    display: grid;
    grid-template-columns: 300px 300px 300px;
    grid-gap: 10px;
}
.main-page-products-container > div {
    max-width: 240px;
    width: 240px;
}
.main-page-products-container > div:hover {
    box-shadow: 10px 10px 10px rgb(0, 0, 0, .5);
}
.main-page-app-title {
    height: 70px;
    display: flex;
    align-items: center;
    font-size: 18px;
    color: white;
    background-color: green;
    font-family: 'Open Sans', sans-serif;
    padding-left: 10px;
    display: flex;
    flex-direction: row;
}
.main-page-app-title > span {
    flex: 1;
}
.main-page-app-title > img {
    margin-right: 10px;
}
.main-page-app-content {
    background-color: white;
    height: 100px;
    padding: 10px;
    font-family: 'Roboto', sans-serif;
}
.main-page-app-platforms {
    display: flex;
    flex-direction: row;
    align-items: center;
    background-color: white;
    height: 40px;
    padding: 10px;
    font-family: 'Roboto', sans-serif;
}
.main-page-app-platforms > span {
    flex: 1;
}
.main-page-branch {
    font-size: 10px;
    padding: 4px;
    border-radius: 4px;
    background-color: #1c84c6;
    vertical-align: top;
}
</style>