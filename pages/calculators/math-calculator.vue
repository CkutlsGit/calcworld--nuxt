<template>
  <section class="calculator m-12 flex justify-center font-montserrat font-semibold">
    <div class="calculator__content bg-gray-300 rounded-lg params-window-calculator p-8">
      <div class="calculator-params">
        <div class="calculator-param-first flex flex-col">
          <label>Первое число</label>
          <input class="input-style-default" type="number" v-model="paramsCalculator.firstParam">
        </div>
        <div class="calculator-param-action flex flex-col my-6">
          <label>Действие</label>
          <select class="select-style-default" v-model="paramsCalculator.actionParam">
            <option value="addition">Сложение (+)</option>
            <option value="subtraction">Вычитание (-)</option>
            <option value="multiplication">Умножение (*)</option>
            <option value="division">Деление (/)</option>
          </select>
        </div>
        <div class="calculator-param-second flex flex-col">
          <label>Второе число</label>
          <input class="input-style-default" type="number" v-model="paramsCalculator.secondParam">
        </div>
      </div>
      <div class="calculator-answer mt-6">
        <h1>{{ answer.toFixed(2) }}</h1>
      </div>
    </div>
  </section>
</template>

<script setup>
  const paramsCalculator = reactive({
    firstParam: '',
    secondParam: '',
    actionParam: ''
  })
  const answer = ref(0)

  watch(() => paramsCalculator, (newValue, oldValue) => {
    if (
        paramsCalculator.firstParam !== '' &&
        paramsCalculator.secondParam !== '' &&
        paramsCalculator.actionParam !== ''
    ) {
      switch (paramsCalculator.actionParam) {
        case 'addition':
          answer.value = paramsCalculator.firstParam + paramsCalculator.secondParam
          return
        case 'subtraction':
          answer.value = paramsCalculator.firstParam - paramsCalculator.secondParam
          return
        case 'multiplication':
          answer.value = paramsCalculator.firstParam * paramsCalculator.secondParam
          return
        case 'division':
          answer.value = paramsCalculator.firstParam / paramsCalculator.secondParam
          return
        default:
          answer.value = 'Ошибка при счете'
          return
      }
    }
  }, { deep: true })
</script>

<style scoped>

</style>