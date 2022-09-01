<template>
  <div class="alert alert-info">
    <p>Your Answer Is correct, You Want More</p>
    <button class="btn btn-primary" @click="isConfirmed">Next Question</button>
  </div>
</template>

<script>
export default {
  methods: {
      isConfirmed(){
    
          this.$emit('confirmed')
      }
  },
};
</script>

<style>
</style>