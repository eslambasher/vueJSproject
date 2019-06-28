
<template>
  <div class="centered-container">
    <md-content class="md-elevation-3">
      <div class="title">
        <img :src="require('../images/logo.png')">
        <div class="md-title">Signup</div>
      </div>
      <div class="form">
           <md-field>
          <label>Username</label>
          <md-input v-model="username" autofocus></md-input>
        </md-field>
          <md-field>
          <label>Name</label>
          <md-input v-model="name" autofocus></md-input>
        </md-field>
        <md-field>
          <label>firstname</label>
          <md-input v-model="firstName" autofocus></md-input>
        </md-field>
        <md-field md-has-password>
          <label>Password</label>
          <md-input v-model="password" type="password"></md-input>
        </md-field>
      </div>

      <div class="actions md-layout md-alignment-center-space-between">
        <a href="/login">Login</a>
        <md-button class="md-raised md-primary" @click="handleSubmit">Signup</md-button>
      </div>

      <div class="loading-overlay" v-if="loading">
        <md-progress-spinner md-mode="indeterminate" :md-stroke="2"></md-progress-spinner>
      </div>

    </md-content>
    <div class="background" />
  </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'
import Vue from 'vue'

export default {
    name: 'FormValidation',
    data () {
        return {
             name: '',
            firstName: '',
            username: '',
            password: '',
            submitted: false
        }
    },
    computed: {
        ...mapState('account', ['status'])
    },
    methods: {
        ...mapActions('account', ['register']),
        handleSubmit(e) {
            this.submitted = true;
            this.$validator.validate().then(valid => {
                if (valid) {
                    this.register(this.user);
                }
            });
        }
    }
}
</script>
<style lang="scss">
.centered-container {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  height: 100vh;
  .title {
    text-align: center;
    margin-bottom: 30px;
    img {
      margin-bottom: 16px;
      max-width: 80px;
    }
  }
  .actions {
    .md-button {
      margin: 0;
    }
  }
  .form {
    margin-bottom: 60px;
  }
  .md-content {
    z-index: 1;
    padding: 40px;
    width: 100%;
    max-width: 400px;
    position: relative;
  }
  .loading-overlay {
    z-index: 10;
    top: 0;
    left: 0;
    right: 0;
    position: absolute;
    width: 100%;
    height: 100%;
    background: rgba(255, 255, 255, 0.9);
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
</style>
