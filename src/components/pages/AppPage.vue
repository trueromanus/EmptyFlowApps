 <template>
    <div>
        <div class="app-page-header-container" :style="{'background-color': application.backgroundColor}">
            <div class="app-page-header-content">
                <span class="app-page-header-title">{{ application.title }}</span>
                <anchors-link :titles="titles"></anchors-link>
            </div>
        </div>
    </div>
 </template>

<script>
export default {
    name: `AppPage`,
    data() {
        return {
            application: {},
            titles: [
                "Overview",
                "Requirements",
                "Features",
                "Screeshoots",
                "Documentation"
            ]
        }
    },
    async mounted() {
        const appName = this.$route.params.app;
        const response = await fetch(`/assets/${appName}.json`);
        this.application = await response.json();
    }
}
 </script>

 <style>
.app-page-header-container {
    height: 50px;
    width: 100%;
    display: flex;
    justify-content: center;
}
.app-page-header-content {
    width: 900px;
    display: flex;
    flex-direction: row;
    align-items: center;
}
.app-page-header-title {
    font-size: 18px;
    font-family: 'Roboto', sans-serif;
    font-weight: bold;
    color: white;
    margin-right: 30px;
}
 </style>

 