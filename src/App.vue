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

      <button class="btn btn--large text-sm text-white bg-orange">
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

    <div class="divider border-b border-gray-300 my-10"></div>

    <nav class="nav flex items-center justify-between">
      <ul class="list flex flex-wrap">
        <li v-for="(category, index) in categories" :key="index" class="list__item mr-2">
          <button
            class="btn btn--medium text-base hover:bg-gray-800 hover:text-white"
            :class="{
              'bg-gray-800 text-white': index === activeItem,
              'text-gray-700 bg-gray-100': index !== activeItem,
            }"
            @click="clickToNavBtn(index)"
          >
            {{ category }}
          </button>
        </li>
      </ul>

      <div class="text-gray-700 text-sm flex items-center relative">
        <svg width="10" height="6" viewBox="0 0 10 6" class="fill-current">
          <path
            d="M10 5C10 5.16927 9.93815 5.31576 9.81445 5.43945C9.69075 5.56315 9.54427 5.625 9.375 5.625H0.625C0.455729 5.625 0.309245 5.56315 0.185547 5.43945C0.061849 5.31576 0 5.16927 0 5C0 4.83073 0.061849 4.68424 0.185547 4.56055L4.56055 0.185547C4.68424 0.061849 4.83073 0 5 0C5.16927 0 5.31576 0.061849 5.43945 0.185547L9.81445 4.56055C9.93815 4.68424 10 4.83073 10 5Z"
          />
        </svg>

        <p class="font-bold mx-2">Сортировка по:</p>

        <button @click="toogleDropdown" class="text-orange border-b border-dotted border-orange">
          {{ sortByArray[activeItemSortBy] }}
        </button>

        <div v-if="visibleDropdown" class="dropdown">
          <ul>
            <li v-for="(name, index) in sortByArray" :key="index">
              <button
                @click="clickToDropdownBtn(index)"
                class="dropdown__btn"
                :class="{ 'dropdown__btn--active': activeItemSortBy === index }"
              >
                {{ name }}
              </button>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  data() {
    return {
      categories: ['Все', 'Мясные', 'Вегетарианская', 'Гриль', 'Острые', 'Закрытые'],
      activeItem: 0,

      visibleDropdown: false,

      sortByArray: ['популярности', 'по цене', 'по алфавиту'],
      activeItemSortBy: 0,
    };
  },

  methods: {
    clickToNavBtn(index) {
      this.activeItem = index;
    },

    closeDropdown() {
      this.visibleDropdown = false;
    },
    toogleDropdown() {
      this.visibleDropdown = !this.visibleDropdown;
    },

    clickToDropdownBtn(index) {
      this.activeItemSortBy = index;
      this.closeDropdown();
    },
  },
};
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
  @apply font-bold;

  &:focus {
    outline: none;
  }

  &--large {
    @apply px-6;
    height: 50px;
  }

  &--medium {
    @apply px-6;
    height: 46px;
  }

  border-radius: 30px;
}

.dropdown {
  @apply bg-white;

  width: 132px;

  position: absolute;
  right: 0;
  top: 30px;

  border-radius: 10px;

  padding: 13px 0;

  box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.09);

  &__btn {
    width: 100%;
    height: 38px;
    padding-left: 14px;

    text-align: left;

    &--active,
    &:hover {
      @apply text-orange;
      @apply font-bold;
      background-color: rgba(254, 95, 30, 0.05);
    }
  }
}
</style>
