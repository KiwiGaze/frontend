<template>
  <div id="loading" class="mt-4 w-full max-w-md text-center text-sm text-gray-500">
    Loading...
  </div>
</template>

<script>
export default {
  name: 'LoadingIndicator',
};
</script>

<style scoped>
#loading {
  display: block;
  position: absolute;
  top: 50px;
  left: 50px;
  width: 200px;
  font-family: Arial;
  font-size: 20px;
}
</style>
