<template>
		<main>
		<h1>Kalkulator</h1>
		<div class="calculator">
			<div class="display">
				{{ display }}
			</div>
			<div class="buttons">
				<div class="button-row" v-for="row in buttonRows">
					<div
						@click="buttonClick(button)"
						:class="{operator: button.type == 'operator'}"
						class="button" 
						v-for="button in row">
						{{ button.text }}
					</div>
				</div>
			</div>
		</div>
	</main>
</template>

<script>
	export default {
		methods: {
			buttonClick(button) {
				if(button.type == 'number') {
					this.display += button.text;
				} else if (button.text == 'C') {
					this.display = '';
				}
			}
		},
		data: () => ({
			display: '',
			buttonRows: [
				[{ 
					text: 'C',
					type: 'special'
				}, {
					text: '()',
					type: 'special'
				}, { 
					text: '%',
					type: 'special'
				}, {
					text: '/',
					type: 'operator'
				}],
				[{ 
					text: '1',
					type: 'number'
				}, {
					text: '2',
					type: 'number'
				}, { 
					text: '3',
					type: 'number'
				}, {
					text: '*',
					type: 'operator'
				}],
				[{ 
					text: '4',
					type: 'number'
				}, {
					text: '5',
					type: 'number'
				}, { 
					text: '6',
					type: 'number'
				}, {
					text: '-',
					type: 'operator'
				}],
				[{ 
					text: '7',
					type: 'number'
				}, {
					text: '8',
					type: 'number'
				}, { 
					text: '9',
					type: 'number'
				}, {
					text: '+',
					type: 'operator'
				}],
				[{ 
					text: '0',
					type: 'number'
				}, {
					text: '.',
					type: 'number'
				}, { 
					text: '=',
					type: 'operator'
				}]
			]
		})
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

.calculator {
	width: 30vw;
	font-family: Georgia, 'Times New Roman', Times, serif;
	border-radius: 20px;
	overflow: hidden;
	background-color:bisque
}

.display {
	height: 2em;
	color: white;
	text-align: right;
	padding: 0.5em;
	border-radius: 5%;
	background-color: darkgray;
	font-size: 1.5em;
}

.buttons {
text-align: center;
}

.button-row {
	display: flex;
	justify-content: space-around;
}

.button {
	display: inline-block;
	border: 1px solid gray;
	border-radius: 25%;
	margin: 0.2em;
	width: 100%;
	padding: 0.5em;
	background-color: aquamarine;
}

.operator {
	background-color: cadetblue;
	color: white;
}

.button:active,
.button:hover {
	background-color: rgb(40, 145, 110);
}

</style>