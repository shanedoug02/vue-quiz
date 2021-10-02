<template>
	<div class="quiz-child-container">
		<div v-for="(item, idx) of quizData" :key="item">
			<div v-if="idx === currentQuestion">
				<h1>{{ item.question }}</h1>
				<div class="answers-container" v-for="answer of item.answersArr" :key="answer">
					<div @click="triggerSelected(answer)" class="check-box" :class="{ selected: answer.isSelected }"></div>
					{{ answer.option }}
				</div>
			</div>
		</div>
		<button @click="saveSelected">next</button>
	</div>
</template>

<script>
export default {
	name: 'QuizChild',
	props: ['quizData', 'currentQuestion'],
	methods: {
		triggerSelected(emitData) {
			this.$emit('selection', emitData);
		},
		saveSelected() {
			this.$emit('evaluate');
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
