 <template>
    <div>
        <div class="app-page-header-container" :style="{'background-color': application.backgroundColor}">
            <div class="app-page-header-content">
                <span class="app-page-header-title">{{ application.title }}</span>
                <anchors-link
                    :titles="titles"
                    @item-selected="sectionSelected($event)">
                </anchors-link>
                <a :href="application.githubLink">
                    <img
                        v-if="application.isOpenSource"
                        src="/assets/icons/github.svg"
                        width="30"
                        height="30"
                    />
                </a>
            </div>
        </div>       
        <div class="app-page-overview-container" ref="overview">
            <div class="app-page-overview-header-container">
                <div class="app-page-overview-application-title">
                    <img
                        :src="'/assets/icons/' + application.icon"
                        width="36"
                        height="36"
                    />
                    <span>
                        {{ application.title }}
                    </span>
                </div>
                <span>{{ application.description }}</span>
                <div class="app-page-overview-download">
                    <a :href="application.downloadLink" :style="{ 'background-color': application.backgroundColor }">Download</a>
                </div>
                <div class="app-page-overview-header-container-version">
                    <span>Latest version {{ latestVersion }} </span>
                    <span>Want to know what a changes in this version? Check out <a href="#">changelog</a></span>
                </div>
            </div>
            <div class="app-page-overview-youtube">
                <iframe
                    width="500"
                    height="300"
                    src="https://www.youtube.com/embed/EDOzl5hEprs"
                    title="YouTube video player"
                    frameborder="0"
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                    allowfullscreen>
                </iframe>
            </div>
        </div>
        <div class="app-page-requirements-container" ref="requirements">
            <div class="app-page-requirements-inner-container">
                <div class="app-page-requirements-header">
                    System Requirements
                </div>
                <div class="app-page-requirements-content">
                    <div>
                        <div class="app-page-requirements-subheader">
                            Minimal
                        </div>
                        <requirements-table
                            v-if="application.systemRequirements"
                            :requirements="application.systemRequirements.minimal">
                        </requirements-table>
                    </div>
                    <div>
                        <div  class="app-page-requirements-subheader">
                            Recommended
                        </div>
                        <requirements-table
                            v-if="application.systemRequirements"
                            :requirements="application.systemRequirements.recommended">
                        </requirements-table>
                    </div>
                </div>
                <div
                    v-if="application.systemRequirements"
                    class="app-page-requirements-oses">
                    <span>Supported operating systems:</span>
                    <div class="app-page-requirements-oses-item" v-for="(item, index) in application.systemRequirements.os" :key="index">
                        <img :src="'/assets/icons/' + item.icon" width="30" height="30" />
                        <div>
                            <span>{{ item.title }}</span>
                        </div>
                        <span>{{ item.bit }}</span>
                    </div>
                </div>
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
    },
    computed: {
        latestVersion() {
            if (!this.application.changelog) return "";
            const item = this.application.changelog[0];
            const date = new Date(item.date);
            return item.version + ` published ` + date.toUTCString();
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
    min-height: 680px;
    background-color: #fff;
    display: flex;
    flex-direction: column;
    align-items: center;
}
.app-page-overview-header-container {
    display: flex;
    flex-direction: column;
    text-align: center;
    max-width: 700px;
    width: 700px;
    margin-top: 40px;
    font-size: 17px;
    font-family: 'Open Sans', sans-serif;
}
.app-page-overview-youtube {
    margin-top: 20px;
}
.app-page-overview-header-container-version {
    margin-top: 20px;
    font-family: 'Roboto', sans-serif;
    font-size: 15px;
    display: flex;
    flex-direction: column;
}
.app-page-overview-header-container-version > span {
    margin-top: 8px;
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
.app-page-requirements-container {
    background-image: url(/assets/requirements-background.jpg);
    background-position: top center;
    display: flex;
    justify-content: center;
}
.app-page-requirements-inner-container {
    width: 900px;
    background-color: white;
    display: flex;
    margin-top: 60px;
    margin-bottom: 60px;
    flex-direction: column;
}
.app-page-requirements-content {
    display: flex;
    flex-direction: row;
}
.app-page-requirements-content > div {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
}
.app-page-requirements-header {
    display: flex;
    justify-content: center;
    font-family: 'Roboto', sans-serif;
    font-size: 22px;
    font-weight: bold;
    margin-top: 20px;
    margin-bottom: 20px;
}
.app-page-requirements-subheader {
    display: flex;
    justify-content: center;
    font-family: 'Roboto', sans-serif;
    font-size: 16px;
    font-weight: bold;
    margin-bottom: 10px;
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
.app-page-requirements-oses {
    font-family: 'Roboto', sans-serif;
    font-size: 18px;
    font-weight: bold;
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 20px;
    margin-bottom: 40px;
}
.app-page-requirements-oses-item {
    font-size: 16px;
    width: 400px;
    display: flex;
    flex-direction: row;
    align-items: center;
    margin-top: 10px;
}
.app-page-requirements-oses-item >:nth-child(2) {
    flex: 1;
    padding-left: 10px;
    padding-right: 10px;
    display: flex;
    flex-direction: row;
    justify-content: center;
}
.app-page-requirements-oses-item > span {
    margin-right: 10px;
}
.app-page-overview-application-title {
    font-size: 34px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    margin-bottom: 10px;
}
.app-page-overview-application-title > img {
    margin-right: 10px;
}
.app-page-overview-download {
    font-size: 18px;
    margin-top: 20px;
}
.app-page-overview-download > a {
    color: white;
    padding: 10px;
}
.app-page-overview-download > a:hover {
    color: white;
}
 </style>

 