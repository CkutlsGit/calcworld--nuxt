<template>
  <section class="calculator m-12 flex justify-center font-montserrat font-semibold">
    <div class="class=calculator__content bg-gray-300 rounded-lg params-window-calculator p-8">
      <div class="calculator-info text-white">
        <h1 class="w-96 mb-1">Чтобы узнать сколько прошло дней нужно указать в конечной дате дату, с которой нужно узнать сколько прошло</h1>
        <p class="mb-4">Пример: Начальная 15.04.2024, конечная 30.12.2023 и в итоге прошло 107 дней</p>
      </div>
      <div class="calculator-params">
        <div class="calculator-start-data__param">
          <h2>Введите начальную дату</h2>
          <div class="param-inputs">
            <input class="input-style-default" type="date" v-model="calculatorParams.startData">
          </div>
        </div>
        <div class="calculator-end-data__param">
          <h2>Введите конечную дату</h2>
          <div class="param-inputs">
            <input class="input-style-default" type="date" v-model="calculatorParams.endData">
          </div>
        </div>
      </div>
      <div class="calculator-answer mt-4">
        <h2>{{ answer }} д.</h2>
      </div>
    </div>
  </section>
</template>

<script setup>
  const calculatorParams = reactive({
    startData: '',
    endData: ''
  })
  const answer = ref(0)

  watch(() => calculatorParams, () => {
    if (
        calculatorParams.startData !== '' &&
        calculatorParams.endData !== ''
    ) {
      const dataTypeObject = {
        startDataType: new Date(calculatorParams.startData),
        endDataType: new Date(calculatorParams.endData)
      }

      const secDifference = dataTypeObject.endDataType.getTime() - dataTypeObject.startDataType.getTime()

      answer.value = Math.ceil(secDifference / (1000 * 3600 * 24))
    }
  }, { deep: true })
</script>

<style scoped>

</style>