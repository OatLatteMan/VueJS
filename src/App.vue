<template>
  <h3>{{ info }}</h3>
  <p>{{ someInfo }}</p>
  <button type="button" @click="userData(`Titles`)">Button</button>
</template>

<script>
  export default {
    data() {
      return {
        info: 'Title',
        someInfo: 'Announcement of message'
      }
    },

    methods: {
      userData(word = `default string`) {
        this.someInfo = `Message announcement`
        this.info = word
      }
    }
  }
</script>

<style scoped>
  h3 {
    font-weight: 700;
  }

  p {
    color: rgb(203, 31, 31);
  }



</style>
