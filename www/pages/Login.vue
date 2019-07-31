<template id="page1">
  <v-ons-page>

<custom-toolbar v-bind="toolbarInfo"></custom-toolbar>
<!--         <v-ons-toolbar>
          <div class="left">
            <slot name="left">
            </slot>
          </div>
          <div class="center"><slot>Registeration</slot></div>
          <div class="right"><slot name="right"></slot></div>
        </v-ons-toolbar>
 -->    
    <v-ons-card>
      <div class="title" style="text-align: center;">
        <h3>User Login</h3> 
      </div>
      <div class="content">
        <div style="text-align: center; margin-top: 30px">
          <p>
            <ons-input id="username" modifier="underbar" placeholder="Username" float ng-model="page.username"></ons-input>
          </p>
          <p>
            <ons-input id="password" modifier="underbar" type="password" placeholder="Password" float ng-model="page.password"></ons-input>
          </p>
          <p style="margin-top: 30px;">
            <ons-button  v-for="page of pages" :key="page.label" @click="push(page.component, page.label, page.desc, page.url)">Sign in</ons-button>
          </p>
        </div>
      </div>



      <br>
      <facebook-login class="button"
        appId="2295796030736034"
        @login="getUserData"
        @logout="onLogout"
        @get-initial-status="getUserData">
      </facebook-login>
      <br>

    </v-ons-card>
 <br>
  </v-ons-page>

  </v-ons-page>
</template>

<script>
import Detail from './Detail.vue';
import Home from './Home.vue';
/*import facebookLogin from 'facebook-login-vuejs';
*/
export default {
  name: "Login",
data () {
return {
state: 'initial',
kittens: this.getRandomData(),
ratio: 0,
  pages: [
    {
      component: Home,
      label: 'Arrival',
      desc: 'Movie description.',
      url: 'http://www.blu-raystats.com/NewsLog/wp-content/uploads/2017/02/Arrival.jpg'
    }
  ]
};
},

methods: {
push(page, title, des , url) {
  this.$store.commit('navigator/push', {
  extends: page,
  data() {
        return {
          toolbarInfo: { //toolbarInfo
            backLabel: 'Home',
            title: title ,
            des: des ,
            url: url
            }
          }
        }
  });
},
onPull(ratio) {
this.ratio = ratio;
},
onAction(done) {
setTimeout(() => {
this.kittens = [this.kittens, this.getRandomKitten()];
done();
}, 1500);
},
getRandomName() {
const names = ['Oscar', 'Max', 'Tiger', 'Sam', 'Misty', 'Simba', 'Coco', 'Chloe', 'Lucy', 'Missy'];
return names[Math.floor(Math.random() * names.length)];
},
getRandomUrl() {
const width = 40 + Math.floor(20 * Math.random());
const height = 40 + Math.floor(20 * Math.random());
return `https://placekitten.com/g/${width}/${height}`;
},
getRandomKitten() {
return {
name: this.getRandomName(),
url: this.getRandomUrl()
};
},
getRandomData() {
const data = [];
for (let i = 0; i < 8; i++) {
data.push(this.getRandomKitten());
}
return data;
}
}
};
</script>
<style>
.intro {
text-align: left;
padding: 0 22px;
margin-top: 20px;
font-size: 14px;
line-height: 1.4;
color: rgba(0, 0, 0, .54);
}
ons-card {
cursor: pointer;
color: #333;
}
.card__title, .card--material__title {
font-size: 20px;
}
.pull-hook-spinner {
color: #666;
transition: transform .25s ease-in-out;
}
.pull-hook-progress {
background-color: white;
width: 32px;
height: 32px;
margin: 30px auto 0;
border-radius: 100%;
position: relative;
box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
display: inline-block;
line-height: 0px;
}
.pull-hook-progress .progress-circular {
width: 24px;
height: 24px;
position: absolute;
top: 4px;
left: 4px;
}
.pull-hook-progress .progress-circular__primary {
transition: stroke-dashoffset 0s;
}
</style>