<template>
  <div class="form-login">
    <input type="text" v-model="username" placeholder="Username" />
    <input type="password" v-model="password" placeholder="Password" />
    <input type="checkbox" v-model="remember" /> remember
    <input type="button" @click="login()" value="Login" />
    {{ username }}
    {{ password }}
    {{ remember }}
  </div>
</template>

<script>
export default {
  layout: 'blank',
  data() {
    return {
      username: 'Mark',
      password: '',
      remember: false,
    }
  },
  methods: {
    login() {
      if (this.username == 'Mark' && this.password=='1234') {
        alert('Hi ' + this.username)
        this.$router.push('/')
      }else{
          alert('Fail')
      }
    },
    
  },
}
</script>

<style>
input {
  padding: 5px 10px;
}
input:focus {
  background-color: black;
  color: white;
}
.form-login {
  max-width: 400px;
  max-height: 500px;
  margin: auto auto;
  background-color: rgba(24, 224, 224, 0.027);
  border-radius: 6px;
  box-shadow: 2px 2px 3px rgba(197, 207, 207, 0.185);
  padding: 20px;
}
</style>