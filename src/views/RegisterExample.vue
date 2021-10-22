<template>
  <div class="container-fluid ps-md-0">
    <div class="row g-0">
      <div class="d-none d-md-flex col-md-4 col-lg-6 bg-image"></div>
      <div class="col-md-8 col-lg-6">
        <div class="login d-flex align-items-center py-5">
          <div class="container">
            <div class="row">
              <div class="col-md-9 col-lg-8 mx-auto">
                <h3 class="login-heading mb-4">Sign Up Account</h3>

                <!-- Sign In Form -->
                <form @submit="postData" method="post">
                  <label for="floatingInput">Full Name</label>
                  <div class="form-floating mb-3">
                    <input
                      type="text"
                      class="form-control"
                      id="floatingInput"
                      placeholder="write your name here"
                      name="nama"
                      v-model="posts.nama"
                    />
                  </div>
                  <label for="floatingInput">Email Address</label>
                  <div class="form-floating mb-3">
                    <input
                      type="email"
                      class="form-control"
                      id="floatingInput"
                      placeholder="write your email here"
                      name="email"
                      v-model="posts.email"
                    />
                  </div>
                  <label for="floatingPassword">Password</label>
                  <div class="form-floating mb-3">
                    <input
                      type="password"
                      class="form-control"
                      id="floatingPassword"
                      placeholder="write your password here"
                      name="password"
                      v-model="posts.password"
                    />
                  </div>
                  <label for="floatingPassword">Confirm Password</label>
                  <div class="form-floating mb-3">
                    <input
                      type="password"
                      class="form-control"
                      id="floatingPassword"
                      placeholder="write your confirm password here"
                    />
                  </div>

                  <label for="floatingRole">Role</label>
                  <div class="form-floating mb-3">
                    <input
                      type="number"
                      class="form-control"
                      id="floatingRole"
                      placeholder="write your role here"
                      name="role_id"
                      v-model.number="posts.role_id"
                    />
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
                      Continue Sign Up
                    </button>
                    <div class="text-center">
                      Already have account?
                      <a class="small" href="/Login">Sign In</a>
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
import Vue from "vue";
import axios from "axios";
import VueAxios from "vue-axios";

Vue.use(VueAxios, axios);

export default {
  name: "RegisterExample",
  data() {
    return {
      posts: {
        nama: null,
        email: null,
        password: null,
        role_id: null,
      },
    };
  },

  methods: {
    postData(e) {
      this.axios
        .post(
          "https://golang-bookstore-rest-api.herokuapp.com/api/auth/register",
          this.posts
        )
        .then((result) => {
          console.warn(result);
        });
      e.preventDefault();
    },
  },
};
</script>

<style scoped>
.login {
  min-height: 100vh;
}

.bg-image {
  background-image: url("https://source.unsplash.com/8ePZbdxnpi0");
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
