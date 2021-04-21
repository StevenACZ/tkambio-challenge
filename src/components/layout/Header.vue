<template>
  <header class="header">
    <a class="icon-mobile--menu" href="/">
      <img src="@/assets/images/icon-menu-mobile.png" alt="Menu mobile" />
    </a>
    <img
      class="logo"
      src="@/assets/images/Logo-TKambio.png"
      alt="Logo tkambio"
    />
    <ul class="nav">
      <li class="nav__item">Blog</li>
      <li class="nav__item">Promociones</li>
      <li class="nav__item">Preguntas frecuentes</li>
      <li class="nav__item">Contáctanos</li>
    </ul>
    <Button text="Iniciar sesión" />
    <a class="icon-mobile--login" href="/">
      <img src="@/assets/images/icon-login.png" alt="Menu mobile" />
    </a>
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
  padding: 30px 0;
  max-width: 992px;
  margin: 0 auto;
  border: 1px solid black;

  .icon-mobile--menu {
    display: none;
  }

  .icon-mobile--login {
    display: none;
  }

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
      font-size: 15px;
      line-height: 16px;
      font-weight: 300;

      &:last-child {
        margin-right: 0px;
      }
    }
  }

  @media (max-width: 991px) {
    position: relative;
    padding: 30px 30px;

    .icon-mobile--menu {
      display: block;
    }

    .logo {
      position: absolute;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
    }

    .nav {
      display: none;
    }
  }

  @media (max-width: 767px) {
    padding: 20px 20px;

    .icon-mobile--login {
      display: block;
    }

    .logo {
      width: 160px;
      height: 31px;
    }

    .btn {
      display: none;
    }
  }
}
</style>
