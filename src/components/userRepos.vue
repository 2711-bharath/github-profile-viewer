<template>
    <div>
        <div v-if="repos.length > 0">
            <div class="h3 text-center mb-3">Repositories</div>
            <div class="row">
                <div class="col-xl-4 col-md-6 col-sm-12 mb-3" v-for="repo in repos" :key="repo">
                    <img :src="'https://github-readme-stats.vercel.app/api/pin/?username='+user.username+'&repo='+repo.name" alt="repo" class="shadow-sm">
                </div>
            </div>
        </div>
        <div v-else>
            <div class="display-5 text-center text-primary mt-5">
              No repositories available
            </div>
        </div>
    </div>
</template>

<script>
const axios = require('axios');

export default {
  name: 'UserRepos',
  props: {
    user: Object,
  },
  created() {
    axios.get(`https://api.github.com/users/${this.user.username}/repos`).then((res) => {
      this.repos = res.data;
    });
  },
  data() {
    return {
      repos: [],
    };
  },
};
</script>
