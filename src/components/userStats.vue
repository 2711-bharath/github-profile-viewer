<template>
    <div>
        <div class="row">
            <div class="col-sm-12 col-md-6 col-lg-4">
                <div class="fw-bold my-1">Change Theme</div>
                <select class="form-select" aria-label="form-select" v-model="theme">
                    <option v-for="theme in themes" :key="theme" :value="theme">
                        {{theme[0].toUpperCase()+theme.slice(1)}}
                    </option>
                </select>
            </div>
        </div>
        <div class="row mt-3">
            <div class="col-xl-6 col-sm-12 mt-2">
                <div class="h5">Github Stats</div>
                <img :src="'https://github-readme-stats.vercel.app/api?username='+user.username+'&show_icons=true&theme='+theme" alt="Stats">
            </div>
            <div class="col-xl-6 col-sm-12 mt-2">
                <div class="h5">Profile Summary</div>
                <img :src="'https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username='+user.username+'&show_icons=true&theme='+theme" alt="Stats">
            </div>

            <div class="h5 mt-3">Most Used Languages</div>
            <div class="col-xl-4 col-sm-12 mt-2">
                <img :src="'https://github-readme-stats.vercel.app/api/top-langs?username='+user.username+'&show_icons=true&theme='+theme" alt="Stats">
            </div>
            <div class="col-xl-4 col-sm-12 mt-2">
                <img :src="'https://github-profile-summary-cards.vercel.app/api/cards/repos-per-language?username='+user.username+'&show_icons=true&theme='+theme+'&count_private=true&layout=compact'" alt="Stats">
            </div>
            <div class="col-xl-4 col-sm-12 mt-2">
                <img :src="'https://github-profile-summary-cards.vercel.app/api/cards/most-commit-language?username='+user.username+'&show_icons=true&theme='+theme+'&count_private=true'" alt="Stats">
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'UserStats',
  props: {
    user: Object,
  },
  data() {
    return {
      themes: [
        'radical',
        'dark',
        'merko',
        'gruvbox',
        'tokyonight',
        'onedark',
        'cobalt',
        'synthwave',
        'highcontrast',
        'dracula',
      ],
      theme: 'dracula',
    };
  },
};
</script>
