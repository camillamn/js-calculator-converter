<template>
	<main>
		<div>
			<section class="converter">
				{{ input }}, {{ output }}
				<input @input="handleInputChange" class="unit-converter__input" type="number" :placeholder="selectedOutputMetric" v-model="input">
				<select v-model="selectedOutputMetric">
					<option value="mm">mm</option>
					<option value="cm">cm</option>
					<option value="m">m</option>
					</select>
				</section>
		</div>

		<div>
			<section class="converter">
				{{ input }}, {{ output }}
				<input type="number" :placeholder="selectedOutputMetric">
				<select v-model="selectedOutputMetric">
					<option value="mm">mm</option>
					<option value="cm">cm</option>
					<option value="m">m</option>
				</select>
				</section>
		</div>


	</main>
</template>

<script>

</script>

<style>
</style>