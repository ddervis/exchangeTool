<template>
 <div class="container">
            <div class="py-5 text-center">
                <img class="d-block mx-auto mb-4" src="logo.png" alt="" width="72" height="72">
                <h2>Dervis Exchange</h2>
                <p class="lead">Buy cryptocurrency instantly with your bank/credit cards.</p>
              </div>
            <div class="row">
            <!-- Amount to Spend İnputu için component -->
             <AmounToSpend 
             @resultEvent="getData($event)"
             :resultBtcValue="resultBtcValue" />
             <!-- Coin To Receive için component -->
             <CoinsToReceive 
             @resultBtcEvent="getCalculateData($event)"
             :resultValue="resultValue" />
            </div>
            <div class="container">
                <hr class="mb-12">
                <div class="row justify-content-md-center">
                    <div class="col-md-auto">
                        <button class="btn btn-primary btn-lg btn-block" type="submit">Buy Now</button>
                    </div>
                </div>
            </div>
        </div>
</template>

<script>
import AmounToSpend from "./components/AmountToSpend"
import CoinsToReceive from "./components/CoinsToReceive"
import axios from "axios"


export default {
  components : {
    AmounToSpend,
    CoinsToReceive
  },
  data () {
    return {
      resultValue :[],
      resultBtcValue :[],
      currency:''
    }
  },
  //  Data çekim işlemleri burada yapılıyor. Bussines katmanı ile buraya erişim yapmak daha doğru olacaktır.
    methods : {
      getData: function(e){
        this.currency = e.currency;
         if(this.exchangeValue != '') {
        let url = "https://blockchain.info/tobtc?currency="+e.currency+"&value="+e.value;
          axios.get(url)
          .then(response => {
              this.resultValue = response
              }).catch(e => console.log(e))
              }
      },
      getCalculateData: function(e){
        var insideCurrency = this.currency;
        let test = 0;
        var value = {}
        let url = "https://blockchain.info/ticker";
        axios.get(url)
          .then(response => {
              Object.keys(response.data).forEach(function(key) {
              if(key == insideCurrency){
                value = response.data[key];
                value.buy = value.buy * e;
              }
              })
              this.resultBtcValue = value
              }).catch(e => console.log(e));
           }
        }
  }
    
</script>

<style>
</style>
