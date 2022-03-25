<template>
  <div id="app">
    <div class="container">
      <!-- ///////////////////////////////////////////////////////////////////////// -->

      <h3>Calculator Mercari</h3>
      <div class="row">
        <div class="col-md-5">
          <div class="card h-90">
            <div class="card-body">
              <h3 class="card-title">รายละเอียด</h3>

              <div class="row">
                <div class="col-md-12">
                  <p>รายละเอียด</p>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12">
                  <textarea class="form-control" v-model="message"></textarea>
                </div>
              </div>

              <div class="row">
                <div class="col-md-12">
                  <p>ราคา (เยน)</p>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12">
                  <input type="number" class="form-control" v-model="price" />
                </div>
              </div>
            </div>
            <div class="card-footer">
              <button
                type="button"
                class="btn btn-primary"
                @click="addtaka(message, price)"
              >
                หยิบลงตะกร้า
              </button>
            </div>
          </div>

          <div class="card h-50">
            <div class="card-body">
              <h3 class="card-title">ค่าขนส่ง</h3>

              <div class="row">
                <div class="col-md-12">
                  <p>น้ำหนัก (kg)</p>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12">
                  <input type="number" class="form-control" v-model="weight" />
                </div>
              </div>

              <div class="row">
                <div class="col-md-12">
                  <p>ค่าส่งในไทย (บาท)</p>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12">
                  <input type="number" class="form-control" v-model="send" />
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="col-md-7">
          <h5>ราคา {{ totaltaka() }} บาท</h5>
          <h5>ค่าขนส่งทางเรือ {{ parseInt(weight) * 250 }} บาท</h5>
          <h5>ค่าขนส่งในไทย {{ send }} บาท</h5>
          <hr />
          <h4>
            จำนวนเงินทั้งหมด
            {{
              parseInt(totaltaka()) + parseInt(weight) * 250 + parseInt(send)
            }}
            บาท
          </h4>
          <table class="table">
            <thead class="thead-dark">
              <tr>
                <th scope="col">รายละเอียด</th>
                <th scope="col">ราคา</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="item_data in data" v-bind:key="item_data">
                <td>{{ item_data.message }}</td>
                <td>{{ item_data.price }} บาท</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>

      <hr />
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      message: "",
      price: 0,
      weight: 0,
      send: 0,

      //work4
      data: [],
    };
  },

  methods: {
    //work 4
    addtaka(message, price) {
      var total = (parseInt(price) + 500 + (parseInt(price) + 500) * 0.1) * 0.3;

      const item = {
        message: message,
        price: total,
      };

      this.data.push(item);
    },

    totaltaka: function() {
      var sum = 0;

      this.data.forEach(function(item) {
        sum += item.price;
      });

      return sum;
    },
    //
  },
};
</script>

<style scoped>
.card-img-top {
  height: 200px;
  border: 1px solid black;
}

.img-taka {
  height: 100px;
  width: 100px;
  border: 1px solid black;
}
</style>
