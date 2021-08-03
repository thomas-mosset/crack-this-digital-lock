<template>
<div>
  <header class="header">
    <h1 class="header__title">Crack the password !</h1>
  </header>
</div>
</template>

<script>
export default {
  name: 'Header',
};
</script>

<style lang="scss">
.header {
  padding: 1rem 0;

  &__title {
    font-weight: bold;
    text-align: center;
    font-size: 2rem;
  }
}
</style>
