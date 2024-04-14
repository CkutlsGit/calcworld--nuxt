<template>
  <section class="calculator m-12 flex justify-center font-montserrat font-semibold">
    <div class="class=calculator__content bg-gray-300 rounded-lg params-window-calculator p-8">
      <div class="calculator-params">
        <div class="calculator-param__numbers">
          <h2>Введите цифры</h2>
          <p>Вводить либо процентное число(0-100) и обычное, или же два обычных</p>
          <div class="number-input mt-2">
            <input class="input-style-default mr-2" type="number" v-model="paramsCalculator.firstNumber">
            <input class="input-style-default ml-2" type="number" v-model="paramsCalculator.twoNumber">
          </div>
        </div>
        <div class="calculator-answer">
          <h2 class="my-2">Число соотвествующее {{ paramsCalculator.firstNumber }}% от числа {{ paramsCalculator.twoNumber }} - {{ answer.answerFirstQuestion.toFixed(2) }}</h2>
          <h2 class="my-2">% числа {{ paramsCalculator.firstNumber }} в другом числе {{ paramsCalculator.twoNumber }} - {{ answer.answerSecondQuestion.toFixed(2) }}%</h2>
          <h2 class="my-2">Прибавление % {{ paramsCalculator.firstNumber }} к числу {{ paramsCalculator.twoNumber }} - {{ answer.answerThirdQuestion.toFixed(2) }}</h2>
          <h2 class="my-2">Отнимание % {{ paramsCalculator.firstNumber }} от числа {{ paramsCalculator.twoNumber }} - {{ answer.answerFourthQuestion.toFixed(2) }}</h2>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
  const paramsCalculator = reactive({
    firstNumber: 60,
    twoNumber: 20
  })
  const answer = reactive({
    answerFirstQuestion: parseFloat(12),
    answerSecondQuestion: parseFloat(33.33),
    answerThirdQuestion: parseFloat(32),
    answerFourthQuestion: parseFloat(8)
  })

  const mathFunctions = {
    getAnswerforFirstQuestion() {
      const coefficient = paramsCalculator.twoNumber / 100

      return (coefficient * paramsCalculator.firstNumber).toFixed(2)
    },
    getAnswerforSecondQuestion() {
      const coefficient = paramsCalculator.twoNumber / paramsCalculator.firstNumber

      return (100 / coefficient).toFixed(2) + "%"
    },
    getAnswerforThirdQuestion() {
      const mathExample = (paramsCalculator.twoNumber / 100) * paramsCalculator.firstNumber

      return (mathExample + paramsCalculator.twoNumber).toFixed(2)
    },
    getAnswerforFourthQuestion() {
      const mathExample = (paramsCalculator.twoNumber / 100) * paramsCalculator.firstNumber

      return (paramsCalculator.twoNumber - mathExample).toFixed(2)
    }
  }

  watch(() => paramsCalculator, () => {
    if (
        paramsCalculator.firstNumber !== 0 && paramsCalculator.firstNumber !== '' &&
        paramsCalculator.twoNumber !== 0 && paramsCalculator.twoNumber !== ''
    ) {
      answer.answerFirstQuestion = parseFloat(mathFunctions.getAnswerforFirstQuestion())
      answer.answerSecondQuestion = parseFloat(mathFunctions.getAnswerforSecondQuestion())
      answer.answerThirdQuestion = parseFloat(mathFunctions.getAnswerforThirdQuestion())
      answer.answerFirstQuestion = parseFloat(mathFunctions.getAnswerforFirstQuestion())
    }
  }, { deep: true })
</script>

<style scoped>

</style>