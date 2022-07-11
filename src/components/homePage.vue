<template>
    <div class="row mt-5">
        <div class="col-xl-4 col-md-3 col-sm-1"></div>
        <div class="col-xl-4 col-md-6 col-sm-10 border">
            <div class="d-flex justify-content-center mt-2 mb-3">
                <img src="../assets/logo.png" alt="logo" height="160" width="300"/>
            </div>
            <label for="username" class="form-label w-100">
                <span class="text-dark fw-normal mb-3 fs-6">Username</span>
                <span class="text-danger sup-text ms-2">*</span>
                <input type="text" class="form-control mt-2"
                    id="username"
                    v-model="username"
                    :class="[submitted && username != '' ? 'is-valid'
                    : submitted ? 'form-control is-invalid' : '']"
                    autocomplete="off"
                />
            </label>
            <div v-if="in_valid_username" class="text-danger">
              Please enter valid username
            </div>
            <div class="text-center my-3">
                <button type="button" class="btn btn-primary hover-shadow" @click="emitSubmit()">
                    View Profile
                </button>
            </div>
        </div>
        <div class="col-xl-4 col-md-3 col-sm-1"></div>
    </div>
</template>

<script>
export default {
  name: 'HomePage',
  data() {
    return {
      username: '',
      submitted: false,
    };
  },
  methods: {
    emitSubmit() {
      this.submitted = true;
      if (this.username !== '') { this.$emit('show-user', this.username); }
    },
  },
};
</script>
