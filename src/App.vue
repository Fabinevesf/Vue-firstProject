<template>
  <div>
    <div class="container">
      <button
        class="btn btn-outline-dark"
        @click="isParent = true"
        :class="{ ['bg-secondary']: isParent }"
      >
        Parent
      </button>
      <button
        class="btn btn-outline-secondary"
        @click="isParent = false"
        :class="!isParent && 'bg-secondary'"
      >
        Child
      </button>
      <!-- 3 -> USE -->
      <Child v-if="!isParent" :coolThings="gifts" />
      <!--
 <div v-else>
        <h3 class="mt-3">I'm a parent</h3>
        <div class="mb-4 mt-2">
          Title
          <input v-model="title" class="form-control" />
        </div>
        <div class="mb-4">
          Image
          <input type="url" class="form-control" v-model="image" />
        </div>
        <button class="btn btn-primary" @click="sendGift">Send</button>
        <hr />
      </div>
      -->
      <Guests v-else @shareGift="sendGift" />
    </div>
  </div>
</template>
<script>
// 1 -> IMPORT
import Child from './components/Child.vue'
import Guests from './components/Guests.vue'
export default {
  name: 'App',
  components: {
    // 2 -> DECLARE
    Child,
    Guests,
  },
  data() {
    return {
      //all the pieces of data that you might need goes here
      isParent: true,
      //title: '',
      //image: '',
      gifts: [],
    }
  },
  methods: {
    sendGift(present) {
      console.log('is working', present)
      this.gifts.push(present)
    },
  },
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
