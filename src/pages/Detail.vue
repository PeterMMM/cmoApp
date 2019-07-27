<template>
<v-ons-page>
<custom-toolbar v-bind="toolbarInfo"></custom-toolbar>
<custom-detail v-bind="toolbarInfo">
</custom-detail>
</v-ons-page>
</template>
<script>


export default {
props: [ 'title']
};


var vid = document.getElementById("video_player");
    console.log(vid);
</script>