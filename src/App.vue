<template>
  <div class="wrapper">
    <header class="header flex items-center justify-between">
      <div class="logo flex items-center">
        <img class="object-cover w-9 h-9 mr-4" src="./assets/logo.png" alt="logo" />
        <div>
          <h1 class="text-2xl font-extrabold uppercase">Vue Pizza</h1>
          <p class="text-gray-500 text-base">самая вкусная пицца во вселенной</p>
        </div>
      </div>

      <button class="btn font-bold text-sm">
        520 ₽
        <div class="h-5 border-current opacity-25 border mx-3"></div>
        <svg class="w-4 h-4 stroke-current mr-2" viewBox="0 0 18 18" fill="none">
          <path
            d="M6.33333 16.3333C7.06971 16.3333 7.66667 15.7364 7.66667 15C7.66667 14.2636 7.06971 13.6667 6.33333 13.6667C5.59695 13.6667 5 14.2636 5 15C5 15.7364 5.59695 16.3333 6.33333 16.3333Z"
            stroke-width="1.8"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
          <path
            d="M14.3333 16.3333C15.0697 16.3333 15.6667 15.7364 15.6667 15C15.6667 14.2636 15.0697 13.6667 14.3333 13.6667C13.597 13.6667 13 14.2636 13 15C13 15.7364 13.597 16.3333 14.3333 16.3333Z"
            stroke-width="1.8"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
          <path
            d="M4.78002 4.99999H16.3334L15.2134 10.5933C15.1524 10.9003 14.9854 11.176 14.7417 11.3722C14.4979 11.5684 14.1929 11.6727 13.88 11.6667H6.83335C6.50781 11.6694 6.1925 11.553 5.94689 11.3393C5.70128 11.1256 5.54233 10.8295 5.50002 10.5067L4.48669 2.82666C4.44466 2.50615 4.28764 2.21182 4.04482 1.99844C3.80201 1.78505 3.48994 1.66715 3.16669 1.66666H1.66669"
            stroke-width="1.8"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
        </svg>
        3
      </button>
    </header>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
@import './main.css';

.wrapper {
  @apply bg-white;
  @apply h-full;

  max-width: 1340px;

  padding: 40px;

  border-radius: 10px;
}

.btn {
  @apply flex;
  @apply items-center;

  @apply px-6;
  @apply py-4;

  @apply bg-orange;
  @apply text-white;

  border-radius: 30px;
}
</style>
