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
                                    <base-input type="email" label="Tên đăng nhập" placeholder="Username"
                                        v-model="user_email">
                                    </base-input>
                                </div>
                                <div class="col-md-4">
                                    <base-input v-model="user_pass" type="text" label="pass" placeholder="pass">
                                    </base-input>
                                </div>

                            </div>


                            <div>
                                <button @click.prevent="login" type="submit"
                                    class="btn btn-success btn-fill float-right">
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
                user_email: null,
                user_pass: null,
            },
        };
    },
    methods: {
        async login() {
            const res = await axios.post("http://localhost:3000/user/login", {
                user_email: this.user_email,
                user_pass: this.user_pass,
            });
           // console.log(res.data.key);
            localStorage.setItem('token', res.data.key)
           // console.log(res.data.key);
            
            alert('success')
            this.$router.push("/")

    }
},
};
</script>