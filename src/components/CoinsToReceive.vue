<!-- Alınan coin değer app.vue içerisine karışılığı hesaplanmak üzere alınıp iletiliyor -->
<template>
 <div class="col-md-6 order-md-3 mb-6">
                    <label for="username">Coins To Receive</label>
                    <div class="input-group">
                        <input @keyup="sendRequest" v-model="resultValue.data" type="text" class="form-control" aria-label="Text input with segmented dropdown button">
                        <div class="input-group-append">
                            <select v-on:change="sendRequest" class="custom-select" id="inputGroupSelect02">
                                <option selected>BTC</option>
                              </select>
                          </div>
                        </div>
                      </div>
                </div>
</template>

<script>
export default {
      props : ["resultValue"],
        data () {
    return {
    
    }
  },
  methods : {
      sendRequest: function (){
           this.$emit("resultBtcEvent", this.resultValue.data)
      }
  }
}
</script>

<style>
</style>
