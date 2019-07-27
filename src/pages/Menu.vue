<template>
  <v-ons-page modifier="white">
    <div class="profile-pic">
      <img src="../assets/user.png" style="width: 100px;height: 100px;margin: auto;padding-top: 10px;">
    </div>

    <v-ons-list-title>MAIN</v-ons-list-title>
    <v-ons-list>
      <v-ons-list-item v-for="(item, index) in access" :key="item.title"
        :modifier="md ? 'nodivider' : ''"
        @click="loadView(index)"
      >
        <div class="left">
          <v-ons-icon fixed-width class="list-item__icon" :icon="item.icon"></v-ons-icon>
        </div>
        <div class="center">
          {{ item.title }}
        </div>
        <div class="right">
          <v-ons-icon icon="fa-link"></v-ons-icon>
        </div>
      </v-ons-list-item>
    </v-ons-list>

    <v-ons-list-title> Personal</v-ons-list-title>
    <v-ons-list>
    <v-ons-list-item v-for="page of pages" :key="page.label"
    @click="push(page.component, page.label)"
      >
        <div class="center">
          {{ page.label }}
        </div>
      </v-ons-list-item>
    </v-ons-list>
  </v-ons-page>
</template>

<script>
import Profile from './Profile.vue';
import Login from './Login.vue';
import Detail from './Detail.vue';


export default {
  methods: {
    loadView(index) {
      this.$store.commit('tabbar/set', index);
      this.$store.commit('splitter/toggle');
    },
    loadLink(url) {
      window.open(url);
    },
    push(page, key) {
      this.$store.commit('navigator/push', {
        extends: page,
        data() {
          return {
            toolbarInfo: {
              backLabel: 'Home',
              title: key
            }
          }
        }
      });
    }
  },
  data() {
    return {
      access: [
        {
          title: 'Home',
          icon: 'ion-home, material:md-home'
        },
        {
          title: 'Channel',
          icon: 'ion-edit, material:md-edit'
        },
        {
          title: 'Myanmar',
          icon: 'ion-film-marker, material: md-movie-alt'
        },
        {
          title: 'Free',
          icon: 'ion-edit, material:md-edit'
        },
        {
          title: 'Premium',
          icon: 'ion-film-marker, material: md-movie-alt'
        }
      ],
      pages: [
        {
          component: Profile,
          label: 'Profile',
          desc: 'Movie description.'
        },
        {
          component: Login,
          label: 'Logout',
          desc: 'Movie description'
        }
      ]
    };
  }
};
</script>

<style scoped>
.profile-pic {
  width: 100%;
  background-color: #fff;
  border-bottom: 1px solid #DDD;
  color: rgba(0, 0, 0, .56);
  padding-bottom: 8px;
}
.page--material .profile-pic {
  background-color: #f6f6f6;
}

.profile-pic > img {
  display: block;
  max-width: 100%;
}
</style>

<style>
.page--material__background.page--white__background {
  background-color: #fff;
}
</style>
