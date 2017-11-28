<template>
  <ul>
    <li>
      <h5>{{CityStateToZipResult}}</h5>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'zipResult',
  props: ['CityStateToZipResult']
}
</script>