<template>
  <div>
    <footer class="footer">
      <p class="title">Made by <a href="https://github.com/th0m4sm0ss3t" target="blank">Thomas Mosset</a></p>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'Footer',
};
</script>

<style lang="scss">
.footer {
  margin-top: 1.5rem;
  padding: 1rem 0;
}

.footer a {
  color: black;
  text-decoration: none;
  font-weight: bold;
  transition: 0.2;
}

.footer a:hover {
  text-decoration: underline;
}
</style>
