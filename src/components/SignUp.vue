<template>

<img class="logo" alt="book logo" src="../assets/logo_books.png">
<h1>Interead</h1>

<div class="register">
  <input type="text" v-model="name" placeholder="Name"/>
  <input type="text" v-model="email" placeholder="E-mail"/>
  <input type="password" v-model="password" placeholder="Password"/>
  <button v-on:click = "SignUp" >Sign UP</button>
</div>
</template>


<script>

 import axios from 'axios'

 export default {

   name: 'SignUp',

   func() {

      return {
        name:"",
        email:"",
        password:""
      }

   },

  //  with this function, it returned variables with the input content that the user has written

   methods: {

    async SignUp() 
    {
      let result = await axios.post("http://localhost:3000/user", {

        name: this.name,
        email: this.email,
        password: this.password

      });
      console.warn(result);
      if (result.status == 201) {
        console.warn("Cadastrado com sucesso.");
      } else {
        console.warn("Erro no cadastro.");
      }

      // when always that we are using an API, the result will apears a little bit later.
      // Cause of that, we should use assync and await.
    }
   }

   // is a special function that pertences to this Vue instance(it's like this current file, SignUp.vue)
   // it's usefull to make some job for us, action, like event handling(v-on)
   // good to make complex, hard things

}

</script>

<style>

.logo {

  width:100px;

}

.register input {

  width: 300px;
  height: 40px;
  padding: 10px;
  margin-right: auto;
  margin-bottom: 25px;
  display: block;
  margin-left: auto;
  border-color: palegoldenrod;
  background-color: #faf5fe;

}

.register button {


  width: 323px;
  height: 50px;
  background-color: #a040f9;
  color: palegoldenrod;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  border: none;

}



</style>
