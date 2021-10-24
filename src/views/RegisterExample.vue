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
                  <input-field
                    textTitle="Full Name"
                    id="nameInput"
                    inputPlaceholder="write your name here"
                    inputName="nama"
                    v-model="posts.nama"
                  />

                  <input-field
                    textTitle="Email Address"
                    id="emailInput"
                    inputPlaceholder="write your email here"
                    inputName="email"
                    inputType="email"
                    v-model="posts.email"
                  />

                  <input-field
                    textTitle="Password"
                    id="passwordInput"
                    inputPlaceholder="write your password here"
                    inputName="password"
                    inputType="password"
                    v-model="posts.password"
                  />

                  <input-field
                    textTitle="Confirm Password"
                    id="passwordConfirmInput"
                    inputPlaceholder="write your password confirm here"
                    inputName="passwordConfirm"
                    inputType="password"
                  />

                  <!-- <input-field
                    textTitle="Role"
                    id="roleInput"
                    inputPlaceholder="write your role here"
                    inputName="role"
                    v-model.number="posts.role_id"
                  /> -->

                  <label>Select Role</label>
                  <div>
                    <select v-model="posts.role_id">
                      <option
                        v-for="(role, index) in roles"
                        :value="role.id_role"
                        :key="index"
                      >
                        {{ role.nama_role }}
                      </option>
                    </select>
                  </div>

                  <div class="d-grid mt-4">
                    <div v-if="error">Something Wrong</div>
                    <div v-else-if="error === false">
                      Success register data!
                    </div>
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
import InputField from "../components/InputField.vue";

Vue.use(VueAxios, axios);

export default {
  name: "RegisterExample",

  components: {
    InputField,
  },

  data() {
    return {
      posts: {
        nama: null,
        email: null,
        password: null,
        role_id: null,
      },
      roles: [],
      selected: {
        role: "",
      },
      error: null,
    };
  },

  mounted() {
    this.getRoles();
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
        })
        .then(() => (this.error = false))
        .catch((err) => (this.error = err));
      e.preventDefault();
    },

    getRoles() {
      this.axios
        .get("https://golang-bookstore-rest-api.herokuapp.com/api/role/")
        .then((response) => {
          this.roles = response.data.data;
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
