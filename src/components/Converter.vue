<template>
  <div class="container">
    <div class="pricing-header px-3 py-3 pt-md-5 pb-md-4 mx-auto text-center">
      <h1 class="display-4">M2LAB Converter</h1>
    </div>
    <div class="row">
      <div class="col-8 offset-2">
        <div class="row">
          <div class="col buy-block">
            <div class="row">
              <div class="col-8 offset-2 px-0">
                <div class="my-5 py-5">
                  <h3>ПОКУПАЕМ</h3>
                  <div class="pt-5">
                    <h5>1 WMR - {{ sell.wmr }} руб</h5>
                    <h5>1 WMZ - {{ sell.wmz }} руб</h5>
                  </div>
                  <div class="converter-block pt-4 mt-3">
                    <div class="row">
                      <div class="col">
                        <label for="buy-give">Вы отдадите</label>
                      </div>
                      <div class="col-8">
                        <input type="number" class="form-control" id="buy-give" placeholder="" v-model.number="amountBuy">
                      </div>
                      <div class="col-4">
                        <select v-model = "convertToBuy" id="inputState" class="form-control">
                          <option v-for = "(a, index) in currencyFrom" v-bind:value = "a.name">{{a.desc}}</option>
                        </select>
                      </div>
                    </div>
                    <div class="row pt-4">
                      <div class="col">
                        <label for="buy-get">Вы получите</label>
                      </div>
                      <div class="col-8">
                        <input type="number" class="form-control" id="buy-get" placeholder="0" v-bind:value= "finalAmountBuy">
                      </div>
                      <div class="col-4 d-flex align-items-center">
                        рублей
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="col sell-block">
            <div class="row">
              <div class="col-8 offset-2 px-0">
                <div class="my-5 py-5">
                  <h3>ПРОДАЁМ</h3>
                  <div class="pt-5">
                    <h5>1 WMR - {{ buy.wmr }} руб</h5>
                    <h5>1 WMZ - {{ buy.wmz }} руб</h5>
                  </div>
                  <div class="converter-block pt-4 mt-3">
                    <div class="row">
                      <div class="col">
                        <label for="sell-give">Вы отдадите</label>
                      </div>
                      <div class="col-8">
                        <input type="number" class="form-control" id="sell-give" placeholder="0" v-model.number="amountSell">
                      </div>
                      <div class="col-4 d-flex align-items-center">
                        рублей
                      </div>
                    </div>
                    <div class="row pt-4">
                      <div class="col">
                        <label for="sell-get">Вы получите</label>
                      </div>
                      <div class="col-8">
                        <input type="number" class="form-control" id="sell-get" placeholder="" v-bind:value= "finalAmountSell">
                      </div>
                      <div class="col-4">
                        <select v-model = "convertToSell" id="inputState" class="form-control">
                         <option v-for = "(a, index) in currencyFrom" v-bind:value = "a.name">{{a.desc}}</option>
                        </select>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="col-8 offset-2 pt-5 px-0 border-bottom"></div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      name: "",
      currencyFrom: [
        { name: "WMR", desc: "WMR" },
        { name: "WMZ", desc: "WMZ" }
      ],
      convertFromBuy: "WMR",
      convertFromSell: "WMR",
      convertToBuy: "WMR",
      convertToSell: "WMR",
      amountBuy: 0,
      amountSell: 0,
      sell: {
        wmr: 0.96,
        wmz: 55.7
      },
      buy: {
        wmr: 1,
        wmz: 58.9
      }
    };
  },
  computed: {
    finalAmountBuy: function() {
      var to = this.convertToBuy;
      var from = this.convertFromBuy;
      var final;
      switch (from) {
        case "WMR":
          if (to == "WMR") {
            final = this.amountBuy * this.sell.wmr;
          }
          if (to == "WMZ") {
            final = this.amountBuy * this.sell.wmz;
          }
          break;
      }
      return final;
    },
    finalAmountSell: function() {
      var to = this.convertToSell;
      var from = this.convertFromSell;
      var final;
      switch (from) {
        case "WMR":
          if (to == "WMR") {
            final = this.amountSell * this.buy.wmr;
          }
          if (to == "WMZ") {
            final = this.amountSell * this.buy.wmz;
          }
          break;
      }
      return final;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
