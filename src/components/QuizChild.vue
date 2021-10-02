<template>
	<div v-if="currentQuestion < quizData.length" class="quiz-child-container">
		<div v-for="(item, idx) of quizData" :key="item">
			<div v-if="idx === currentQuestion">
				<h1>{{ item.question }}</h1>
				<div class="answers-container" v-for="answer of item.answersArr" :key="answer">
					<div @click="emitCurrentSelection(answer)" class="check-box" :class="{ selected: answer.isSelected }"></div>
					{{ answer.option }}
				</div>
			</div>
		</div>
		<button v-if="currentQuestion < quizData.length - 1" @click="emitFinalSelection">Next</button>
		<button v-else @click="emitFinalSelection">Submit</button>
	</div>
</template>

<script>
export default {
	name: 'QuizChild',
	props: ['quizData', 'currentQuestion'],
	methods: {
		emitCurrentSelection(emitData) {
			this.$emit('currentSelection', emitData);
		},
		emitFinalSelection() {
			this.$emit('finalSelection');
		},
	},
};
</script>
<style>
.quiz-child-container {
	margin: 1rem;
}

.answers-container {
	display: flex;
	align-items: center;
}

.check-box {
	height: 10px;
	width: 10px;
	outline: 1px solid rgb(209, 206, 206);
	margin-right: 10px;
}
.selected {
	background: cyan;
}
</style>
