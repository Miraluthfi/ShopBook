<template>
  <div class="container-fluid ps-md-0">
    <div class="row g-0">
      <div class="d-none d-md-flex col-md-4 col-lg-6 bg-image"></div>
      <div class="col-md-8 col-lg-6">
        <div class="login d-flex align-items-center py-5">
          <div class="container">
            <div class="row">
              <div class="col-md-9 col-lg-8 mx-auto">
                <h3 class="login-heading mb-4">Sign In to Your Account</h3>

                <!-- Sign In Form -->
                <form>
                  <label for="floatingInput">Email Address</label>
                  <div class="form-floating mb-3">
                    <input
                      type="email"
                      class="form-control"
                      id="floatingInput"
                      placeholder="write your email here"
                      v-model="form.email"
                    />
                  </div>
                  <label for="floatingPassword">Password</label>
                  <div class="form-floating mb-3">
                    <input
                      type="password"
                      class="form-control"
                      id="floatingPassword"
                      placeholder="write your password here"
                      v-model="form.password"
                    />
                  </div>
                  <label for="floatingPassword">Confirm Password</label>
                  <div class="form-floating mb-3">
                    <input
                      type="password"
                      class="form-control"
                      id="floatingPassword"
                      placeholder="write your confirm password here"
                      v-model="form.confirm"
                    />
                  </div>
                  <div class="form-check mb-3">
                    <input
                      class="form-check-input"
                      type="checkbox"
                      value=""
                      id="rememberPasswordCheck"
                    />
                    <label class="form-check-label" for="rememberPasswordCheck">
                      Remember password
                    </label>
                  </div>

                  <div class="d-grid">
                    <button
                      class="
                        btn btn-lg btn-primary btn-login
                        text-uppecase
                        fw-bold
                        mb-2
                      "
                      type="submit"
                    >
                      Sign In
                    </button>
                    <div class="text-center">
                      Don’t have account?
                      <a class="small" href="/Register">Sign Up</a>
                    </div>
                  </div>
                </form>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "login",
  data() {
    return {
      form: {
        email: "",
        password: "",
        confirm: "",
      },
    };
  },
  methods: {
    submitForm() {
      axios
        .post("/Login", this.form)
        .then((res) => {
          //Perform Success Action
        })
        .catch((error) => {
          // error.response.status Check status code
        })
        .finally(() => {
          //Perform action in always
        });
    },
  },
};
</script>

<style scoped>
.login {
  min-height: 100vh;
}

.bg-image {
  background-image: url("https://source.unsplash.com/apcUIqOPEIo");
  background-size: cover;
  background-position: center;
}

.login-heading {
  font-weight: 300;
}

.btn-login {
  font-size: 0.9rem;
  letter-spacing: 0.05rem;
  padding: 0.75rem 1rem;
}
</style>