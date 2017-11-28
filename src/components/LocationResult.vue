<template>
  <h5 class="text-success">{{zipToCityResult}}</h5>
</template>

<script>
export default {
  name: 'LocationResult',
  props: ['zipToCityResult']
}
</script>