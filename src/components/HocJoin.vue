<template>
  <div v-if="Hidden == false" class="d-flex justify-content-center">
    <div
      class="form-container d-flex flex-column justify-content-center mt-5 mb-3"
    >
      <div>
        <p class="mb-1 discription" style="text-align: center; font-size: 4vh">
          Join HOC Discord server.
        </p>
      </div>
      <div class="mb-4">
        <b-form class="row d-flex justify-content-center">
          <label class="discription" style="margin: 1%" for="user-name"
            >Discord User Name</label
          >
          <b-form-input
            class="form-control"
            v-model="uname"
            placeholder="Eg: dev_j1#6406"
            id="user-name"
          ></b-form-input>
          <label class="discription" style="margin: 1%" for="discord-id"
            >Discord ID</label
          >
           <b-form-input
            class="form-control"
            v-model="discord_id"
            placeholder="Eg:939016787092189255"
            id="discord_name"
          ></b-form-input>
          <label class="discription" style="margin: 1%" for="name"
            >Name</label
          >
          <b-form-input
            class="form-control"
            v-model="name"
            placeholder="Eg: UrName : )"
            id="name"
          ></b-form-input>
          <label class="discription" style="margin: 1%" for="name">Email</label>
          <b-form-input
            class="form-control"
            v-model="e_mail"
            placeholder="Eg:musk@mail.com"
            id="e_mail"
          ></b-form-input>
        </b-form>
      </div>
      <div>
        <b-button
          class="btn btn-raised shadow"
          v-on:click="submit_form(uname, discord_id, name, e_mail)"
          type="button"
          >submit</b-button
        >
      </div>
      <div>
        <img
          class="discord_logo"
          src="../assets/discord_logo.svg"
          alt="discord logo"
        />
      </div>
    </div>
  </div>
  <div v-if="Hidden == true" class="loading">
    <h1 class="header">Loading please Wait :)</h1>
    <div>
      <img
        class="discord_logo"
        src="../assets/discord_logo.svg"
        alt="discord logo"
      />
    </div>
  </div>
</template>

<script>
function invite_usr(url) {
  window.location.replace(url);
}

export default {
  name: "HocJoin",
  data() {
    return {
      uname: "",
      discord_id: "",
      name: "",
      e_mail: "",
      Hidden: false,
    };
  },
  methods: {
    submit_form: function submit_form(uname, discord_id, name, email) {
      if (uname == "" || discord_id == "" || name == "" || email == "") {
        return;
      }
      this.Hidden = true;
      const axios = require("axios");
      const url = "https://discord-db-api.herokuapp.com/add_data";
      const config = {
        headers: {
          "Content-Type": "application/json",
        },
      };
      let data = JSON.stringify({
        uname: uname,
        discord_id: discord_id,
        name: name,
        e_mail: email,
      });
      axios
        .post(url, data, config)
        .then((res) => invite_usr(res.data.result))
        .catch((err) => console.log(err));
    },
  },
};
</script>
<style scoped>
.discription {
  color: #738adb;
  font-size: 3vh;
  font-family: "IBM Plex Mono", monospace;
}
.form-control {
  border: solid 2px #738adb;
  background-color: #2c2f33;
  color: #738adb;
  width: 40%;
  text-align: center;
}
.form-control:focus {
  background-color: #2c2f33;
  color: #738adb;
  border-color: #bd93f9;
}
.btn {
  background-color: #2c2f33;
  border: solid 2px;
  color: #738adb;
  width: 15%;
  margin-bottom: 2%;
}
.btn:focus {
  background-color: #2c2f33;
  border: solid 2px;
  color: #99aab5;
}
.btn:hover {
  background-color: #2c2f33;
  border: solid 2px;
  color: #99aab5;
}
.discord_logo {
  width: 12%;
}
.form-container {
  border: #738adb solid 2px;
  width: 50%;
  padding-top: 2%;
  padding-bottom: 1%;
  background-color: #2c2f33;
}
.loading {
  margin-top: 10%;
}
</style>
