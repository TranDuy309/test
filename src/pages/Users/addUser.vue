<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-12">
          <card>
            <h4 slot="header" class="card-title">Thêm người dùng</h4>
            <form>
              <div class="row">
                <div class="col-md-4">
                  <base-input type="text" label="Tên đăng nhập" placeholder="Username" v-model="form.user_name">
                  </base-input>
                </div>
                <div class="col-md-4">
                  <base-input v-model="form.user_email" type="email" label="Email" placeholder="Email">
                  </base-input>
                </div>
                <div class="col-md-4">
                  <base-input v-model="form.user_phone" type="text" label="Phone" placeholder="SDT">
                  </base-input>
                </div>
              </div>
              <div class="row">
                <div class="col-md-4">
                  <base-input type="text" label="Mật khẩu" placeholder="Password" v-model="form.user_pass">
                  </base-input>
                </div>
                <div class="col-md-4">
                  <base-input v-model="form.user_address" type="text" label="DIa chi" placeholder="diaj chi">
                  </base-input>
                </div>
              </div>
              <div>
                <button @click.prevent="onCreate" type="submit" class="btn btn-primary btn-fill float-right">
                  Thêm người dùng
                </button>
              </div>
              <div class="clearfix"></div>
            </form>
          </card>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      form: {
        user_name: null,
        user_email: null,
        user_pass: null,
        user_phone: null,
        user_address: null,
      },
    };
  },
  methods: {
    async onCreate() {
      try {
        let data = new FormData();
        data.append("user_name", this.form.user_name);
        data.append("user_email", this.form.user_email);
        data.append("user_pass", this.form.user_pass);
        data.append("user_phone", this.form.user_phone);
        data.append("user_address", this.form.user_address);

        await axios.post("http://localhost:3000/user/create-usr",data)
//         .then(
//       response => {
// console.log(response)

//  alert("success");
//       });
       
      } catch (error) {
        console.log(error);
      }
    },
    // async register() {
    //   let result = await axios.post("http://localhost:3000/user/create-usr", {
    //     user_name: this.form.user_name,
    //     user_email: this.form.user_email,
    //     user_pass: this.form.user_pass,
    //     user_phone: this.form.user_phone,
    //     user_address: this.form.user_address,
    //     user_type: 1,
    //   },
    //   );
    //   console.log(result);
    // },
  }
};
</script>