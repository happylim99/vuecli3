<template>
	<div>
		<div class="row">
			<div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3">
				<h2 class="text-center">The Super Quiz</h2>
			</div>
		</div>
		<div class="row">
			<div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3">
				<transition name="flip" mode="out-in">
					<component :is="mode" @answered="answered($event)" @confirmed="mode = 'app-question'" />
				</transition>
			</div>
		</div>

	</div>
</template>

<script>
import Question from '../components/QuestionAnswer/Question.vue'
import Answer from '../components/QuestionAnswer/Answer.vue'
export default {
	data() {
		return {
			mode: 'app-question'
		}
	},

	methods: {
		answered(isCorrect) {
			if(isCorrect) {
				this.mode = 'app-answer'
			} else {
				this.mode = 'app-question'
				alert('Wrong, try again');
			}
		}
	},

	components: {
		appQuestion: Question,
		appAnswer: Answer
	}
}
</script>

<style scoped>
	.flip-enter {
		/* transform: rotateY(0deg); */
	}
	.flip-enter-active {
		animation: flip-in 0.5s ease-out forwards;
	}
	.flip-leave {
		/* transform: rotateY(90deg); */
	}
	.flip-leave-active {
		animation: flip-out 0.5s ease-out forwards;
	}
	@keyframes flip-out {
		from {
			transform: rotateY(0deg);
		}
		to {
			transform: rotateY(90deg);
		}
	}
	@keyframes flip-in {
		from {
			transform: rotateY(90deg);
		}
		to {
			transform: rotateY(0deg);
		}
	}
</style>