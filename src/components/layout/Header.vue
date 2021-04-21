<template>
  <header class="header">
    <div class="logo">
      <img src="@/assets/images/Logo-TKambio.png" alt="Logo tkambio" />
    </div>
    <ul class="nav">
      <li class="nav__item">Blog</li>
      <li class="nav__item">Promociones</li>
      <li class="nav__item">Preguntas frecuentes</li>
      <li class="nav__item">Contáctanos</li>
    </ul>
    <Button text="Iniciar sesión" />
  </header>
</template>

<script>
// Components
import Button from '../ui/Button';

export default {
  name: 'Header',
  components: {
    Button,
  },
};
</script>

<style lang="scss" scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 1px solid black;
  max-width: 992px;
  margin: 0 auto;

  .logo {
    cursor: pointer;
  }

  .nav {
    display: flex;
    justify-content: space-between;
    align-items: center;

    .nav__item {
      color: white;
      margin-right: 28px;

      &:last-child {
        margin-right: 0px;
      }
    }
  }
}
</style>
