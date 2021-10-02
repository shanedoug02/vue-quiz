<template>
	<QuizChild :quizData="quizData" :currentQuestion="currentQuestion" @emittedSelection="setSelected" @evaluate="see" />
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
					answersArr: [
						{ option: 'Shopify', isCorrect: false, isSelected: false },
						{ option: 'WooCommerce', isCorrect: false, isSelected: false },
						{ option: 'ShopCommerce', isCorrect: true, isSelected: false },
						{ option: 'BigCommerce', isCorrect: false, isSelected: false },
					],
				},
				{
					question: 'If Shopify is so good, why are Shopify developers necessary?',
					answersArr: [
						{ option: 'To save time on things like store setups and migrations', isCorrect: false, isSelected: false },
						{ option: 'To extend the limited design options and functionalities of themes with custom code', isCorrect: false, isSelected: false },
						{
							option: 'To provide support with a deep understanding of how the platform works and what its limitations are',
							isCorrect: false,
							isSelected: false,
						},
						{ option: 'All the above', isCorrect: true, isSelected: false },
					],
				},
				{
					question: ' Which of the following is true about Shopify developers?',
					answersArr: [
						{ option: 'They are paid extremely well', isCorrect: false, isSelected: false },
						{ option: 'There is a high demand for them', isCorrect: false, isSelected: false },
						{
							option: 'They need to know web development, the platform itself, and the liquid template language',
							isCorrect: false,
							isSelected: false,
						},
						{ option: 'All the above', isCorrect: true, isSelected: false },
					],
				},
			],
			currentQuestion: 0,
			currentSelection: [],
			finalSelections: [],
			results: [],
		};
	},
	methods: {
		setSelected(payload) {
			for (let item of this.quizData) {
				for (let ans of item.answersArr) {
					ans.isSelected = false;
				}
			}
			payload.isSelected = true;
			if (payload.isSelected) {
				this.currentSelection.unshift(payload.option);
				console.log(this.currentSelection);
			}
		},
		see() {
			this.finalSelections.push(this.currentSelection[0]);
			this.currentQuestion++;
			console.log('finals', this.finalSelections);
		},
	},
};
</script>
<style></style>
