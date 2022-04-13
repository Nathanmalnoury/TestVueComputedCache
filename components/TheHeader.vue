<template>
  <div style="margin-bottom: 15px">
    <NuxtLink to="/computedSimple">
      Computed simple
    </NuxtLink>
    <NuxtLink to="/computedUsingFunction">
      Computed using a function
    </NuxtLink>
    <NuxtLink to="/computedReturningCallable">
      Computed returning a callable
    </NuxtLink>
    <NuxtLink to="/computedCallableWithWrapper">
      Computed wrapping a computer returning a callable
    </NuxtLink>
  </div>
</template>

<script>
export default {
  name: 'TheHeader'
}
</script>

<style scoped>
a {
  border: 1px solid blue;
  margin: 5px;
}
</style>
