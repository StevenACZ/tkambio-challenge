<template>
  <div class="exchange">
    <header class="exchange__header">
      <div class="send">
        <div class="send__type">
          <h3>SOL</h3>
          <img src="@/assets/images/bandera-peru.png" alt="flag" />
        </div>
        <div class="send__quantity">
          <h4>Envias</h4>
          <input type="text" placeholder="100.000,00" />
        </div>
      </div>

      <div class="reverse">
        <div class="line"></div>
      </div>

      <div class="receive">
        <div class="receive__type">
          <h3>DÓLARES</h3>
          <img src="@/assets/images/bandera-usa.png" alt="flag" />
        </div>
        <div class="receive__quantity">
          <h4>Recibes</h4>
          <input type="text" placeholder="100.000" />
        </div>
      </div>

      <img
        class="icon-reverse"
        src="@/assets/images/icon-cambio.png"
        alt="icono cambio"
      />
    </header>

    <footer class="exchange__footer">
      <div class="exchange-rate">
        <h3>
          <p>Tipo de Cambio:</p>
          <span class="buy active">Compra: 3.398</span>
          <span class="sale">Venta: 3.398</span>
        </h3>
      </div>
      <div class="promotional-code">
        <a href="/">¿Tienes un código promocional? Ingrésalo acá</a>
      </div>
      <Button text="¡A cambiar!" type="primary" size="big" />
    </footer>
  </div>
</template>

<script>
// Components
import Button from './ui/Button';

export default {
  name: 'Exchange',
  components: {
    Button,
  },
};
</script>

<style lang="scss" scoped>
.exchange {
  background-color: #eeeeee;
  border-radius: 15px;
  padding: 12px 11px 40px 11px;

  .exchange__header {
    display: grid;
    grid-template-columns: 40% 1fr 40%;
    grid-template-areas: 'send reverse receive';
    background-color: white;
    border-radius: 15px;
    padding: 20px 25px;
    position: relative;

    .send {
      display: grid;
      grid-template-columns: 1fr;
      grid-template-areas:
        'type'
        'quantity';

      .send__type {
        grid-area: type;
        display: flex;
        justify-content: flex-start;
        align-items: center;
        padding-bottom: 15px;
        border-bottom: 1px solid rgba(0, 0, 0, 0.15);

        & > h3 {
          font-size: 13px;
          line-height: 13.47px;
          font-weight: 300;
          margin-right: 8px;
        }
      }

      .send__quantity {
        grid-area: quantity;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        padding-top: 13px;

        & > h4 {
          font-size: 15px;
          line-height: 15.54px;
          font-weight: 300;
          margin-bottom: 11px;
        }

        & > input {
          width: 90%;
          font-size: 35px;
          line-height: 36.26px;
          font-weight: 300;
          border: none;
          border-radius: 0;
          outline: none;
          border-bottom: 1px solid black;
        }
      }
    }

    .reverse {
      grid-area: reverse;

      .line {
        border-bottom: 1px solid rgba(0, 0, 0, 0.15);
        padding-top: 30px;
      }
    }

    .receive {
      display: grid;
      grid-template-columns: 1fr;
      grid-template-areas:
        'type'
        'quantity';

      .receive__type {
        grid-area: type;
        display: flex;
        justify-content: flex-start;
        align-items: center;
        padding-bottom: 15px;
        border-bottom: 1px solid rgba(0, 0, 0, 0.15);

        & > h3 {
          font-size: 13px;
          line-height: 13.47px;
          font-weight: 300;
          margin-right: 8px;
        }
      }

      .receive__quantity {
        grid-area: quantity;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        padding-top: 13px;

        & > h4 {
          font-size: 15px;
          line-height: 15.54px;
          font-weight: 300;
          margin-bottom: 11px;
        }

        & > input {
          width: 100%;
          font-size: 35px;
          line-height: 36.26px;
          font-weight: 300;
          border: none;
          outline: none;
          border-bottom: 1px solid black;
        }
      }
    }

    .icon-reverse {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -10%);
      cursor: pointer;
    }
  }

  .exchange__footer {
    position: relative;

    .exchange-rate {
      margin-top: 19px;

      & > h3 {
        font-size: 13px;
        line-height: 13.47px;
        font-weight: 300;

        & > p {
          display: inline-block;
          margin-right: 5px;
        }

        .buy {
          border-right: 1px solid black;
          padding-right: 8px;
          margin-right: 8px;
        }

        .active {
          font-weight: 600;
          text-decoration: underline;
        }
      }
    }

    .promotional-code {
      margin-top: 20px;

      & > a {
        font-size: 10px;
        line-height: 18px;
        font-weight: 300;
        color: black;
      }
    }

    & > button {
      position: absolute;
      bottom: 0%;
      left: 50%;
      transform: translate(-50%, 130%);
    }
  }

  @media (max-width: 991px) {
    .exchange__header {
      grid-template-columns: 1fr;
      grid-template-areas:
        'send'
        'receive';
      background-color: white;
      padding: 20px;

      .send {
        display: grid;
        grid-template-columns: 60% 1fr;
        grid-template-areas: 'quantity type';
        grid-column-gap: 20px;
        padding-bottom: 22px;
        border-bottom: 1px solid rgba(0, 0, 0, 0.15);

        .send__quantity {
          padding-top: 0;

          & > input {
            font-size: 28px;
            line-height: 29.01px;
          }
        }

        .send__type {
          grid-area: type;
          display: flex;
          justify-content: center;
          align-items: center;
          padding-bottom: 0;
          border-bottom: none;

          & > h3 {
            margin-right: 10px;
          }
        }
      }

      .reverse {
        display: none;
      }

      .receive {
        display: grid;
        grid-template-columns: 60% 1fr;
        grid-template-areas: 'quantity type';
        grid-column-gap: 20px;
        padding-top: 22px;

        .receive__quantity {
          padding-top: 0;

          & > input {
            font-size: 28px;
            line-height: 29.01px;
          }
        }

        .receive__type {
          grid-area: type;
          display: flex;
          justify-content: center;
          align-items: center;
          padding-bottom: 0;
          border-bottom: none;

          & > h3 {
            margin-right: 10px;
          }
        }
      }

      .icon-reverse {
        left: 70%;
        transform: translate(0%, -50%);
      }
    }

    .exchange__footer {
      .exchange-rate {
        & > h3 {
          & > p {
            display: block;
            margin-right: 0;
            margin-bottom: 10px;
          }
        }
      }
    }
  }
}
</style>
