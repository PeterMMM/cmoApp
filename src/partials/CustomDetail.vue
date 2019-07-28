<template>
  <v-ons-card>
    <img v-bind:src="url"  alt="Image Url" style="width: 100%;height: auto;">
    <div class="title">
      {{title}}
    </div>
    <div class="content">
      <p>
        {{des}}
      </p>
      <div>
        <ons-button><ons-icon icon="ion-thumbsup"></ons-icon></ons-button>
        <ons-button><ons-icon icon="ion-share"></ons-icon></ons-button>
      </div>
    </div>
  </v-ons-card>
</template>

<script>
export default {
  props: ['title','des' , 'url','backLabel']
};
</script>