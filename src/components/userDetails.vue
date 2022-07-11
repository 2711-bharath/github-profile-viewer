<!-- eslint-disable vuejs-accessibility/click-events-have-key-events -->
<template>
    <div class="container mt-5">
      <ul class="nav nav-tabs mb-2">
        <li class="nav-item cursor-pointer" @click="changeView('profile')">
          <div class="nav-link" :class="[active_view === 'profile' ? 'active': '']">
            Profile
          </div>
        </li>
        <li class="nav-item cursor-pointer" @click="changeView('repostitories')">
          <div class="nav-link" :class="[active_view === 'repostitories' ? 'active': '']">
            Repostitories
          </div>
        </li>
        <li class="nav-item cursor-pointer" @click="changeView('stats')">
          <div class="nav-link" :class="[active_view === 'stats' ? 'active': '']">Stats</div>
        </li>
      </ul>
      <template v-if="active_view === 'profile'">
        <user-profile :user="user" />
      </template>
      <template v-if="active_view === 'repostitories'">
        <user-repos :user="user" />
      </template>
      <template v-if="active_view === 'stats'">
        <user-stats :user="user" />
      </template>
    </div>
</template>

<script>
import UserProfile from './userProfile.vue';
import UserStats from './userStats.vue';
import UserRepos from './userRepos.vue';

export default {
  name: 'UserDetails',
  components: {
    UserProfile,
    UserStats,
    UserRepos,
  },
  props: {
    user: Object,
  },
  data() {
    return {
      active_view: 'profile',
    };
  },
  methods: {
    changeView(view) {
      this.active_view = view;
    },
  },
};
</script>
