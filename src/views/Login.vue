<template>
  <div class="login">
    <div class="wrapper">
      <div class="login-card">
        <img
          class="avatar"
          src="https://i.ya-webdesign.com/images/drapery-clip-matt-black-5.png"
          alt="user-icon"
        />
        <form class="log-form" @submit.prevent="checkForm" novalidate="true">
          <div class="form-inner-wr">
            <div class="input-wr">
              <input v-model="email" type="text" class="in" placeholder="Enter E-Mail" />
              <div v-if="errors.length" class="error">
                <p v-for="error in errors" :key="error">{{ error }}</p>
              </div>
            </div>
            <div class="submit">
              <input class="submit-btn" type="submit" value="Submit" />
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
//
export default {
  data() {
    return {
      errors: [],
      email: null
    };
  },

  methods: {
    checkForm: function() {
      this.errors = [];
      if (!this.email) {
        this.errors.push("email required.");
      } else if (!this.validEmail(this.email)) {
        this.errors.push("valid email required.");
      }
      if (!this.errors.length) {
        this.$router.push({ path: "/", name: "home" });
        localStorage.setItem("login", this.email);
      }
    },
    validEmail: function(email) {
      const re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    }
  }
};
</script>

<style scoped>
.login {
  position: fixed;
  height: 100vh;
  width: 100vw;
}
.wrapper {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.login-card {
  width: 370px;
  height: 450px;
  border-radius: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
  background-color: #ffffff;
  box-shadow: 0px 12px 24px 0px rgba(40, 43, 49, 0.16);
}
.avatar {
  height: 150px;
  width: 150px;
}
.form-inner-wr {
  text-align: center;
  width: 200px;
}

.in {
  width: 100%;
  height: 40px;
  border-radius: 5px;
  padding-left: 10px;
  background: transparent;
  outline: none;
  border: 1px solid #e7e8ea;
  border-radius: 6px;
  background-color: #f8f9fa;
  font-size: 17px;
  padding: 0 15px;
  box-sizing: border-box;
  color: #000;
}

.submit {
  margin-top: 30px;
}

.submit-btn {
  width: 100%;
  height: 40px;
  background: transparent;
  border-radius: 15px;
  box-shadow: 0px 6px 12px 0px rgba(40, 43, 49, 0.08);
  font-size: 17px;
  font-weight: 700;
  cursor: pointer;
  letter-spacing: 1px;
  /* color: #4fc08d;
  border: 0.5px solid #4fc08d; */

  transition: 250ms ease-out;
}
.error {
  color: red;
  font-size: 16px;
  font-weight: bold;
}
@media (max-width: 420px) {
  .login-card {
    width: 320px;
  }
}
@media (max-width: 320px) {
  .login-card {
    width: 270px;
    height: 390px;
  }
  .button-wr {
    margin-top: 0;
  }
  .message {
    margin: 10px;
  }
}
</style>
