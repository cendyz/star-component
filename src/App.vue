<script setup lang="ts">
import { ref } from 'vue'
const stars: Record<number, string> = {
	0: "Excellent! We're thrilled to hear you had such a positive experience. Thank you for choosing our product/service",
	1: 'We apologize for the inconvenience you experienced. We appreciate your feedback and would like to work with you to address any issues.',
	2: "Thank you for your feedback. We're sorry to hear that your experience wasn't perfect. We would love to hear more about your concerns to see how we can improve.",
	3: "Thank you for your positive feedback! We're glad to know that you had a great experience and we appreciate your support.",
	4: "Excellent! We're thrilled to hear you had such a positive experience. Thank you for choosing our product/service.",
}

const num = ref(-1)
const right = ref(-1)

const desc = ref('')

const leftStar = (index: number): void => {
	desc.value = stars[index]
	right.value = -1
	num.value = index
}

const rightStar = (index: number): void => {
	desc.value = stars[index]
	right.value = index
	num.value = index
}
</script>
<template>
	<main class="box">
		<h1 class="title">
			How many stars would you give to our Online Code Editor?
		</h1>
		<div class="btnsBoxs">
			<button
				class="star"
				v-for="(_, index) in stars"
				:key="index"
				:class="{ selected: num === index }">
				<span
					class="leftStar"
					:class="{ selectedLeft: num === index }"
					@click="leftStar(index)"></span>
				<span
					class="rightStar"
					:class="{ selectedRight: right === index }"
					@click="rightStar(index)"></span>
			</button>
		</div>
		<p class="desc" v-text="desc"></p>
	</main>
</template>

<style lang="scss">
@use './sass/utilities/reset.scss';
@use './sass/Main.scss';

body {
	display: grid;
	place-items: center;
	font-family: 'Rubik', serif;
	font-size: 1.6rem;
	background-color: #333;
}
</style>
