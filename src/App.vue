<template>
  <div class="min-h-screen bg-white flex flex-col items-center justify-center p-4">
    <!-- Avatar Section -->
    <UserAvatar id="avatar" />
    <ChatBot id="chat-bot" />
    <!-- Loading Indicator -->
    <LoadingIndicator id="loading"/>
  </div>
</template>
<script>
  import UserAvatar from './components/Avatar.vue';
  import LoadingIndicator from './components/LoadingIndicator.vue';
  import ChatBot from './components/ChatBot.vue';


  export default {
    components: {
      UserAvatar,
      LoadingIndicator,
      ChatBot,
    },
  };
</script>

<style>
body, html {
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  color: black;
  background-color: lightskyblue;
}
</style>
