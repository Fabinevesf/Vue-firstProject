<template>
  <div>
    <h3 class="mt-3">I'm a guest</h3>
    <div class="mb-4 mt-2">
      Title
      <input v-model="title" class="form-control" />
    </div>
    <div class="mb-4">
      Image
      <input type="url" class="form-control" v-model="image" />
    </div>
    <div class="input-group mb-3">
      <span class="input-group-text">First and Last name</span>
      <input
        type="text"
        aria-label="First name"
        class="form-control"
        v-model="firstName"
      />
      <input
        type="text"
        aria-label="Last name"
        class="form-control"
        v-model="lastName"
      />
    </div>
    <button class="btn btn-primary" @click="wrapThePresent">Send</button>
    <hr />
  </div>
</template>

<script>
export default {
  name: 'Guests',
  data() {
    return {
      title: '',
      image: '',
      firstName: '',
      lastName: '',
    }
  },
  methods: {
    wrapThePresent() {
      let present = {
        title: this.title,
        image: this.image,
        firstName: this.firstName,
        lastName: this.lastName,
      }
      this.$emit('shareGift', present)
    },
  },
}
</script>

<style></style>
