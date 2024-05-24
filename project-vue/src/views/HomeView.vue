<template lang="">
  <div>
    
  </div>
</template>
<script>
import router from '@/router'

export default {
  data() {
    return {
      username : ''
    }
  },
  mounted() {
    this.username = localStorage.getItem('name')
    if (!this.username || this.username == '' || this.username == null) {
      router.push({ name: 'login' })
    }
  },
}
</script>
<style lang="">
  
</style>