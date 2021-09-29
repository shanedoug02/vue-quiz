<template>
	<QuizChild :quizData="quizData" />
</template>

<script>
import QuizChild from './QuizChild.vue';
export default {
	name: 'QuizParent',
	components: { QuizChild },
	data() {
		return {
			quizData: [
				{
					question: 'Which of the following is not a real eCommerce platform?',
					answersArr: ['Shopify', 'WooCommerce', 'ShopCommerce', 'BigCommerce'],
					correctAnswerIndex: 2,
				},
				{
					question: 'If Shopify is so good, why are Shopify developers necessary?',
					answersArr: [
						'To save time on things like store setups and migrations',
						'To extend the limited design options and functionalities of themes with custom code',
						'To provide support with a deep understanding of how the platform works and what its limitations are',
						'All the above',
					],
					correctAnswerIndex: 3,
				},
				{
					question: ' Which of the following is true about Shopify developers?',
					answersArr: [
						'They are paid extremely well',
						'There is a high demand for them',
						'They need to know web development, the platform itself, and the liquid template language',
						'All the above',
					],
					correctAnswerIndex: 3,
				},
			],
		};
	},
};
</script>
<style></style>
