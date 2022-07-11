<template>
  <div class="m-0 p-0">
    <navbar @show-home="show = 'home'" />
    <template v-if="show === 'home'">
      <home @show-user="getUser" />
    </template>
    <template v-if="show === 'user-details'">
      <user-details :user="userdata" />
    </template>
    <template v-if="show === 'user-invalid'">
      <invalid-user />
    </template>
  </div>
</template>

<script>
import Navbar from './components/navigationBar.vue';
import Home from './components/homePage.vue';
import UserDetails from './components/userDetails.vue';
import InvalidUser from './components/invalidUser.vue';

const axios = require('axios');

export default {
  name: 'App',
  components: {
    Navbar,
    Home,
    UserDetails,
    InvalidUser,
  },
  data() {
    return {
      show: 'home',
      userdata: {},
    };
  },
  methods: {
    async getUser(username) {
      axios.get(`https://api.github.com/users/${username}`).then((res) => {
        if (res.status === 200) {
          this.userdata = {
            username: res.data.login,
            name: res.data.name,
            imageUrl: res.data.avatar_url,
            linkUrl: res.data.html_url,
            noOfRepo: res.data.public_repos,
            followers: res.data.followers,
            following: res.data.following,
            bio: res.data.bio,
            location: res.data.location,
          };
          this.show = 'user-details';
        }
      }).catch((err) => {
        console.log('Error Occured', err);
        this.show = 'user-invalid';
      });
    },
  },
};
</script>

<style lang="scss">

body {
  overflow-x: hidden;
}

$primary: rgb(109, 131, 242);

.text-primary {
  color:  $primary;

  &.hover-black {
    color: #000;
  }
}

.bg-primary {
  background:  $primary;
}

.btn:focus,.btn:active {
   outline: none !important;
   box-shadow: none !important;
}

.btn-primary {
  color: $primary !important;
  background: #fff !important;
  border: 2px solid rgb(217, 224, 255) !important;

  &:hover {
    border: 2px solid $primary !important;
    background: rgb(217, 224, 255);
  }
}

.hover-shadow:hover {
  &.btn {
    box-shadow: 0 .5rem 1rem rgba(0,0,0,.15)!important;
  }
}

.link {
    border: 1px solid transparent;
    &:hover {
        border: 1px solid $primary;
    }
}

.cursor-pointer {
  cursor: pointer;
}

</style>
