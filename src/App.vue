<script setup>
import { reactive, computed } from 'vue';

const estado = reactive({
	numero1: 0,
	numero2: 0,
	operacao: 'adicao',
});

const resultado = computed(() => {
	const { numero1, numero2, operacao } = estado;

	switch (operacao) {
		case 'adicao':
			return numero1 + numero2;
		case 'subtracao':
			return numero1 - numero2;
		case 'multiplicacao':
			return numero1 * numero2;
		case 'divisao':
			if (numero2 === 0) {
				return 'Não é possível dividir por zero';
			}
			return numero1 / numero2;
		default:
			return 0;
	}
});
</script>

<template>
	<div class="calculator">
		<header>
			<h1>Calculadora Aritmética</h1>
		</header>
		<main>
			<div class="inputs">
				<input v-model.number="estado.numero1" type="number" placeholder="Número 1">
				<select v-model="estado.operacao">
					<option value="adicao">+ adição</option>
					<option value="subtracao">- subtração</option>
					<option value="multiplicacao">* multiplicação</option>
					<option value="divisao">/ divisão</option>
				</select>
				<input v-model.number="estado.numero2" type="number" placeholder="Número 2">
			</div>
			<p class="result">
				Resultado: {{ resultado }}
			</p>
		</main>
	</div>
</template>

<style scoped>
.calculator {
	padding: 20px;
}

.inputs {
	display: flex;
	justify-content: center;
	align-items: center;
	margin-top: 24px;
}
</style>