<template>
    <div id="app" class="w-1/4 mx-auto my-16">
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
                        question: 'Самое большое современное млекопитающее:',
                        rightAnswer: 'Кит',
                        options: ['Жираф', 'Гигантский ленивец', 'Кит', 'Слон']
                    },
                    {
                        question: 'Автора романа "Война и мир" звали:',
                        rightAnswer: 'Лев',
                        options: ['Кот', 'Лев', 'Алексей', 'Вениамин']
                    },
                    {
                        question: 'Самая длинная река мира:',
                        rightAnswer: 'Нил',
                        options: ['Нил', 'Янцзы', 'Амазонка', 'Енисей', ]
                    },
                    {
                        question: 'На чем стоит плоский мир?',
                        rightAnswer: 'На трёх китах',
                        options: ['На руках атлантов', 'На страшной женщине', 'На яйцах утки', 'На трёх китах', ]
                    },
                    {
                        question: 'Что изображено на флаге пиратов?',
                        rightAnswer: 'Череп',
                        options: ['Змей', 'Перевернутый крест', 'Череп', 'Серп и молот', ]
                    },
                    {
                        question: '',
                        rightAnswer: '',
                        options: ['', '', '', '', ]
                    },
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