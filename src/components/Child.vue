<template>
  <div>
    <h1>This is the child component</h1>
    <div v-if="favorite" class="row p-3 my-5 align-items-center">
      <div class="col-6">
        <img :src="favorite.image" class="img-fluid rounded" />
      </div>
      <div class="col-4 align-items-center">
        <h3 class="">Who gave me this was {{ fullName }}</h3>
      </div>
    </div>
    <div class="row">
      <div
        v-for="(thing, index) in coolThings"
        :key="index"
        class="col col-md-4 col-sn-auto col-lg-3 mb-2"
      >
        <h4>{{ thing.title }}</h4>
        <img
          :src="thing.image"
          class="img-fluid rounded shadow"
          @click="changeFavorite(thing)"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Child',
  props: ['coolThings'],
  data() {
    return {
      isClicked: false,
      favorite: {},
    }
  },
  methods: {
    changeFavorite(fav) {
      console.log('hello', fav.image)
      this.favorite = fav
    },
  },
  computed: {
    //computed properties are like methods but they are cached
    //so they are only re-evaluated when the data depend on charges
    fullName() {
      return `${this.favorite.firstName} ${this.favorite.lastName}`
    },
  },
}
</script>

<style></style>
