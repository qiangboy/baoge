<template>
  <div>
      <router-link :to="{ path:'/userCenter/userInfo', query: { name: 'zsq' }}">用户信息</router-link>
      <router-view></router-view>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
</style>
