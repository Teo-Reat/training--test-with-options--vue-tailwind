<template>
    <div id="app" class="w-1/5 mx-auto my-16">
        <app-card v-for="(test, index) in tests"
                  v-show="index === counter"
                  @next-question="counter++"
                  :test="test"
                  :key="index"/>
    </div>
</template>

<script>
    import Card from "./components/Card";

    export default {
        data() {
            return {
                counter: 0,
                tests: [
                    {
                        question: '2 + 2',
                        rightAnswer: 4,
                        options: [3, 4, 5, 6]
                    },
                    {
                        question: '3 + 3',
                        rightAnswer: 6,
                        options: [3, 4, 5, 6]
                    }
                ]
            }
        },
        components: {
            AppCard: Card
        }
    }
</script>

<style src="./css/tailwind.css"/>

<style>

</style>