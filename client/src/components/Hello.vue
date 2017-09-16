<template>
  <div class="hello">
      <v-container>
          <h4>Create your account</h4>
          <v-form v-model="valid">
              <v-text-field
                      label="Name"
                      v-model="name"
                      :rules="nameRules"
                      :counter="50"
                      required
              ></v-text-field>
              <v-text-field
                      label="E-mail Address"
                      v-model="email"
                      :rules="emailRules"
                      required
              ></v-text-field>
              <v-text-field
                      label="Password"
                      type="password"
                      v-model="password"
                      :rules="passwordRules"
                      required
              ></v-text-field>
              <v-text-field
                      label="Confirm Password"
                      type="password"
                      v-model="confPassword"
                      :rules="confPassRules"
                      required
              ></v-text-field>
              <v-btn dark @click="register">Register</v-btn>
          </v-form>
      </v-container>
  </div>
</template>

<script>
    import axios from '../services/Api'


export default {
  name: 'hello',
    data () {
        return {
            valid: false,
            name: '',
            nameRules: [
                (v) => !!v || 'Name is required',
                (v) => v.length <= 50 || 'Name must be less than 10 characters'
            ],
            email: '',
            emailRules: [
                (v) => !!v || 'E-mail is required',
                (v) => /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(v) || 'E-mail must be valid'
            ],
            password: '',
            confPassword: '',
            passwordRules:[
                (v) => !!v || 'Password is required',
            ],
            confPassRules:[
                () => this.password === this.confPassword || 'Password does not match'
            ]
        }
    },
    methods:{


        register(){

            axios().post('/api/testing', {
                name: this.name,
                email: this.email,
                password: this.password
            })
                .then(function(response){
                    console.log(response);
                })
                .catch(function(error){
                    console.log(error);
                });
        }

    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
