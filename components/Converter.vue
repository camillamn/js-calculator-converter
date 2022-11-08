<template>
<!-- {{ selectedOutputMetric }} -->

<main>
	<h2>Length-converter</h2>
	<div class="container">
		<div v-for="length in lengthConvert">
			<label> {{length.id}} </label>
			<input 
				id:="length.id"
				type="number"
				v-model="length.input"
				@input="lengthConverter(length.id)">
		</div>
	</div>
</main>

</template>

<script>
	export default {
		data() {
			return {
				lengthConvert:[
					{
						id: 'Milimeter',
						input: '0'
					},
					{
						id: 'Centimeter',
						input: '0'
					},
					{
						id: 'Meter',
						input: '0'
					},
					{
						id: 'Kilometer',
						input: '0'
					},
				]
			}
		},

		methods: {
			lengthConverter(source) {
				let vm = this,
					milimeter = vm.lengthConvert[0],
					centimeter = vm.lengthConvert[1],
					meter = vm.lengthConvert[2],
					kilometer = vm.lengthConvert[3];

				if (source =='milimeter') {
					centimeter.input=(milimeter.input/10).toFixed(2);
					meter.input=(milimeter.input/100).toFixed(2);
					kilometer.input=(milimeter.input/10000).toFixed(2);
				}
				if (source =='centimeter') {
					milimeter.input=(centimeter.input*10).toFixed(2);
					meter.input=(centimeter.input/10).toFixed(2);
					kilometer.input=(centimeter.input/10000).toFixed(2);
				}
				if (source=='meter') {
					milimeter.input=(meter.input/10).toFixed(2);
					centimeter.input=(meter.input/100).toFixed(2);
					kilometer.input=(meter.input/10000).toFixed(2);
				};
				if (source=='kilometer') {
					milimeter.input=(kilometer.input/10).toFixed(2);
					centimeter.input=(kilometer.input/100).toFixed(2);
					meter.input=(kilometer.input/10000).toFixed(2);
				};
			}
		}
	}

</script>

<style>

body {
	height: 100vh;
}

.container {
	width: 30vw;
	font-family: Georgia, 'Times New Roman', Times, serif;
	border-radius: 20px;
	overflow: hidden;
	background-color: lightgrey;
	padding: 1em;
}

.input-box input {
	display: block;
	width: 100%;
	font-size: 1em;
	padding: 0.2em;
	margin-bottom: 0.2em;
}

.input-box label {
	display: block;
	font-size: 1em;
	margin-bottom: 0.2em;
}
</style>