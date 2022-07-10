<template>
  <div class="m-0 p-0">
    <navbar @show-home="show = 'home'" />
    <template v-if="show === 'home'">
      <home @show-user="getUser" />
    </template>
  </div>
</template>

<script>
import Navbar from './components/navigationBar.vue';
import Home from './components/homePage.vue';

export default {
  name: 'App',
  components: {
    Navbar,
    Home,
  },
  data() {
    return {
      show: 'home',
    };
  },
  methods: {
    getUser(username) {
      this.show = 'user-details';
      console.log(username);
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
