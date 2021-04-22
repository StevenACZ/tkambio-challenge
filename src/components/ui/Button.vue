<template>
  <button class="btn" :class="btn">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    text: String,
    type: String,
    size: String,
  },
  computed: {
    btn() {
      return [this.btnSize, this.btnType];
    },
    btnSize() {
      switch (this.size) {
        case 'small':
          return 'btn--primary';
        case 'big':
          return 'btn--big';
      }
    },
    btnType() {
      switch (this.type) {
        case 'primary':
          return 'btn--primary';
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.btn {
  font-size: 14px;
  line-height: 15px;
  font-weight: normal;
  background: none;
  border: 1px solid white;
  border-radius: 50px;
  padding: 16px 30px;
  cursor: pointer;
  color: white;

  /* Types */
  &--primary {
    font-size: 16px;
    line-height: 16.58px;
    font-weight: 400;
    background-color: #ffbd12;
    border: none;
    color: black;
  }

  /* Sizes */
  &--small {
    padding: 16px 30px;
  }

  &--big {
    padding: 16px 50px;
  }
}
</style>
