<template>
  <div class="pizza-card text-center">
    <img :src="pizzaObject.imageUrl" alt="pizza image" class="pizza-card__img mx-auto" />

    <h2 class="font-extrabold text-xl mt-2 mb-5">{{ pizzaObject.name }}</h2>

    <div class="bg-gray-100 py-2 px-1 rounded-xl mb-4 mt-auto">
      <div class="w-full flex justify-between mb-2">
        <button
          class="pizza-card__button"
          :disabled="getTypeDisabled() === 1"
          :class="{ 'pizza-card__button--active': activeType === 'thin' }"
          @click="clickToType('thin')"
        >
          тонкое
        </button>

        <button
          class="pizza-card__button"
          :disabled="getTypeDisabled() === 0"
          :class="{ 'pizza-card__button--active': activeType === 'trad' }"
          @click="clickToType('trad')"
        >
          традиционное
        </button>
      </div>

      <div class="w-full flex justify-between">
        <button
          class="pizza-card__button pizza-card__button--small"
          :disabled="!this.pizzaObject.sizes.includes(26)"
          :class="{ 'pizza-card__button--active': size === 'sm' }"
          @click="clickToSize('sm')"
        >
          26 см.
        </button>

        <button
          class="pizza-card__button pizza-card__button--small"
          :disabled="!this.pizzaObject.sizes.includes(30)"
          :class="{ 'pizza-card__button--active': size === 'md' }"
          @click="clickToSize('md')"
        >
          30 см.
        </button>

        <button
          class="pizza-card__button pizza-card__button--small"
          :disabled="!this.pizzaObject.sizes.includes(40)"
          :class="{ 'pizza-card__button--active': size === 'lg' }"
          @click="clickToSize('lg')"
        >
          40 см.
        </button>
      </div>
    </div>

    <div class="flex items-center justify-between">
      <p class="font-bold text-xl">от {{ pizzaObject.price }} ₽</p>

      <button class="btn btn--small pizza-card__btn">
        <svg class="w-3 h-3 fill-current mr-2" viewBox="0 0 12 12">
          <path
            d="M10.8 4.8H7.2V1.2C7.2 0.5373 6.6627 0 6 0C5.3373 0 4.8 0.5373 4.8 1.2V4.8H1.2C0.5373 4.8 0 5.3373 0 6C0 6.6627 0.5373 7.2 1.2 7.2H4.8V10.8C4.8 11.4627 5.3373 12 6 12C6.6627 12 7.2 11.4627 7.2 10.8V7.2H10.8C11.4627 7.2 12 6.6627 12 6C12 5.3373 11.4627 4.8 10.8 4.8Z"
          />
        </svg>

        Добавить
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'pizza-card',

  props: {
    pizzaObject: {
      type: Object,
      default: () => {},
    },
  },

  data() {
    return {
      activeType: this.getTypeDisabled() === 1 ? 'trad' : 'thin',
      size:
        this.pizzaObject.sizes[0] === 40 ? 'lg' : this.pizzaObject.sizes[0] === 30 ? 'md' : 'sm',
    };
  },

  methods: {
    getTypeDisabled() {
      if (this.pizzaObject.types.length < 2) {
        const [type] = this.pizzaObject.types;
        return type;
      }
      return undefined;
    },

    clickToType(type) {
      this.activeType = type;
    },

    clickToSize(size) {
      this.size = size;
    },
  },

  computed: {},
};
</script>

<style lang="scss">
.pizza-card {
  @apply h-full;
  @apply flex;
  @apply flex-col;

  width: 280px;

  &__img {
    width: 260px;
    height: 260px;
  }

  &__button {
    @apply text-sm;
    @apply text-gray-700;
    @apply font-bold;

    width: 132px;
    height: 32px;

    border-radius: 5px;

    &:disabled {
      opacity: 0.2;
      cursor: not-allowed;

      &:hover {
        @apply bg-transparent;
      }
    }

    &--active,
    &:hover {
      @apply bg-white;
    }

    &--small {
      width: 86px;
    }
  }

  &__btn {
    @apply text-orange;
    @apply border;
    @apply border-orange;

    &--active,
    &:hover {
      @apply text-white;
      @apply bg-orange;
    }
  }
}
</style>
