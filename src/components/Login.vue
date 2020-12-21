<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="container">
      <div class="arrage">
        <input type="text" id="username" placeholder="username" />
      </div>
      <div class="arrage">
        <input type="text" id="password" placeholder="password" />
      </div>
      <input
        type="submit"
        value="Login"
        id="submit"
        class="primary"
        v-on:click="make_happen"
      />
      <!-- <a i></a> -->
    </div>
  </div>
</template>

<script>
export default {
  name: "Login",
  props: {
    msg: String,
  },
  methods: {
    async make_happen() {
      let username = document.getElementById("username").value;
      let password = document.getElementById("password").value;
      let option = {
        method: "POST",
        body: JSON.stringify({ username: username, password: password }),
        headers: {
          "Content-Type": "application/json",
          Accept: "*/*",
        },
      };

      return fetch("http://localhost:3000/login", option)
        .then((res) => res.json())
        .then((res) => {
          if(res.code==200){
              alert(res.message)
            }else{
              alert(res.message)

              }
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.container {
  flex-direction: row;
  padding: 10px;
}
input {
  padding: 10px 0 10px 0;
  border-radius: 10px;
  text-align: center;
}

.arrage {
  padding: 10px;
}

#submit {
  border: 2px solid black;
  padding: 6px 40px 6px 40px;
  background: white;
}
</style>
