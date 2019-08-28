<template>
  <l-default>
      <template #header>
        <s-header></s-header>
      </template>

      <template #default>
        <s-middle></s-middle>
      </template>

      <template #footer>
        <s-footer></s-footer>
      </template>
  </l-default>
</template>

<script>
  import header from "@/3.sections/s-header";
  import middle from "@/3.sections/s-middle";
  import footer from "@/3.sections/s-footer";

  export default {
    data() {
      return {
      };
    },
    computed: {
    },
    created() {
    },
    components: {
      's-header': header,
      's-middle': middle,
      's-footer': footer
    }

  };
</script>

<style lang="scss">
</style>
