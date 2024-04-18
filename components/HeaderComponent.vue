<template>
  <header class="header bg-header">
    <div class="header__content flex items-center justify-between p-4 max-sm:flex-col">
      <div class="header__logo m-4">
        <NuxtLink to="/">
          <h1 class="text-3xl color-text-custom font-merriweather font-bold">Calc-World</h1>
        </NuxtLink>
      </div>
      <div class="header__nav m-4">
        <div class="nav-menu relative inline-block">
          <button class="text-lg font-montserrat font-semibold text-gray-50 bg-btns p-2 rounded-lg">Калькуляторы</button>
          <div class="nav-menu__content flex flex-col text-center bg-header-menu rounded-lg w-36 max-h-64 overflow-y-auto absolute opacity-0">
            <NuxtLink to="/calculators/math-calculator" :class="{ 'text-blue-200' : route.fullPath === '/calculators/math-calculator' }" class="btn-header-menu">Обычный</NuxtLink>
            <NuxtLink to="/calculators/percent-calculator" :class="{ 'text-blue-200' : route.fullPath === '/calculators/percent-calculator' }" class="btn-header-menu">Процентный</NuxtLink>
            <NuxtLink to="/calculators/days-calculator" :class="{ 'text-blue-200' : route.fullPath === '/calculators/days-calculator' }" class="btn-header-menu">Дней</NuxtLink>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>
  const route = useRoute()
</script>

<style scoped>
.nav-menu:hover button {
  background: #c1c7a2;
}
.nav-menu:hover .nav-menu__content {
  opacity: 1;
}
.nav-menu__content {
  transition: opacity .2s ease-in;
}
</style>