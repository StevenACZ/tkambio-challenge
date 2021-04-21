<template>
  <button class="btn">{{ text }}</button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    text: String,
  },
};
</script>

<style lang="scss" scoped>
.btn {
  background: none;
  border: 1px solid white;
  border-radius: 50px;
  font-size: 14px;
  font-weight: normal;
  line-height: 15px;
  color: white;
  padding: 16px 30px;
  cursor: pointer;
}
</style>
