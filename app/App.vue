<template>
	<main>
		<h1>Kalkulator</h1>
		<div class="calculator">
			<div class="display"></div>
		</div>
	</main>
</template>

<script>

</script>

<style scoped>
	.calculator {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		grid-auto-rows: minmax(50px, auto);
	}

	.display {
		grid-column: 1 / 5;
		background-color: aquamarine;
	}
</style>