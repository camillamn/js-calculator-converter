<!-- Inspired by https://www.youtube.com/watch?v=8ypiRFlXZG4  -->
<template>

<main>
	<div class="title">Metric-converter</div>
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
						id: 'Millimeter',
						input: 0
					},
					{
						id: 'Centimeter',
						input: 0
					},
					{
						id: 'Decimeter',
						input: 0
					},
					{
						id: 'Meter',
						input: 0
					},
				]
			}
		},

		methods:{
			lengthConverter(source) {
				let inputNumber = this,
					millimeter = inputNumber.lengthConvert[0],
					centimeter = inputNumber.lengthConvert[1],
					decimeter = inputNumber.lengthConvert[2],
					meter = inputNumber.lengthConvert[3]

				if (source == 'Millimeter') {
					centimeter.input=(millimeter.input/10);
					decimeter.input=(millimeter.input/100);
					meter.input=(millimeter.input/1000);
				} else
				if (source == 'Centimeter') {
					millimeter.input=(centimeter.input*10);
					decimeter.input=(centimeter.input/10);
					meter.input=(centimeter.input/100);
				} else
				if (source == 'Decimeter') {
					millimeter.input=(decimeter.input*100);
					centimeter.input=(decimeter.input*10);
					meter.input=(decimeter.input/10);
				} else
				if (source == 'Meter') {
					millimeter.input=(meter.input*1000);
					centimeter.input=(meter.input*100);
					decimeter.input=(meter.input*10);
				}
			}
		}
	}

</script>

<style>

body {
	width: 100vw;
	height: 100vh;
	display: flex;
	justify-content: center;
	align-items: center;
}

input {
	display: block;
	width: 100%;
	font-size: 1rem;
	padding: 0.2rem;
	margin-bottom: 0.2rem;
}

.title {
	font-size: 1.3em;
	display: flex;
	justify-content: center;
}

.container {
	width: 250px;
	font-family: Georgia, 'Times New Roman', Times, serif;
	border-radius: 20px;
	overflow: hidden;
	background-color: lightgrey;
	padding: 1em;
}


</style>