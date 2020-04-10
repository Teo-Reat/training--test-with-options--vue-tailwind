<template>
    <div>
        <transition>
            <div class="card-question w-full bg-green-300 text-center mx-auto px-4 py-2" v-if="question">
                <h3>{{ test.question }}</h3>
                <hr class="mb-6">
                <ul>
                    <li v-for="(option, index) in test.options" :key="index"
                        @click="checkAnswer(option)"
                        class="bg-green-200 mb-2 cursor-pointer">
                        <span>{{ option }}</span>
                    </li>
                </ul>
                <hr>
            </div>
            <div class="card-answer w-full bg-red-300 text-center mx-auto px-4 py-2"
                 :class="{'bg-green-300': result}"
                 v-else>
                <span>{{ result }}</span>
                <hr>
                <button @click="nextQuestion">Next question</button>
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
                result: null
            }
        },
        methods: {
            checkAnswer(value) {
                this.question = !this.question;
                if (this.test.rightAnswer === value) {
                    this.result = true
                } else {
                    this.result = false
                }
            },
            nextQuestion() {
                this.$emit('next-question')
            }
        }
    }
</script>

<style scoped>

</style>