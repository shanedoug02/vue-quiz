<template>
	<div>
		<div>{{ quizData }}</div>
	</div>
</template>

<script>
export default {
	name: 'QuizChild',
	props: ['quizData'],
};
</script>
<style>
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}
</style>
