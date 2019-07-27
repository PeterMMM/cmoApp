<template>
  <v-ons-page>
    <custom-toolbar v-bind="toolbarInfo"></custom-toolbar>
    <custom-detail v-bind="toolbarInfo"></custom-detail>

  <h3>welcome to detail page</h3>  
  </v-ons-page>
</template>

<script>
export default {
  props: ['title']
};

</script>

<style>

</style>
