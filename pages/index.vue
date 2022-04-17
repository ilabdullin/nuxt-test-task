<template></template>

<script>
export default {
  created: function () {
    setTimeout(() => {
      this.$router.push('/posts');
    }, 0);
  },
};
</script>

<style></style>
