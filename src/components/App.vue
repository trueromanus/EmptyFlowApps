<template>
	<div class="main-container">
		<main-header></main-header>
		<router-view></router-view>
		<main-footer></main-footer>
	</div>		
</template>

<script>
export default async function () {
	await globalComponents(
		`/components/controls/ActiveLink.vue`,
		`/components/controls/MainHeader.vue`,
		`/components/controls/AnchorsLink.vue`,
		`/components/controls/RequirementsTable.vue`,
		`/components/controls/Screenshots.vue`,
		`/components/controls/MainFooter.vue`,
		`/components/controls/DocumentationPreview.vue`
	);

	return {
		name: `RootComponent`
	}
};
</script>

<style>
.divider {
    flex: 1;
}
</style>