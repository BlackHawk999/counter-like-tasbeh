<template>
  <div class="count">
    <div class="counts-wrapper">
      <div class="counter-child">
        <p class="count-title">Current amount</p>
        <h6 class="amount-balls">{{ count }}</h6>
      </div>
      <button @click="increment" class="increment">+</button>
      <div class="counter-child">
        <p class="count-title">Counter of all amount</p>
        <h6 class="amount-balls all">{{ allCount }}</h6>
      </div>
    </div>
  </div>
</template>

<script>
const MAX_AMOUNT = 33;

export default {
  name: "HelloWorld",
  data() {
    return {
      amount: 0,
    };
  },
  computed: {
    allCount() {
      if (!this.amount) return 0;

      return Math.floor(this.amount / MAX_AMOUNT);
    },
    count() {
      if (!this.allCount) return this.amount;

      return this.amount - this.allCount * MAX_AMOUNT;
    },
  },
  methods: {
    increment() {
      this.amount++;
    },
  },
};
</script>

<style scoped lang="scss">
.count {
  .counts-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .increment {
    margin-top: 15px;
    margin-bottom: 20px;
    font-size: 25px;
    color: #fff;
    background-color: rgba(159, 66, 199, 0.85);
    border: 2px solid #bd3fef;
    outline: none;
    transition: 0.3s all;
    cursor: pointer;

    &:hover {
      background-color: #fff;
      color: #bd3fef;
    }
  }

  &-child {
    display: flex;
    flex-direction: column;
  }
  
  &-title {
    font-size: 28px;
    font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
      "Lucida Sans", Arial, sans-serif;
      font-weight: 600;
      margin: 0;
  }

  .amount-balls {
    font-size: 35px;
    margin: 0;

    &:not(:last-child) {
      margin-right: 20px;
    }

    &.all {
      font-size: 30px;
    }
  }
}
</style>
