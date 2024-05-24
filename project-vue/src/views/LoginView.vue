<template lang="">
  <div class="container mt-5">
    <div class="row justify-content-center align-items-center">
      <div class="col-md-6">
        <div class="card">
          <div class="card-header">
            <h4>Login</h4>
          </div>
          <div class="card-body">
            <form @submit.prevent>
              <div class="form-group mb-3">
                <label for="email">email</label>
                <input
                  type="email"
                  v-model="email"
                  class="form-control"
                  id="email"
                  name="email"
                  placeholder="Enter your email"
                  required
                />
              </div>
              <div class="form-group mb-3">
                <label for="password">Password</label>
                <input
                  type="password"
                  v-model="password"
                  class="form-control"
                  id="password"
                  name="password"
                  placeholder="Enter your password"
                  required
                />
              </div>
              <button @click="login()" class="btn btn-primary btn-block form-control">
                Login
              </button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import axios from'axios'
import router from '@/router';

export default {
    data() {
        return {
            email: "",
            password: ""
        }
    },
    methods: {
        login() {
            axios.post('http://localhost/laravue/public/api/auth/login', {
                email: this.email,
                password: this.password
            })
            .then(function (response) {
                console.log(response);
                localStorage.setItem('email', response.data.data.email)
                localStorage.setItem('name', response.data.data.name)
                localStorage.setItem('role_id', response.data.data.role_id)
                localStorage.setItem('token', response.data.data.token)
                router.push({name: 'home'})
            })
            .catch(function (error) {
                console.log(error);
            });
        }
    },
    mounted() {
    this.username = localStorage.getItem('name')
    if (this.username || this.username !== '' || this.username !== null) {
      router.push({ name: 'home' })
    }
  },
};
</script>
<style lang=""></style>
