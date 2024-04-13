<template>
  <header class="header bg-header">
    <div class="header__content flex items-center justify-between p-4 max-sm:flex-col">
      <div class="header__logo m-4">
        <h1 class="text-3xl color-text-custom font-merriweather font-bold">Calc-World</h1>
      </div>
      <div class="header__nav m-4">
        <div class="nav-menu relative inline-block">
          <button class="text-lg font-montserrat font-semibold text-gray-50 bg-btns p-2 rounded-lg">Калькуляторы</button>
          <div class="nav-menu__content flex flex-col text-center bg-header-menu rounded-lg w-36 max-h-64 overflow-y-auto absolute opacity-0">
            <NuxtLink class="btn-header-menu">Обычный калькулятор</NuxtLink>
            <NuxtLink class="btn-header-menu">Обычный калькулятор</NuxtLink>
            <NuxtLink class="btn-header-menu">Обычный калькулятор</NuxtLink>
            <NuxtLink class="btn-header-menu">Обычный калькулятор</NuxtLink>
            <NuxtLink class="btn-header-menu">Обычный калькулятор</NuxtLink>
            <NuxtLink class="btn-header-menu">Обычный калькулятор</NuxtLink>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>

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