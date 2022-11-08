<!-- https://www.youtube.com/watch?v=7l-ZAuU8TXc&t=364s -->

<template>
	<main>
		<h2>Unit-converter</h2>
		<div>
			<section class="converter">
				{{ input }}, {{ output }}
				<input @input="handleInputChange" class="unit-converter__input" type="number" :placeholder="selectedOutputMetric" v-model="input">
				<select v-model="selectedOutputMetric">
					<option value="mm">mm</option>
					<option value="cm">cm</option>
					<option value="m">m</option>
					<option value="km">km</option>
				</select>
				</section>
		</div>


	</main>
</template>

<script>

</script>

<style>
</style>