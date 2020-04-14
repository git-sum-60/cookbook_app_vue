<template>
  <div class="second-test">
    <h1>{{ message }}</h1>
  </div>
</template>

<style>
</style>

<script>
export default {
  data: function() {
    return {
      message: "Welcome to the second test page!"
    };
  },
  created: function() {
    console.log('here i am')
  },
  methods: {}
};
</script>
