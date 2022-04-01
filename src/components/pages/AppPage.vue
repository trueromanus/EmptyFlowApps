 <template>
    <div>
        <div class="app-page-header-container" :style="{'background-color': application.backgroundColor}">
            <div class="app-page-header-content">
                <span class="app-page-header-title">{{ application.title }}</span>
                <anchors-link
                    :titles="titles"
                    @item-selected="sectionSelected($event)">
                </anchors-link>
            </div>
        </div>
        <div class="app-page-overview-container" ref="overview">
            <div class="app-page-overview-header-container">
                <span>{{ application.description }}</span>
            </div>
        </div>
        <div class="app-page-features-container" ref="features">
            <div class="app-page-features-content">
                <div class="app-page-features-header">
                    <span>{{ application.title }} features:</span>
                </div>               
                <div class="app-page-features-items">
                    <div
                        v-for="(item, index) in application.features"
                        :key="index"
                        class="app-page-features-item">
                        <div class="app-page-features-item-icon">
                            <img
                                :src="'/assets/icons/' + item.icon"
                                width="80"
                                height="80"
                            />
                        </div>
                        <span class="app-page-features-item-title">
                            {{ item.title }}
                        </span>
                        <span class="app-page-features-item-description">
                            {{ item.description }}
                        </span>
                    </div>
                </div>
            </div>
        </div>
        <div class="app-page-documentation-container" ref="docs">
            <span>{{ application.description }}</span>
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
                {
                    title: "Overview",
                    anchor: "overview"
                },
                {
                    title: "Requirements",
                    anchor: "requirements"
                },
                {
                    title: "Features",
                    anchor: "features"
                },
                {
                    title: "Screeshoots",
                    anchor: "screeshoots"
                },
                {
                    title: "Documentation",
                    anchor: "docs"
                }
            ]
        }
    },
    async mounted() {
        const appName = this.$route.params.app;
        const response = await fetch(`/assets/${appName}.json`);
        this.application = await response.json();
    },
    methods: {
        sectionSelected(item) {
            this.$refs[item.anchor].scrollIntoView({ behavior: `smooth` });
        }
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
.app-page-overview-container {
    background-image: url(/assets/white-background.png);
    background-position: top center;
    min-height: 700px;
    background-color: #fff;
    display: flex;
    justify-content: center;
}
.app-page-overview-header-container {
    text-align: center;
    width: 700px;
    margin-top: 20px;
    font-size: 16px;
    font-family: 'Open Sans', sans-serif;
}
.app-page-features-container {
    background-image: url(/assets/feature-background.avif);
    background-position: top center;
    display: flex;
    justify-content: center;
}
.app-page-features-content {
    width: 900px;
    font-size: 22px;
    font-weight: bold;
    background: white;
    font-family: 'Roboto', sans-serif;
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 60px;
    margin-bottom: 60px;
}
.app-page-features-header {
    width: 100%;
    margin-top: 30px;    
    display: flex;
    justify-content: center;
}
.app-page-documentation-container {
    background-image: url(/assets/documentation-background.jfif);
    background-position: top center;
    min-height: 800px;
    display: flex;
    justify-content: center;
}
.app-page-features-items {
    width: 100%;
    display: grid;
    grid-template-columns: 300px 300px 300px;
    grid-gap: 10px;
    padding-top: 50px;
    margin-left: 50px;
}
.app-page-features-item {
    width: 230px;
    height: 220px;
    display: flex;
    flex-direction: column;
}
.app-page-features-item-icon {
    margin-top: 8px;
    display: flex;
    justify-content: center;
    margin-bottom: 10px;
}
.app-page-features-item-title {
    margin-top: 10px;
    display: flex;
    justify-content: center;
    font-size: 15px;
    padding: 4px;
}
.app-page-features-item-description {
    font-size: 12px;
    text-align: justify;
    padding: 4px;
}
 </style>

 