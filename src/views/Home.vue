<template>
  <div class="hero">
    <Header />
    <main class="landing-page">
      <div class="info">
        <header class="info__header">
          <h2>
            Sé tu propio cambista.
          </h2>
          <h4>Seguro, rápido y al mejor cambio</h4>
          <p>Inscritos en la Superintendencia de Banca, Seguros y AFP.</p>
        </header>

        <footer class="info__footer">
          <Button text="Crear cuenta" />
          <a href="/">¿Cómo funciona?</a>
        </footer>
      </div>

      <div class="exchange">
        <Exchange />
      </div>
    </main>
    <Footer />
  </div>
</template>

<script>
// Components
import Header from '../components/layout/Header';
import Footer from '../components/layout/Footer';
import Button from '../components/ui/Button';
import Exchange from '../components/Exchange';

export default {
  name: 'Home',
  components: {
    Header,
    Footer,
    Button,
    Exchange,
  },
};
</script>

<style lang="scss" scoped>
.hero {
  background-image: url('../assets/images/background.png');
  background-position: center top;
  background-repeat: no-repeat;
  width: 100%;
  height: 100vh;

  .landing-page {
    display: grid;
    grid-template-columns: 45% 1fr;
    grid-template-areas: 'info exchange';
    max-width: 992px;
    margin: 70px auto 160px auto;

    .info {
      grid-area: info;
      color: white;
      text-align: start;

      .info__header {
        & > h2 {
          font-size: 50px;
          line-height: 60px;
          font-weight: 700;
        }

        & > h4 {
          font-size: 20px;
          line-height: 20.72px;
          font-weight: 300;
          margin: 24px 0 11px;
        }

        & > p {
          font-size: 11px;
          line-height: 11.4px;
          font-weight: 300;
          margin-bottom: 28px;
        }
      }

      .info__footer {
        display: flex;
        flex-direction: column;
        align-items: flex-start;

        & > a {
          margin-top: 9px;
          color: white;
        }
      }
    }

    .exchange {
      grid-area: exchange;
    }
  }

  @media (max-width: 991px) {
    .landing-page {
      max-width: 75%;
      grid-template-columns: 45% 1fr;
      margin: 40px auto 140px auto;
      padding: 0;

      .info > .info__header {
        & > h2 {
          font-size: 38px;
          line-height: 40px;
        }

        & > h4 {
          font-size: 16px;
          line-height: 20px;
          padding-right: 40px;
          margin: 24px 0 11px;
        }

        & > p {
          font-size: 9px;
          padding-right: 40px;
          line-height: 13px;
        }
      }
    }
  }

  @media (max-width: 767px) {
    .landing-page {
      max-width: 100%;
      grid-template-columns: 1fr;
      grid-template-areas:
        'info'
        'exchange';
      justify-content: center;
      padding: 0 20px;
      margin: 30px auto 75px auto;

      .info {
        text-align: center;

        .info__header {
          margin-bottom: 27px;

          & > h2 {
            font-size: 30px;
            line-height: 36px;
            font-weight: 700;
          }

          & > h4 {
            font-size: 16px;
            line-height: 23px;
            font-weight: 300;
            margin-top: 6px;
            padding: 0;
          }

          & > p {
            display: none;
          }
        }

        .info__footer {
          display: none;
        }
      }
    }
  }
}
</style>
