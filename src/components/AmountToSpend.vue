<!-- Alınan USD vey EUR değeri app.vue içerisine karışılığı hesaplanmak üzere alınıp iletiliyor -->
<!-- Validate işlemi manuel yapılmıştır -->
<template>
   <div class="col-md-6 order-md-3 mb-6">
                    <label for="username">Amount To Spend</label>
                    <div class="input-group">
                        <input @keyup="sendRequest" v-model="resultBtcValue.buy" type="number" class="form-control" aria-label="Text input with segmented dropdown button">
                        <div class="input-group-append">
                            <select v-on:change="sendRequest" v-model="exchangeCurrency" class="custom-select">
                                <option value="USD" selected>USD</option>
                                <option value="EUR">EUR</option>
                              </select>
                        </div>
                      </div>
                <small v-if="!valid.situation" class="form-text text-danger">{{ valid.msg }}</small>
                </div>
</template>

<script>
export default {
     props : ["resultBtcValue"],
  data () {
    return {
     exchangeCurrency : 'USD',
     valid : {
       situation: true,
       msg : ''
     } 
    }
  },
  methods : {
      sendRequest: function (){
          let request = {
              value : this.resultBtcValue.buy,
              currency : this.exchangeCurrency
          }
            if(request.value < 25){
              console.log("girdim")
            this.valid.situation = false; 
            this.valid.msg = 'Order minimum amount should be 25 '+ this.exchangeCurrency;
          } else if(request.value > 25000){
             this.valid.situation = false; 
            this.valid.msg = 'Order maximum amount should be 20000 '+ this.exchangeCurrency;
          }else{
              this.valid.situation = true;
          }
          this.$emit("resultEvent", request)
      },
  }
}
</script>

<style>
</style>
