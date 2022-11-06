<template>
		<main>
		<h2>Kalkulator</h2>
		<div class="calculator">
			<div class="display">
				{{ display }}
			</div>
			<div class="buttons">
				<div class="button-row" v-for="row in buttonRows">
					<div
						@click="buttonClick(button)"
						:class="{operator: button.type == 'operator'}, {special: button.type == 'special'}"
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
		// created() {
		// 	window.addEventListener('keyup', this.handleKeyup);
		// },
		methods: {
			buttonClick(button) {
				if(button.type == 'number') {
					if (this.previousValue === null) {
						this.previousValue = Number(this.display);
						this.display = '';
					}
					if (button.text == '.' && this.display.includes('.')) return;
					this.display += button.text;
				} else if (button.text == 'C') {
					this.display = '';
				} else if (button.text == '+/-') {
					this.display *= -1;
				} else if (button.text == '%') {
					this.display /= 100;
				} else if (button.text == '=') {
					this.display = this.operations[this.currentOperator](+this.previousValue, +this.display);
					this.currentOperator = '';
				} else if (button.type == 'operator') {
					if (this.currentOperator) {
						this.display = this.operations[this.currentOperator](+this.previousValue, +this.display);
					};
					this.previousValue = null;
					this.currentOperator = button.text;
				}
			}
		},
		// clearResult() {
		// 		this.sequence = '';
		// 		this.total = 0;
		// 		this.showingResult = false;
		// 	},

		// 	calculateResult() {
		// 		this.total = eval(this.sequence)
		// 	},
			
		// 	handleInput(input) {
		// 		this.sequence += input;
		// 	},
			
			// showResult() {
			// 	this.calculateResult();
			// 	this.showingResult = true;
			// },
		// handleKeyup(event) {
		// 		switch(event.key) {
		// 			case '0':
		// 			case '1':
		// 			case '2':
		// 			case '3':
		// 			case '4':
		// 			case '5':
		// 			case '6':
		// 			case '7':
		// 			case '8':
		// 			case '9':
		// 				this.handleInput(event.key)
		// 				break;
		// 			case '+':
		// 			case '-':
		// 			case '/':
		// 			case '*':
		// 				this.handleOperatorInput(event.key)
		// 				break;
		// 			case '.':
		// 			case ',':
		// 				this.handleInput('.')
		// 				break;
		// 			case '=':
		// 			case 'Enter':
		// 				this.handleEqualsInput()
		// 				break;
		// 			case 'Escape':
		// 			case 'Backspace':
		// 				this.clearResult()
		// 				break;
		// 		}
		// 	},
		data: () => ({
			display: '',
			previousValue: '',
			currentOperator: '',
			operations: {
				'÷': (a, b) => a / b,
				'×': (a, b) => a * b,
				'-': (a, b) => a - b,
				'+': (a, b) => a + b,
			},
			buttonRows: [
				[{ 
					text: 'C',
					type: 'special',
					case: 'Escape'
				}, {
					text: '+/-',
					type: 'special'
				}, { 
					text: '%',
					type: 'operator'
				}, {
					text: '÷',
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
					text: '×',
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