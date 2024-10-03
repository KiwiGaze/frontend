<template>
  <div id="avatar" class="bg-gray-100">
    <!-- Avatar content can go here -->
  </div>
</template>

<script>
export default {
  name: 'UserAvatar',
};
</script>

<style scoped>
#avatar {
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  width: 40%;
  height: 100%;
  background-color: lightskyblue;
}
@media (max-width: 768px) {
  #avatar {
    display: none;
  }
}
</style>
