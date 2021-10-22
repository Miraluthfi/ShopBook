<template>
  <div>
    <label :for="inputId">{{ textTitle }}</label>
    <div class="form-floating mb-3">
      <input
        :type="inputType"
        class="form-control"
        :class="inputClass"
        :id="inputId"
        :placeholder="inputPlaceholder"
        :name="inputName"
        :maxlength="maxlength"
        :minlength="minlength"
        :disabled="isDisabled"
        @input="updateValue($event.target.value)"
        :value="value"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "InputField",
  props: {
    textTitle: {
      type: String,
      default: "",
    },
    inputType: {
      type: String,
      default: "text",
    },
    inputId: {
      type: String,
      default: "",
    },
    inputClass: {
      type: String,
      default: "",
    },
    inputPlaceholder: {
      type: String,
      default: "",
    },
    inputName: {
      type: String,
      default: "",
    },
    inputVModel: {
      type: String,
      default: "",
    },
    maxlength: {
      type: String,
      default: "",
    },
    minlength: {
      type: String,
      default: "",
    },
    isDisabled: {
      type: Boolean,
      default: false,
    },
    value: {
      type: String,
    },
  },

  methods: {
    updateValue(value) {
      this.$emit("input", value);
    },
  },
};
</script>
<style scoped>
.login {
  min-height: 100vh;
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
