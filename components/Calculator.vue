<!-- Inspired by https://www.youtube.com/watch?v=MRsDx3sFKOs and borrowed parts of the setup from this video-->

<template>
		<main>
		<div class="calculator">
			<div class="display">
				{{ display }}
			</div>
			<div class="buttons">
				<div class="button-row" v-for="row in buttonRows">
					<div
						@click="buttonClick(button)"
						class="button" 
						:class="
							{operator: button.type == 'operator'}, 
							{special: button.type == 'special'},
							{number: button.type == 'number'}"
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
		created() {
			window.addEventListener('keyup', this.handleWindowKeyUp)
		},

		methods: {
			handleWindowKeyUp(event) {
				switch(event.key) {

					/* 	number-keys	 */
					case '1':
						this.previousValue = 1;
						this.previousValue = Number(this.display);
						this.display += '1';
					break;

					case '2':
						this.previousValue = '2';
						this.previousValue = Number(this.display);
						this.display += '2';
					break;

					case '3':
						this.previousValue = '3';
						this.previousValue = Number(this.display);
						this.display += '3';
					break;

					case '4':
						this.previousValue = 4;
						this.previousValue = Number(this.display);
						this.display += '4';
					break;

					case '5':
						this.previousValue = 5;
						this.previousValue = Number(this.display);
						this.display += '5';
					break;

					case '6':
						this.previousValue = 6;
						this.previousValue = Number(this.display);
						this.display += '6';
					break;

					case '7':
						this.previousValue = 7;
						this.previousValue = Number(this.display);
						this.display += '7';
					break;

					case '8':
						this.previousValue = 8;
						this.previousValue = Number(this.display);
						this.display += '8';
					break;

					case '9':
						this.previousValue = 9;
						this.previousValue = Number(this.display);
						this.display += '9';
					break;

					case '0':
						this.previousValue = 0;
						this.previousValue = Number(this.display);
						this.display += '0';
					break;


					/* 	special-keys	 */

					/* 	empty display (Clear)	*/
					case 'Escape':
					case 'Backspace':
						this.display = '';
						this.previousValue = '';
					break;

					/* 	negate the displayed value	 +/- 	(⌥ -) */
					case '–':
						this.display *= -1;
					break;

					/*	 calculate what the given percentage of the number in the display is	*/
					case '%':
						this.display = (this.previousValue / 100) * this.display;
					break;

					/* 	Do not allow more than one . in a number	*/
					case '.':
						if (this.previousValue = '.' && this.display.includes('.')) return;
						this.previousValue = Number(this.display);
						this.display += '.';
					break;

					case 'Enter':
					this.display = this.operations[this.currentOperator](this.previousValue, this.display);
					break;

					// /*		Operators	 */
					// case '+':
					// 	this.display = this.operations(this.previousValue += this.display);
					}
			},

			buttonClick(button) {
				const previousValueAsNumber = Number(this.previousValue);
				const displayAsNumber = Number(this.display);
				const percentValueAsNumber = Number((this.previousValue / 100) * this.display);

				if (button.type == 'number') {
					if (this.previousValue === null) {
						this.previousValue = displayAsNumber;
						this.display = '';
					}
					if (button.text == '.' && this.display.includes('.')) return;
						this.display += button.text;
					} else if (button.text == 'C') {
						this.display = '';
						this.previousValue = '';
					} else if (button.text == 'CE') {
						this.display = this.previousValue;
					} else if (button.text == '+/-') {
						this.display *= -1;
					} else if (button.text == '%') {
						this.display = percentValueAsNumber;
					} else if (button.text == '=') {
						this.display = this.operations[this.currentOperator](previousValueAsNumber, displayAsNumber);
						this.currentOperator = '';
					} else if (button.type == 'operator') {
						 if (this.currentOperator) {
							this.display = this.operations[this.currentOperator](previousValueAsNumber, displayAsNumber);
						};
						this.previousValue = null;
						this.currentOperator = button.text;
				}
			},
		},
			data: () => ({
				display: '',
				previousValue: '',
				currentOperator: '',

				operations: {
					'÷': (a, b) => a / b,
					'×': (a, b) => a * b,
					'-': (a, b) => a - b,
					'+': (a, b) => a + b,
					// '%': (a, b) => (b / a) * 100,
				},

				buttonRows: [
					/* First row */
					[{ 
						text: 'C',
						type: 'special',
					}, {
						text: 'CE',
						type: 'special'
					}, {
						text: '+/-',
						type: 'special'
					}, { 
						text: '%',
						type: 'special'
					}, {
						text: '÷',
						type: 'operator'
					}],

					/* Second row */
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
						text: '×',
						type: 'operator'
					}],

					/* Third row */
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

					/* Forth row */
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
					
					/* Fifth row */
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
				],
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
	font-size: 20px;
}

.calculator {
	width: 250px;
	font-family: Georgia, 'Times New Roman', Times, serif;
	border-radius: 20px;
	overflow: hidden;
	background-color: lightgrey;
	padding: 0.8rem;
}

.display {
	height: 3rem;
	color: white;
	text-align: right;
	padding: 0.5em;
	background-color: darkgray;
	font-size: 1.5rem;
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
	padding: 0.2em;
	background-color: aquamarine;
}

.operator {
	background-color: cadetblue;
	color: white;
}

.button:active,
.button:hover {
	background-color: rgb(40, 145, 110);
	cursor: pointer;
}

</style>