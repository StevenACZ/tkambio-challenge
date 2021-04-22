<template>
  <div class="exchange">
    <header class="exchange__header">
      <!-- SEND -->
      <div class="send" v-if="change">
        <div class="send__type">
          <h3>{{ pen_usd.money }}</h3>
          <img src="@/assets/images/bandera-peru.png" alt="flag" />
        </div>
        <div class="send__quantity">
          <h4>Envias</h4>
          <input type="number" placeholder="0.00" v-model="send" />
        </div>
      </div>

      <div class="send" v-else>
        <div class="send__type">
          <h3>{{ usd_pen.money }}</h3>
          <img src="../assets/images/bandera-usa.png" alt="flag" />
        </div>
        <div class="send__quantity">
          <h4>Envias</h4>
          <input type="number" placeholder="0.00" v-model="send" />
        </div>
      </div>

      <div class="reverse">
        <div class="line"></div>
      </div>

      <!-- RECEIVE -->
      <div class="receive" v-if="change">
        <div class="receive__type">
          <h3>{{ usd_pen.money }}</h3>
          <img src="@/assets/images/bandera-usa.png" alt="flag" />
        </div>
        <div class="receive__quantity">
          <h4>Recibes</h4>
          <input
            type="number"
            disabled
            placeholder="0.00"
            v-model="calcReceive"
          />
        </div>
      </div>

      <div class="receive" v-else>
        <div class="receive__type">
          <h3>{{ pen_usd.money }}</h3>
          <img src="@/assets/images/bandera-peru.png" alt="flag" />
        </div>
        <div class="receive__quantity">
          <h4>Recibes</h4>
          <input
            type="number"
            disabled
            placeholder="0.00"
            v-model="calcReceive"
          />
        </div>
      </div>

      <img
        class="icon-reverse"
        @click="activeChange"
        src="@/assets/images/icon-cambio.png"
        alt="icono cambio"
      />
    </header>

    <footer class="exchange__footer">
      <div class="exchange-rate">
        <h3>
          <p>Tipo de Cambio:</p>
          <span class="buy" :class="change ? '' : 'active'"
            >Compra: {{ pen_usd.rate.toFixed(3) }}</span
          >
          <span class="sale" :class="change ? 'active' : ''"
            >Venta: {{ (pen_usd.rate + 0.01).toFixed(3) }}</span
          >
        </h3>
      </div>
      <div class="promotional-code">
        <a href="/">¿Tienes un código promocional? Ingrésalo acá</a>
        <img src="@/assets/images/arrow-down-black.png" alt="arrow downblack" />
      </div>
      <Button text="¡A cambiar!" type="primary" size="big" />
    </footer>
  </div>
</template>

<script>
// Axios
import axios from 'axios';

// Components
import Button from './ui/Button';

export default {
  name: 'Exchange',
  components: {
    Button,
  },
  data() {
    return {
      change: true,
      pen_usd: {
        name: 'PERU',
        money: 'SOL',
        rate: 3.742,
        image: 'bandera-peru.png',
      },
      usd_pen: {
        name: 'USA',
        money: 'DÓLARES',
        rate: 0.27,
        image: '@/assets/images/bandera-usa.png',
      },
      send: 1000,
      receive: 0,
    };
  },
  computed: {
    calcReceive() {
      return (
        this.send * (this.change ? this.usd_pen.rate : this.pen_usd.rate)
      ).toFixed(2);
    },
    calcUsPenRate() {
      return this.pen_usd.rate;
    },
  },
  methods: {
    async currencyConvert() {
      try {
        const { data: DATA_PEN_USD } = await axios.get(
          `https://free.currconv.com/api/v7/convert?q=PEN_USD&compact=ultra&apiKey=8b642ccca9fad18d8208`
        );
        const { data: DATA_USD_PEN } = await axios.get(
          `https://free.currconv.com/api/v7/convert?q=USD_PEN&compact=ultra&apiKey=8b642ccca9fad18d8208`
        );
        this.usd_pen.rate = DATA_PEN_USD.PEN_USD;
        this.pen_usd.rate = DATA_USD_PEN.USD_PEN;
      } catch (error) {
        console.error(error);
      }
    },
    activeChange() {
      this.change = !this.change;
    },
  },
  created() {
    this.currencyConvert();
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
          background-color: transparent;

          &::-webkit-outer-spin-button,
          &::-webkit-inner-spin-button {
            -webkit-appearance: none;
            margin: 0;
          }

          &[type='number'] {
            -moz-appearance: textfield;
          }
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
          width: 90%;
          font-size: 35px;
          line-height: 36.26px;
          font-weight: 300;
          border: none;
          border-radius: 0;
          outline: none;
          border-bottom: 1px solid black;
          background-color: transparent;

          &::-webkit-outer-spin-button,
          &::-webkit-inner-spin-button {
            -webkit-appearance: none;
            margin: 0;
          }

          &[type='number'] {
            -moz-appearance: textfield;
          }
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
    z-index: 999;

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
        margin-right: 5px;
      }
    }

    & > button {
      position: absolute;
      bottom: 0%;
      left: 50%;
      transform: translate(-50%, 130%);
      z-index: 999;
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
