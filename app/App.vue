<template>
	<Calculator/>
	<Converter/>
</template>

<script>
	import Calculator from '../components/Calculator.vue'
	import Converter from '../components/Converter.vue'

	export default {
		components: {
			Calculator,
			Converter
		}
	}
</script>

<style>
* {
	box-sizing: border-box;
	padding: 0;
	margin: 0;
}

</style>