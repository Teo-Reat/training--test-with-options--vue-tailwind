<template>
    <div>
        <transition name="flip" mode="out-in">
            <div class="card-question w-full bg-green-300 text-center mx-auto px-4 py-2 rounded-lg shadow-lg"
                 key="question"
                 v-if="question">
                <h3 class="mb-6 mt-8 text-2xl bg-green-800 text-white px-4 py-2 rounded-lg shadow">
                    {{ test.question }}
                </h3>
                <ul>
                    <li v-for="(option, index) in test.options" :key="index"
                        @click="checkAnswer(option)"
                        class="bg-white mb-2 cursor-pointer px-4 py-2 rounded-lg
                        hover:bg-green-800 hover:text-white shadow">
                        <span>{{ option }}</span>
                    </li>
                </ul>
            </div>
            <div class="card-answer w-full bg-red-300 text-center mx-auto px-4 py-2 rounded-lg shadow-lg"
                 :class="{ 'bg-green-300': result }"
                 @click="nextQuestion"
                 key="answer"
                 v-else>
                <h3 class="mb-6 mt-8 text-2xl bg-red-800 text-white px-4 py-2 rounded-lg shadow"
                    :class="{ 'bg-green-800': result }">
                    {{ result ? "Абсолютно правильно!" : "Эх ты... нет, ответ не верен." }}
                </h3>
<!--                <button @click="nextQuestion" class="bg-white text-black py-2 px-4 rounded shadow mt-16">-->
<!--                    Следующий вопрос-->
<!--                </button>-->
            </div>
        </transition>
    </div>
</template>

<script>
    export default {
        props: {
            test: {
                type: Object,
                required: true
            }
        },
        data() {
            return {
                question: true,
                result: null,
                elementWidth: 0
            }
        },
        methods: {
            checkAnswer(value) {
                this.question = !this.question;
                this.test.rightAnswer === value ? this.result = true : this.result = false
            },
            nextQuestion() {
                this.question = !this.question;
                setTimeout(this.$emit('next-question'), 1000)
                // this.$emit('next-question')
            },
        }
    }
</script>

<style scoped>
    /*flip*/
    .flip-enter {
        opacity: 0;
    }

    .flip-enter-active {
        animation: flip-in 1s ease-out forwards;
        /*transition: opacity .5s;*/
    }

    .flip-leave {
    }

    .flip-leave-active {
        animation: flip-out .5s ease-out forwards;
        /*transition: opacity 1s;*/
        /*opacity: 0;*/
    }

    .flip-move {
        transition: transform .5s;
    }

    @keyframes flip-in {
        from {
            /*transform: translateY(20px);*/
            /*transform: rotate(40deg);*/
            transform: rotate3d(0, 1, 0, 90deg);
        }
        to {
            /*transform: translateY(0);*/
            /*transform: rotate3d(0, 1, 0, 90deg);*/
        }
    }

    @keyframes flip-out {
        from {
            /*transform: rotate3d(0, 1, 0, 90deg);*/
        }
        to {
            transform: rotate3d(0, 1, 0, 90deg);
        }
    }
    .card-answer,
    .card-question {
        height: 440px;
    }
</style>