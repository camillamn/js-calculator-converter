<!-- https://www.youtube.com/watch?v=XmIE_o-LenM  -->

<template>
	<main>
		<h4>Length-converter</h4>
		<div class="container">
			<div class="input-box">
				<label for="mm">Millimeter:</label>
				<input 
					type="number"
					id="mm"
					value="10">
			</div>
			<div class="input-box">
				<label for="cm">Centimeter:</label>
				<input 
					type="number"
					id="cm">
			</div>
			<div class="input-box">
				<label for="meter">Meter:</label>
				<input 
					type="number"
					id="m">
			</div>
			<div class="input-box">
				<label for="km">Kilometer:</label>
				<input 
					type="number"
					id="km">
			</div>

		</div>
	</main>
</template>

<script>


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