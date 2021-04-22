<template>
  <footer class="footer">
    <div class="banks">
      <header class="banks__header">
        <p>Operaciones de cambio inmediatas a través de:</p>
      </header>

      <footer class="banks__footer">
        <div class="bcp">
          <img src="@/assets/images/logo-bcp.png" alt="BCP logo" />
          <p>Todos los días</p>
        </div>
        <div class="interbank">
          <img src="@/assets/images/logo-interbank.png" alt="BCP logo" />
          <p>de Lunes a Sábados</p>
        </div>
      </footer>
    </div>

    <div class="info">
      <h3>
        Operaciones interbancarias a <br />
        todos los bancos de Lima
      </h3>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
};
</script>

<style lang="scss" scoped>
.footer {
  display: grid;
  grid-template-columns: auto 1fr;
  grid-template-areas: 'banks info';
  max-width: 992px;
  margin: 0 auto;

  .banks {
    grid-area: banks;
    border-right: 1px solid #c4c4c4;
    padding-right: 24px;
    margin-right: 24px;

    .banks__header {
      margin-bottom: 11px;

      & > p {
        font-size: 13px;
        line-height: 13.47px;
        font-weight: 300;
      }
    }

    .banks__footer {
      display: flex;
      justify-content: space-between;
      align-items: center;

      .bcp {
        & > p {
          margin-top: 6px;
          font-size: 13px;
          line-height: 13.47px;
          font-weight: 300;
        }
      }

      .interbank {
        & > p {
          margin-top: 6px;
          font-size: 13px;
          line-height: 13.47px;
          font-weight: 300;
        }
      }
    }
  }

  .info {
    grid-area: info;
    display: flex;
    align-items: center;

    & > h3 {
      font-size: 16px;
      line-height: 22px;
      font-weight: 300;
    }
  }

  @media (max-width: 991px) {
    max-width: 75%;
  }

  @media (max-width: 767px) {
    max-width: 100%;
    grid-template-columns: 1fr;
    grid-template-areas:
      'banks'
      'info';
    grid-row-gap: 23px;
    justify-content: center;
    margin: 0 auto;

    .banks {
      display: flex;
      flex-direction: column;
      align-items: center;
      border-right: none;
      padding-right: 0;
      margin-right: 0;
    }

    .info {
      justify-content: center;
    }
  }
}
</style>
