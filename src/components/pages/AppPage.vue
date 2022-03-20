 <template>
    <div class="app-page-container">
        <span>{{ application.title }}</span>
    </div>
 </template>

<script>
export default {
    name: `AppPage`,
    data() {
        return {
            application: {}
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
.app-page-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 20px;
}
 </style>

 