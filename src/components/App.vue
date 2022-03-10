<template>
	<div class="main-container">
		<main-header></main-header>
		<router-view></router-view>
	</div>
</template>

<script>
export default async function () {
	await globalComponents(
		`/components/controls/MainHeader.vue`,
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